# Hello world Python

The simplest workflow for a python application in docker on [Docker tools VM](../kvm/Docker-tools.md).

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
