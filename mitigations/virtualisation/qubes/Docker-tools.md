# Server with docker (The plan)

Based on
* https://www.docker.com
* https://www.qubes-os.org

Versions

    Qubes-OS 4.0.4

Guides
* https://docs.docker.com/engine/install/centos/


## Template VM 

- [ ] Install the standard CentOS TemplateVM in dom0
- [ ] Clone the templateVM (docker has security implications)
- [ ] Check CentOS version. Docker Engine requires a maintained version of CentOS 7 or 8. Archived versions are not supported or tested.
- [ ] The centos-extras repository must be enabled. In a normal CentOS installation this repository is enabled by default. Check that it is. If it is not, it must either be added to or enabled in the cloned TemplateVM.
- [ ] Check the overlay2 storage driver is installed. It is not required, but is recommended.
- [ ] Check yum-utils are installed.

## Install Docker

- [ ] Go to settings of the cloned templateVM (in the Qubes manager). Under firewall rules, check on allow full access for 5 min.
- [ ] Install the docker repository in the cloned templateVM

```
    $ sudo yum-config-manager \
--add-repo \
https://download.docker.com/linux/centos/docker-ce.repo
```

- [ ] Install the latest version of Docker Engine and containerd

```
     $ sudo yum install docker-ce docker-ce-cli containerd.io
```

If prompted to accept the GPG key, verify that the fingerprint matches 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35, and if so, accept it.

The docker group is created, but no users are added to the group. See [Docker daemon attack surface](https://docs.docker.com/engine/security/#docker-daemon-attack-surface).

- [ ] To [Run the Docker daemon as a non-root user (Rootless mode)](https://docs.docker.com/engine/security/rootless/) add a user:

```
$ sudo usermod -aG docker $USER
$ newgrp docker
```
    
- [ ] Enable docker

```
$ sudo systemctl enable docker
```

- [ ] Bindings (appvms get to keep customisations)

```
sudo mkdir -p /rw/config/qubes-bind-dirs.d
sudo cat << EOF > /rw/config/qubes-bind-dirs.d/50_user.conf
binds+=( '/var/lib/docker' )
binds+=( '/etc/docker' )
EOF
```
    
Maybe more needs to be added to bind-dirs. If not works, make a stand alone AppVM, based on the template. 

## AppVM

- [ ] Make an AppVM based on the dockerhost template 

## Testing

- [ ] In the AppVM, run

```
    $ docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.

When restarting the appVM, and doing `docker run hello-world` again, check it does not have to download the image again.

## Notes

By default, appVM's only get 2G of storage. In the appvm settings from the qubes-manager, the first tab has "Disk Settings" where private storage size can be increased.
