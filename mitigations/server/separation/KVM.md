# KVM

* The kernel module `kvm.ko` is a loadable kernel, giving VMs direct access to the hardware.
* KVM comes with processor-specific kernels `kvm-amd.ko` and `kvm-intel.ko`.
* It uses a combination of security-enhanced Linux (SELinux) and secure virtualization (sVirt) for VM security and isolation. 
  * `SELinux` sets up security boundaries around VMs. 
  * `sVirt` allows for applying Mandatory Access Control (MAC) security to guest VMs and prevents manual labelling errors.

## Installation

* `qemu-kvm` is the kvm client
* `libvirt` provides an abstraction language to define and launch Virtual Machines, and is normally used just to launch single VMs. It uses XML to represent and define the VM. The toolkit was written in C to interact with recent versions of Linux (and other OSes). 
* `libvirt-daemon-system` contains the configuration files to run the `libvirt daemon` as a system service.
* `virtinst` is a set of commandline tools to create virtual machines using `libvirt`.
* add the `--no-install-recommends apt option`, to prevent the installation of extraneous graphical packages

    $ sudo apt-get install --no-install-recommends qemu-kvm libvirt-clients libvirt-daemon-system virtinst    

Additionally:

* `qemu-system` supports the emulation of various architectures that can then be used in guests.
* `libguestfs-tools` is a set of tools for accessing and modifying virtual machine (VM) disk images.
* `virt-top` displays statistics of virtualised domains and uses many of the same keys and command line options as the top utility.
* `libosinfo-bin` gives info about the OS

## Networking
* `bridge-utils` 

    sudo apt-get install bridge-utils

## Configuration resources

* [Linux KVM wiki](https://www.linux-kvm.org/page/Main_Page) 
* [KVM Debian wiki](https://wiki.debian.org/KVM)

