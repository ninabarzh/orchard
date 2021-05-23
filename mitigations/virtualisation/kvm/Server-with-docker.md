# Docker machine

Machine lets you create Docker hosts on your local computer, on cloud providers, and inside your own data center. Given a token, it creates servers, installs Docker on them, then configures the Docker client to talk to them.

## Installing centos in VM

Went without a glitch. Will take getting used to though. Prior to the eighth iteration, CentOS used the yum package manager. As of CentOS 8, package management has migrated from yum to Dandified Yum (DNF). 

## Docker Machine

Install [docker machine](https://github.com/docker/machine). See [releases](https://github.com/docker/machine/releases)

    $ curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
    chmod +x /tmp/docker-machine &&
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine

Check with:

    $ docker-machine version
    
Add completion with [these 3 scripts](https://github.com/docker/machine/tree/master/contrib/completion/bash). If need be adapt scripts.

