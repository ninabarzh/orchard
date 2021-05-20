# Installation KVM

- [Installation KVM](#installation-kvm)
  - [Preparation](#preparation)
  - [Installation](#installation)
  - [Test](#test)
  - [Creating VM's](#creating-vms)
    - [GUI](#gui)
    - [CLI](#cli)
  - [Importing OVA's](#importing-ovas)
  - [Cloning VM's](#cloning-vms)
  - [Autostart](#autostart)

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

## Test

To check virsh is running and chosen users have access:

    $ virsh list --all

Not much to see yet, but confirms running without a problem.

Check `libvirtd` service is running:

    $ sudo systemctl status libvirtd

If not active, try:

    $ sudo systemctl enable --now libvirtd

## Creating VM's

* Download an `.iso`

### GUI

    $ sudo apt install virt-manager

Start virt-manager with:

    $ sudo virt-manager

And install the `.iso`

### CLI

Use the `virt-install` command to create a VM via Linux terminal. Example:

The virtual machine will get "default" networking.

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

To list the available formats for qemu images
    $ qemu-img -h | tail -n1

And to convert to a format qemu/kvm can import:

$ qemu-img convert -O qcow2 [name].vmdk [newname].qcow2

Put the qcow2 image in the kvm guest repository and create a new Guest VM with virt-manager using the image.

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

To check libvirtd service (`/etc/init.d/libvirtd`) is started on boot:

    $ chkconfig libvirtd on

or:

    $ systemctl enable libvirtd
