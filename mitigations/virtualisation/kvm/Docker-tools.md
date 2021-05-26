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
  - [Installing VSCode](#installing-vscode)

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
    Docker version 20.10.6, build 370c289
    
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
    docker-compose version 1.29.2, build 5becea4c

## Installing docker machine

To install [docker machine](https://github.com/docker/machine), see [releases](https://github.com/docker/machine/releases).

    $ sudo curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` -o /usr/local/bin/docker-machine &&
    sudo chmod +x /usr/local/bin/docker-machine

Check with:

    $ docker-machine version
    docker-machine version 0.16.2, build bd45ab13
    
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
    
## Installing VSCode

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

In VSCode, install the [docker extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker).

## Installing python

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



    
