# Hello world Python

The simplest workflow for a python application in docker on [Docker tools VM](../kvm/Docker-tools.md), based on the docker tutorials, adapted to my environment and expanded.

- [Hello world Python](#hello-world-python)
  - [Installing Python](#installing-python)
  - [Make containers](#make-containers)
  - [Using Compose](#using-compose)
  - [Debugging](#debugging)
  - [Testing](#testing)

## Installing Python

Unlike other Linux distributions, Python is not installed by default on CentOS 8.

Per repository:

    $ sudo dnf install python3

and

    $ python3 --version
    Python 3.6.8

But I need 3.8+. Hence:

    $ sudo dnf install wget yum-utils make gcc openssl-devel bzip2-devel libffi-devel zlib-devel
    
Download (see [releases](https://www.python.org/ftp/python/)) and install:

    $ wget https://www.python.org/ftp/python/3.9.5/Python-3.9.5.tgz
    $ tar xzf Python-3.9.5.tgz
    $ cd Python-3.9.5
    $ sudo ./configure --with-system-ffi --with-computed-gotos --enable-loadable-sqlite-extensions
    $ sudo make -j ${nproc}
    
Make alternative install:

    $ sudo make altinstall
    ...
    Installing collected packages: setuptools, pip
      WARNING: The script pip3.9 is installed in '/usr/local/bin' which is not on PATH.
      Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
    Successfully installed pip-21.1.1 setuptools-56.0.0
    WARNING: Running pip as root will break packages and permissions. You should install packages reliably by using venv: https://pip.pypa.io/warnings/venv
    
Check with:

    $ python3.9 -V 
    Python 3.9.5

## Make containers

    $ mkdir python-docker
    
Install flask and freeze rqs

    $ sudo pip3.9 install Flask
    $ pip3.9 freeze > requirements.txt
    $ touch app.py
    
Open vscode and add content to `app.py`:

    from flask import Flask
    app = Flask(__name__)

    @app.route('/')
    def hello_world():
        return 'Hello, Docker!'
        
Check by starting application:

    $ python3.9 -m flask run
     * Environment: production
       WARNING: This is a development server. Do not use it in a production deployment.
       Use a production WSGI server instead.
     * Debug mode: off
     * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)

Create Dockerfile:
     
    # syntax=docker/dockerfile:1

    FROM python:3.9.5

    WORKDIR /app

    COPY requirements.txt requirements.txt
    RUN pip3.9 install -r requirements.txt

    COPY . .

    CMD [ "python3.9", "-m" , "flask", "run", "--host=0.0.0.0"]

Build image:

    $ docker build --tag python-docker .
    Sending build context to Docker daemon   5.12kB
    Step 1/6 : FROM python:3.9.5
    3.9.5: Pulling from library/python
    d960726af2be: Pull complete 
    e8d62473a22d: Pull complete 
    8962bc0fad55: Pull complete 
    65d943ee54c1: Pull complete 
    532f6f723709: Pull complete 
    1334e0fe2851: Pull complete 
    062ada600c9e: Pull complete 
    aec2e3a89371: Pull complete 
    1ec7c3bcb4b2: Pull complete 
    Digest: sha256:65367d1d3eb47f62127f007ea1f74d1ce11be988044042ab45d74adc6cfceb21
    Status: Downloaded newer image for python:3.9.5
     ---> 5b3b4504ff1f
    Step 2/6 : WORKDIR /app
     ---> Running in 7f9ce3f322c8
    Removing intermediate container 7f9ce3f322c8
     ---> fa5afe0ed131
    Step 3/6 : COPY requirements.txt requirements.txt
     ---> 0a6e8a47cfe2
    Step 4/6 : RUN pip3.9 install -r requirements.txt
     ---> Running in b9ee8a184ed8
    Collecting click==8.0.1
      Downloading click-8.0.1-py3-none-any.whl (97 kB)
    Collecting Flask==2.0.1
      Downloading Flask-2.0.1-py3-none-any.whl (94 kB)
    Collecting itsdangerous==2.0.1
      Downloading itsdangerous-2.0.1-py3-none-any.whl (18 kB)
    Collecting Jinja2==3.0.1
      Downloading Jinja2-3.0.1-py3-none-any.whl (133 kB)
    Collecting MarkupSafe==2.0.1
      Downloading MarkupSafe-2.0.1-cp39-cp39-manylinux2010_x86_64.whl (30 kB)
    Collecting Werkzeug==2.0.1
      Downloading Werkzeug-2.0.1-py3-none-any.whl (288 kB)
    Installing collected packages: MarkupSafe, Werkzeug, Jinja2, itsdangerous, click, Flask
    Successfully installed Flask-2.0.1 Jinja2-3.0.1 MarkupSafe-2.0.1 Werkzeug-2.0.1 click-8.0.1 itsdangerous-2.0.1
    WARNING: Running pip as root will break packages and permissions. You should install packages reliably by using venv: https://pip.pypa.io/warnings/venv
    Removing intermediate container b9ee8a184ed8
     ---> e8da28a86d98
    Step 5/6 : COPY . .
     ---> bbfcf6aea711
    Step 6/6 : CMD [ "python3.9", "-m" , "flask", "run", "--host=0.0.0.0"]
     ---> Running in 28c4e9b32583
    Removing intermediate container 28c4e9b32583
     ---> a89aa71ba28b
    Successfully built a89aa71ba28b
    Successfully tagged python-docker:latest
    
Shit. WARNING: Running pip as root will break packages and permissions. You should install packages reliably by using venv: https://pip.pypa.io/warnings/venv
Not using venv. Using docker.

    $ docker images
    REPOSITORY          TAG       IMAGE ID       CREATED          SIZE
    python-docker       latest    a89aa71ba28b   10 minutes ago   896MB
    node-docker         latest    0517c3e1a6f2   6 hours ago      968MB
    node-docker_notes   latest    0404e6f8e810   24 hours ago     961MB
    python              3.9.5     5b3b4504ff1f   46 hours ago     886MB
    mongo               latest    07630e791de3   2 weeks ago      449MB
    node                14.16.0   abea835c0b3b   8 weeks ago      943MB
    
Run image inside of a container, mapping the host’s port 5000 to the container’s port 5000 (`--publish 5000:5000`):

    $ docker run --publish 5000:5000 python-docker
     * Environment: production
       WARNING: This is a development server. Do not use it in a production deployment.
       Use a production WSGI server instead.
     * Debug mode: off
     * Running on all addresses.
       WARNING: This is a development server. Do not use it in a production deployment.
     * Running on http://172.17.0.2:5000/ (Press CTRL+C to quit)
    172.17.0.1 - - [26/May/2021 17:54:38] "GET / HTTP/1.1" 200 -
    
Open a new terminal and make a GET request to the server:

    $ curl localhost:5000
    Hello, Docker!
    
Create database containers.

Create volumes to store persistent data and configuration:
    
    $ docker volume create mysql
    $ docker volume create mysql_config
    
Create a user-defined bridge network for application and database to talk with each other (and gives a DNS lookup service useful for creating the connection string later):

    $ docker network create mysqlnet
    
Docker will pull the image from Hub and run it locally:

    $ docker run --rm -d -v mysql:/var/lib/mysql \
      -v mysql_config:/etc/mysql -p 3306:3306 \
      --network mysqlnet \
      --name mysqldb \
      -e MYSQL_ROOT_PASSWORD=p@ssw0rd1 \
      mysql

Update `app.py` to use MySQL as a datastore, and add some routes to the server (fetching records and inserting records):
  
    import mysql.connector
    import json
    from flask import Flask

    app = Flask(__name__)

    @app.route('/')
    def hello_world():
      return 'Hello, Docker!'

    @app.route('/widgets')
    def get_widgets() :
      mydb = mysql.connector.connect(
        host="mysqldb",
        user="root",
        password="p@ssw0rd1",
        database="inventory"
      )
      cursor = mydb.cursor()


      cursor.execute("SELECT * FROM widgets")

      row_headers=[x[0] for x in cursor.description] #this will extract row headers

      results = cursor.fetchall()
      json_data=[]
      for result in results:
        json_data.append(dict(zip(row_headers,result)))

      cursor.close()

      return json.dumps(json_data)

    @app.route('/initdb')
    def db_init():
      mydb = mysql.connector.connect(
        host="mysqldb",
        user="root",
        password="p@ssw0rd1"
      )
      cursor = mydb.cursor()

      cursor.execute("DROP DATABASE IF EXISTS inventory")
      cursor.execute("CREATE DATABASE inventory")
      cursor.close()

      mydb = mysql.connector.connect(
        host="mysqldb",
        user="root",
        password="p@ssw0rd1",
        database="inventory"
      )
      cursor = mydb.cursor()

      cursor.execute("DROP TABLE IF EXISTS widgets")
      cursor.execute("CREATE TABLE widgets (name VARCHAR(255), description VARCHAR(255))")
      cursor.close()

      return 'init database'

    if __name__ == "__main__":
      app.run(host ='0.0.0.0')
      
  Import problem on `mysql.connector`:
  
    $ pip3.9 install mysql-connector-python
    $ pip3.9 freeze > requirements.txt
    
Build image:

    $ docker build --tag python-docker .
    
Run image:
    
    $ docker run \
      --rm -d \
      --network mysqlnet \
      --name rest-server \
      -p 5000:5000 \
      python-docker
      
Test:
  
    $ curl http://localhost:5000/initdb
    $ curl http://localhost:5000/widgets
    []
    
## Using Compose

`docker-compose.dev.yml`:

    version: '3.8'

    services:
     web:
      build:
       context: .
      ports:
      - 5000:5000
      volumes:
      - ./:/app

     mysqldb:
      image: mysql
      ports:
      - 3306:3306
      environment:
      - MYSQL_ROOT_PASSWORD=p@ssw0rd1
      volumes:
      - mysql:/var/lib/mysql
      - mysql_config:/etc/mysql

    volumes:
      mysql:
      mysql_config:

Build:

    $ docker-compose -f docker-compose.dev.yml up --build

Test:

    $ curl http://localhost:5000/initdb
    $ curl http://localhost:5000/widgets
    []

## Debugging

See [Debug Python within a container](https://code.visualstudio.com/docs/containers/debug-python)

Note: Debugging services running in a container is possible, but brings additional complexity. Use normal debugging by default, and debugging in the container only when needed.

## Testing

See [Python testing in Visual Studio Code](https://code.visualstudio.com/docs/python/testing)
