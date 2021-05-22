# Docker machine (The plan)

## Installing centos in VM

Went without a glitch. Will take getting used to though.

## Installing docker machine

Install [docker machine](https://github.com/docker/machine). See [releases](https://github.com/docker/machine/releases)

    $ curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
    chmod +x /tmp/docker-machine &&
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine

Check with:

    $ docker-machine version
    
## Add completion

[These 3 scripts](https://github.com/docker/machine/tree/master/contrib/completion/bash). If need be adapt scripts.
