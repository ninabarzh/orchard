# Docker tools

We can run our containers in Docker Machine and get the composition done by Docker Compose. Well, at least that is the plan.

* Compose defines a multi-container application in a single file, then spins the application up with a single command which does everything that needs to be done to get it running.
* Machine can create Docker hosts on local computer, on cloud providers, and inside a data center. Given a token, it creates servers, installs Docker on them, then configures the Docker client to talk to them.

- [Docker tools](#docker-tools)
  - [Installing centos in VM](#installing-centos-in-vm)
  - [Installing docker](#installing-docker)
  - [Installing docker compose](#installing-docker-compose)
  - [Installing docker machine](#installing-docker-machine)

## Installing centos in VM

Went without a glitch. Will take getting used to though. Prior to the eighth iteration, CentOS used the yum package manager. As of CentOS 8, package management has migrated from yum to Dandified Yum (DNF). yum is also still working. 

    # adduser -aG wheel [user]
    
Then as user:
    
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
    
## Installing docker compose

To install [docker compose]([Docker compose releases](https://github.com/docker/compose). See [releases]([Docker compose releases](https://github.com/docker/compose/releases)

    $ sudo curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose &&
    sudo chmod +x /usr/local/bin/docker-compose

Check with

    $ docker-compose --version

## Installing docker machine

To install [docker machine](https://github.com/docker/machine). See [releases](https://github.com/docker/machine/releases).

    $ sudo curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` -o /usr/local/bin/docker-machine &&
    sudo chmod +x /usr/local/bin/docker-machine

Check with:

    $ docker-machine version
    
## Scripts
    
Add [these 3 scripts](https://github.com/docker/machine/tree/master/contrib/completion/bash). If need be adapt scripts.

### See active machines

To make it possible to see the active machine in the bash prompt:

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine-prompt.bash -O /etc/bash_completion.d/docker-machine-prompt.bash
    
In ~/.bashrc add:

    export PS1='[\u@\h \W$(__docker_machine_ps1 " [%s]")]\$ '
    
### Switch between machines

docker-machine-wrapper.bash adds a use subcommand to the docker-machine command to switch between Dockerised Machines:

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine-wrapper.bash -O /etc/bash_completion.d/docker-machine-wrapper.bash
    
### Bash completion

    $ sudo wget https://raw.githubusercontent.com/docker/machine/master/contrib/completion/bash/docker-machine.bash -O /etc/bash_completion.d/docker-machine.bash

If not works, the bash-completion package may not be installed:

    sudo dnf install bash-completion





