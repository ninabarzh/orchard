# Hello world JS

The simplest workflow for a docker node.js application on [Docker tools VM](../kvm/Docker-tools.md) based on the docker tutorials, adapted to my environment and expanded.

- [Hello world JS](#hello-world-js)
  - [Installing Node.js](#installing-nodejs)
  - [Make containers](#make-containers)
  - [Using Compose](#using-compose)
  - [Debugging](#debugging)
  - [Testing](#testing)

## Installing Node.js

    $ dnf module list nodejs   
    Docker CE Stable - x86_64                        50 kB/s |  12 kB     00:00      
    CentOS Linux 8 - AppStream
    Name      Stream    Profiles                                Summary             
    nodejs    10 [d]    common [d], development, minimal, s2i   Javascript runtime  
    nodejs    12        common [d], development, minimal, s2i   Javascript runtime  
    nodejs    14        common [d], development, minimal, s2i   Javascript runtime  
    
    $ sudo dnf module install -y nodejs:14
    
Check Node.js and Node Package Manager (NPM) versions:
    
    $ node -v
    v14.16.0
    $ npm -v
    6.14.11

## Make containers

A JS hello to build a first simple workflow.

    $ mkdir Development
    $ cd Development
    $ mkdir node-docker
    
Create a simple REST API with a a mock server:

    $ cd node-docker
    $ npm init -y    
    Wrote to /home/{user}/Development/node-docker/package.json:
    {
        "name": "node-docker",
        "version": "1.0.0",
        "description": "",
        "main": "index.js",
        "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
        },
        "keywords": [],
        "author": "",
        "license": "ISC"
    }
    
    $ npm install ronin-server ronin-mocks
    $ touch server.js
    
Open in VSCode and add to `server.js`:

    const ronin     = require( 'ronin-server' )
    const mocks     = require( 'ronin-mocks' )

    const server = ronin.server()

    server.use( '/', mocks.server( server.Router(), false, true ) )
    server.start()
    
Create dockerfile:

    # syntax=docker/dockerfile:1

    FROM node:14.16.0
    ENV NODE_ENV=production

    WORKDIR /app

    COPY ["package.json", "package-lock.json*", "./"]

    RUN npm install --production

    COPY . .

    CMD [ "node", "server.js" ]
    
Create .dockerignore file with content:

    node_modules
    
Build image:
    
    $ sudo docker build --tag node-docker .
    [sudo] password for nina: 
    Sending build context to Docker daemon  12.98MB
    Step 1/7 : FROM node:14.16.0
    14.16.0: Pulling from library/node
    ...
    Successfully built b00e291ed20a
    Successfully tagged node-docker:latest

Create database container.

Create volumes to store persistent data and configuration:

    $ sudo docker volume create mongodb
    $ sudo docker volume create mongodb_config
    
Create a user-defined bridge network for application and database to talk with each other (and gives a DNS lookup service useful for creating the connection string later):
    
    $ docker network create mongodb

Docker will pull the image from Hub and run it locally:

    $ sudo docker run -it --rm -d -v mongodb:/data/db \
      -v mongodb_config:/data/configdb -p 27017:27017 \
      --network mongodb \
      --name mongodb \
      mongo
    Unable to find image 'mongo:latest' locally
    latest: Pulling from library/mongo
    ...
    Digest: sha256:8b35c0a75c2dbf23110ed2485feca567ec9ab743feee7a0d7a148f806daf5e86
    Status: Downloaded newer image for mongo:latest
    c359e054deed443eb6be849c300e712b4f7192b132b2997070a605ca0f721317

Update `server.js` to use MongoDB and not an in-memory data store (add the `ronin-database` module and update the code to connect to the database and set the in-memory flag to false).

    const ronin     = require( 'ronin-server' )
    const mocks     = require( 'ronin-mocks' )
    const database  = require( 'ronin-database' )
    const server = ronin.server()

    database.connect( process.env.CONNECTIONSTRING )
    server.use( '/', mocks.server( server.Router(), false, false ) )
    server.start()
    
Run the mongodb container and then the rest-server container.
    
## Using Compose

Creating a `docker-compose.dev.yml`:

    version: '3.8'

    services:
     notes:
      build:
       context: .
      ports:
       - 8000:8000
       - 9229:9229
      environment:
       - SERVER_PORT=8000
       - CONNECTIONSTRING=mongodb://mongo:27017/notes
      volumes:
       - ./:/app
      command: npm run debug

     mongo:
      image: mongo:4.2.8
      ports:
       - 27017:27017
      volumes:
       - mongodb:/data/db
       - mongodb_config:/data/configdb
    volumes:
     mongodb:
     mongodb_config:

To start the application in debug mode, add a line to `package.json` in the scripts section:

    "debug": "nodemon --inspect=0.0.0.0:9229 server.js"
    
Install the `nodemon`:

    $ npm install nodemon
    
Start application

    $ docker-compose -f docker-compose.dev.yml up --build
    Creating network "node-docker_default" with the default driver
    ERROR: could not find an available, non-overlapping IPv4 address pool among the defaults to assign to the network
   
To remove all networks not used by at least one container:

    $ docker network prune
    WARNING! This will remove all custom networks not used by at least one container.
    Are you sure you want to continue? [y/N] y
    Deleted Networks:
    mongodb

Still error. Hmmm. I have just installed a VPN on this VM. Openvpn adds routes for `0.0.0.0/1` and `128.0.0.0/1` (the entire IP range), and docker can not find a range of IP addresses to create a private network. I do not want to disable (`service openvpn stop`) it.  Thinking ... But for now I will just disable the vpn. Works like a charm now. Nearly.

    [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
    
[DEP0018](https://github.com.cnpmjs.org/nodejs/node/issues/32081) is a highly contested warning.

"Rejection" is the canonical term for a promise reporting an error. As defined in ES6, a promise is a state machine representation of an asynchronous operation and can be in one of 3 states: "pending", "fulfilled", or "rejected". A pending promise represents an asynchronous operation that's in progress and a fulfilled promise represents an asynchronous operation that's completed successfully. A rejected promise represents an asynchronous operation that failed for some reason. For example, trying to connect to a nonexistent MongoDB instance using the MongoDB driver will give a promise rejection. Apparently `mongo` does not exist before `notes` does.   

A possible solution is to add the mongo dependency in the notes service in`docker-compose.dev.yml`:

    version: '3.8'

    services:
     notes:
      build:
       context: .
      ports:
       - 8000:8000
       - 9229:9229
      depends_on:
       - ¨mongo¨
      environment:
       - SERVER_PORT=8000
       - CONNECTIONSTRING=mongodb://mongo:27017/notes
      volumes:
       - ./:/app
      command: npm run debug
     mongo:
      image: mongo:4.2.8
      ports:
       - 27017:27017
      volumes:
       - mongodb:/data/db
       - mongodb_config:/data/configdb
    volumes:
     mongodb:
     mongodb_config:
     
But, this way [Docker controls the start order of services not the ready state](https://docs.docker.com/compose/startup-order/). Looking into [controlled compose](https://github.com/dansteen/controlled-compose), but for now will continue.

## Debugging
Install Chrome for the Open dedicated DevTools for Node (about:inspect)

`server.js`:

    const ronin     = require( 'ronin-server' )
    const mocks     = require( 'ronin-mocks' )
    const database  = require( 'ronin-database' )
    const server = ronin.server()

    database.connect( process.env.CONNECTIONSTRING )
    server.use( '/foo', (req, res) => {
        return res.json({ "foo": "bar" })
      }) 
    server.use( '/', mocks.server( server.Router(), false, false ) )
    server.start()
    
Check in run terminal that nodemon noticed the changes and reloaded our application.

Go to Chrome DevTools and set a breakpoint on the line containing the `return res.json({ "foo": "bar" })` statement, and then run curl command to trigger the breakpoint:

    $ curl --request GET --url http://localhost:8000/foo
    
Check code stopped and debugging can be used (minimally inspect and watch variables, set conditional breakpoints, view stack traces).

Note: Debugging services running in a container is possible, but brings additional complexity. Use normal debugging by default, and debugging in the container only when needed.

## Testing

Make a test directory with a `test.js` in it:

    $ mkdir -p test
    
`test.js`:

    var assert = require('assert');
    describe('Array', function() {
      describe('#indexOf()', function() {
        it('should return -1 when the value is not present', function() {
          assert.equal([1, 2, 3].indexOf(4), -1);
        });
      });
    });

POST a JSON payload:

    $ curl --request POST \
    >   --url http://localhost:8000/test \
    >   --header 'content-type: application/json' \
    >   --data '{
    > "msg": "testing"
    > }'
    {"code":"success","payload":{"_id":"60ad2f626b284b002c4cad93","msg":"testing","createDate":"2021-05-25T17:09:54.314Z"}}

GET request to the same endpoint to make sure the JSON payload was saved and retrieved correctly:

    $ curl http://localhost:8000/test
    {"code":"success","meta":{"total":2,"count":2},"payload":[{"_id":"60ad04b94f0bd2004297cea9","msg":"testing","createDate":"2021-05-25T14:07:53.403Z"},{"_id":"60ad2f626b284b002c4cad93","msg":"testing","createDate":"2021-05-25T17:09:54.314Z"}]}
    
Install mocha:

    $ npm install --save-dev mocha
    
Update `package.json` with `"test": "mocha ./**/*.js"`:

    {
      "name": "node-docker",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "mocha ./**/*.js",
        "debug": "nodemon --inspect=0.0.0.0:9229 server.js"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "dependencies": {
        "nodemon": "^2.0.7",
        "ronin-database": "^0.1.1",
        "ronin-mocks": "^0.1.6",
        "ronin-server": "^0.1.3"
      }
    }

Dockerfile for multi-stage testing:

    # syntax=docker/dockerfile:1

    FROM node:14.16.0

    WORKDIR /code

    COPY package.json package.json
    COPY package-lock.json package-lock.json

    FROM base as test
    RUN npm ci
    COPY . .
    CMD [ "npm", "run", "test" ]

    FROM base as prod
    RUN npm ci --production
    COPY . .
    CMD [ "node", "server.js" ]
    
Build:

    $ docker build -t node-docker --target test .
    Sending build context to Docker daemon   76.8kB
    Step 1/8 : FROM node:14.16.0 as base
     ---> abea835c0b3b
    Step 2/8 : WORKDIR /code
     ---> Running in 72677d4774b5
    Removing intermediate container 72677d4774b5
     ---> ad9ab2a8358a
    Step 3/8 : COPY package.json package.json
     ---> c3fd1fc57e2e
    Step 4/8 : COPY package-lock.json package-lock.json
     ---> 9db103078488
    Step 5/8 : FROM base as test
     ---> 9db103078488
    Step 6/8 : RUN npm ci
     ---> Running in cd130ecf5d46

    > nodemon@2.0.7 postinstall /code/node_modules/nodemon
    > node bin/postinstall || exit 0

    Love nodemon? You can now support the project via the open collective:
     > https://opencollective.com/nodemon/donate

    added 229 packages in 15.946s
    Removing intermediate container cd130ecf5d46
     ---> 2fd75d778b1f
    Step 7/8 : COPY . .
     ---> 2c7975eddeea
    Step 8/8 : CMD [ "npm", "run", "test" ]
     ---> Running in 2598bf5a1a51
    Removing intermediate container 2598bf5a1a51
     ---> 02fe284e0759
    Successfully built 02fe284e0759
    Successfully tagged node-docker:latest
    
And run:

    $ docker run -it --rm -p 8000:8000 node-docker

    > node-docker@1.0.0 test /code
    > mocha ./**/*.js

    sh: 1: mocha: not found
    npm ERR! code ELIFECYCLE
    
    ...
    
  Yet `mocha` is installed. Installing it globally (`-g` flag) hangs the build process at step 6.
  
    $ docker build -t node-docker --target test .
    Sending build context to Docker daemon  97.28kB
    Step 1/8 : FROM node:14.16.0 as base
     ---> abea835c0b3b
    Step 2/8 : WORKDIR /code
     ---> Using cache
     ---> ad9ab2a8358a
    Step 3/8 : COPY package.json package.json
     ---> 978f4fa26cbf
    Step 4/8 : COPY package-lock.json package-lock.json
     ---> 4e52fac77355
    Step 5/8 : FROM base as test
     ---> 4e52fac77355
    Step 6/8 : RUN npm ci
     ---> Running in bc8e844a3401

Removing `node_modules`, then reinstalling everything with `npm install` did the trick.

    $ docker run -it --rm -p 8000:8000 node-docker

    > node-docker@1.0.0 test /code
    > mocha ./**/*.js



      Array
        #indexOf()
          ✓ should return -1 when the value is not present


      1 passing (4ms)
      
  Update Dockerfile:

    # syntax=docker/dockerfile:1
    FROM node:14.16.0 as base

    WORKDIR /code

    COPY package.json package.json
    COPY package-lock.json package-lock.json

    FROM base as test
    RUN npm ci
    COPY . .
    RUN npm run test

    FROM base as prod
    RUN npm ci --production
    COPY . .
    CMD [ "node", "server.js" ]
    
To run tests, now only the build command suffices:

    $ docker build -t node-docker --target test .
    

      
