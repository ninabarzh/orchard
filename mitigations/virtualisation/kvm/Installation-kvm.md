# Installation KVM

- [Installation KVM](#installation-kvm)
  - [Preparation](#preparation)
  - [Installation](#installation)
  - [Tests](#tests)
  - [Creating VM's](#creating-vms)
    - [GUI](#gui)
    - [CLI](#cli)
  - [Importing OVA's](#importing-ovas)
  - [Cloning VM's](#cloning-vms)
  - [Autostart](#autostart)
  - [Sharing files](#sharing-files)

## Preparation

Check if the CPU supports hardware virtualization:

    $ egrep -c '(vmx|svm)' /proc/cpuinfo

If a value of 0 is returned, the processor is not capable of running KVM. 

To check for KVM acceleration:

    $ sudo apt install cpu-checker

    $ sudo kvm-ok

## Installation

To install essential KVM packages:

    $ sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils

Only members of the `libvirt` and `kvm` groups can run VM's. Add user(s):

    $ sudo adduser [username] libvirt

    $ sudo adduser [username] kvm

To delete users from the groups, replace `adduser` with `deluser`.

## Tests

To check `virsh` is running and chosen users have access:

    $ virsh list --all

Not much to see yet, but confirms running without a problem.

To check `libvirtd` service (`/etc/init.d/libvirtd`) is started on boot:

    $ chkconfig libvirtd on

or:

    $ systemctl enable libvirtd

If not active, try:

    $ sudo systemctl enable --now libvirtd

## Creating VM's

* Download an `.iso`

### GUI

    $ sudo apt install virt-manager

Start `virt-manager` with:

    $ sudo virt-manager

And install the `.iso`

### CLI

Use the `virt-install` command to create a VM via Linux terminal. Example (the virtual machine will get "default" networking):

    virt-install \
    --name vmname \
    --memory 2048 \
    --vcpus 2 \
    --os-type=linux \
    --os-variant=centos7.0 \
    --location /iso-images/CentOS-7-x86_64-DVD-7.9.2009.iso \
    --extra-args="console=tty0 console=ttyS0,115200n8" \
    --disk=/iso-images/CentOS-7-x86_64-DVD-7.9.2009.iso,device=cdrom \
    --disk=/main-storage-pool/testvm-01.qcow2,size=10 \
    --network=default \
    --graphics none

## Importing OVA's

Extract the files:

    $ tar xvf [vmname].ova

The `.vmdk` file format was developed for the use in VMWare or Virtualbox. It is an open format.

To list the available formats for `qemu` images
    $ qemu-img -h | tail -n1

And to convert to a format `qemu/kvm` can import:

    $ qemu-img convert -O qcow2 [name].vmdk [newname].qcow2

Put the `qcow2` image in the kvm guest repository and create a new Guest VM with `virt-manager` using the image.

## Cloning VM's

To clone an existing KVM VM:

    $ sudo virt-clone --original [vmname] --auto-clone

or

    $ sudo virt-clone --original [vmname] --name [new vmname] --auto-clone

or

    $ sudo virt-clone --original [vmname] \
--name [new vmname] --file {/var/lib/libvirt/images/[new vmname file]}

## Autostart

To start a VM at boot time:

    $ sudo virsh autostart [vmname]

In my case my "default" VM containing my communication.

    $ sudo virsh autostart default
    Domain default marked as autostarted

To disable autostart:

    $ virsh autostart [vmname] --disable

## Sharing files

Not recommended (exposing host-managed files to VMs!), but an option in special circumstances.

On the host, make a directory for sharing:

    $ mkdir /home/{username}/vmshare

In the virt-manager GUI, click on the "i" icon => Add Hardware => Filesystem. 
* Type: mount
* Driver: default. The other options are `Handle` and `Path`.
Path is the option you want to use
* Mode: - Mode is how UIDs and permissions are handled between guest and host.           
  * `Passthrough` - files on the filesystem are directly created with client-user’s credentials. The guest may try to set ownership permissions on a file, and the host may block it based on the qemu’s user account. This could be an option if running a VM as user, and running apps in the VM as the same user.
  * `Squashed` - is equivalent to passthrough security model with the exception of ignoring failure of privileged operations like `chown`. This could be a slightly better option if running a VM as user, and running apps in the VM as the same user.
  * `Mapped` - Files are created with qemu user credentials and the client-user’s credentials are saved in extended attributes, separating host and client permissions. On the host, you have to `chown -R qemu:qemu` all the files you intend to share with the guest. On the guest, you can chown/chmod as much as you want. Any metadata changes made by the guest are stored in global extended attributes, allowing sharing between guests, because they will see the same UIDs.
* Source path: The path on the host you want to export, for example `/home/{username}/vmshare`
* Target path: Not a path, but a label, identifying this share to the guest, for example `/vmshare`
* You can export the filesystem as a readonly mount, for example if you want only one guest to be able to write changes to the data, and the others only be able to read it.

Make `libvirt-qemu` the owner of the directory on the host, and if needed `chmod` the directory:

    $ sudo chown libvirt-qemu /home/{username}/vmshare

Make a directory on the guest, and mount the filesystem onto that folder:

    $ sudo mount -t 9p -o trans=virtio,version=9p2000.L /vmshare /home/{username}/vmshare

Note that RHEL and CentOS do not enable the `9p` filesystem driver in their kernel. Try [Mount a 9p Share in a Centos 7 or 8 KVM Guest using kernel-plus](https://www.dvlv.co.uk/how-to-mount-a-9p-share-in-a-centos-7-or-8-kvm-guest.html) or [kernel-ml](https://elrepo.org/tiki/kernel-ml).