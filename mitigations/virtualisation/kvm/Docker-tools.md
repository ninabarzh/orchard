# Docker tools

We can run our containers in Docker Machine and get the composition done by Docker Compose. Well, at least that is the plan.

* Compose defines a multi-container application in a single file, then spins the application up with a single command which does everything that needs to be done to get it running.
* Machine can create Docker hosts on local computer, on cloud providers, and inside a data center. Given a token, it creates servers, installs Docker on them, then configures the Docker client to talk to them.

- [Docker tools](#docker-tools)
  - [Installing centos in VM](#installing-centos-in-vm)
  - [Installing docker](#installing-docker)
  - [Installing docker compose](#installing-docker-compose)
  - [Installing docker machine](#installing-docker-machine)
  - [Scripts](#scripts)
    - [See active machines](#see-active-machines)
    - [Switch between machines](#switch-between-machines)
    - [Bash completion](#bash-completion)
  - [Installing Node.js](#installing-nodejs)
  - [Installing VScode](#installing-vscode)
  - [Hello world JS](#hello-world-js)
    - [Use Compose locally](#use-compose-locally)
  - [Hello world Python](#hello-world-python)

## Installing centos in VM

Went without a glitch. Will take getting used to though. Prior to the eighth iteration, CentOS used the yum package manager. As of CentOS 8, package management has migrated from yum to Dandified Yum (DNF). `yum` is also still working. 

    # adduser -aG wheel [user]
    
Then as `user`:
    
    $ sudo dnf install curl -y

## Installing docker

To add the Docker-CE repository:

    $ sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
    

To install the latest version of docker:

    $ sudo dnf install docker-ce --nobest -y

    $ sudo systemctl start docker
    $ sudo systemctl enable docker

Check with:

    $ sudo docker --version
    
Add user to the docker group (otherwise you may get connection refusals later):

    $ sudo usermod -a -G docker {user}

Configure Docker to start on boot:

    $ sudo systemctl enable docker.service
    $ sudo systemctl enable containerd.service

    
## Installing docker compose

To install [docker compose](https://github.com/docker/compose), see [releases](https://github.com/docker/compose/releases).

    $ sudo curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose &&
    sudo chmod +x /usr/local/bin/docker-compose

Check with:

    $ docker-compose --version

## Installing docker machine

To install [docker machine](https://github.com/docker/machine), see [releases](https://github.com/docker/machine/releases).

    $ sudo curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` -o /usr/local/bin/docker-machine &&
    sudo chmod +x /usr/local/bin/docker-machine

Check with:

    $ docker-machine version
    
## Scripts
    
Add [these 3 scripts](https://github.com/docker/machine/tree/master/contrib/completion/bash). If need be adapt scripts.

### See active machines

To make it possible to see the active machine in the bash prompt:

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine-prompt.bash -O /etc/bash_completion.d/docker-machine-prompt.bash
    
In `~/.bashrc` add:

    export PS1='[\u@\h \W$(__docker_machine_ps1 " [%s]")]\$ '
    
### Switch between machines

`docker-machine-wrapper.bash` adds a use subcommand to the docker-machine command to switch between Dockerised Machines:

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine-wrapper.bash -O /etc/bash_completion.d/docker-machine-wrapper.bash
    
### Bash completion

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine.bash -O /etc/bash_completion.d/docker-machine.bash

If not works, the `bash-completion` package may not be installed:

    sudo dnf install bash-completion
    
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
    
## Installing VScode

    $ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    
    $ sudo vi /etc/yum.repos.d/vscode.repo
    
Add content to enable the repository:

    [code]
    name=Visual Studio Code
    baseurl=https://packages.microsoft.com/yumrepos/vscode
    enabled=1
    gpgcheck=1
    gpgkey=https://packages.microsoft.com/keys/microsoft.asc

Check with `cat`.

Install code:

    $ sudo dnf install code

## Hello world JS

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
    
### Use Compose locally

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

"Rejection" is the canonical term for a promise reporting an error. As defined in ES6, a promise is a state machine representation of an asynchronous operation and can be in one of 3 states: "pending", "fulfilled", or "rejected". A pending promise represents an asynchronous operation that's in progress and a fulfilled promise represents an asynchronous operation that's completed successfully. A rejected promise represents an asynchronous operation that failed for some reason. For example, trying to connect to a nonexistent MongoDB instance using the MongoDB driver will give a promise rejection. Apparently mongodb does not exist yet before notes does.   

Could possibly be dealt with by adding the mongo dependency in the notes service in`docker-compose.dev.yml`:

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

    
## Hello world Python
