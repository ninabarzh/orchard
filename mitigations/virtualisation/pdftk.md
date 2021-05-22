# pdftk

`pdftk` is missing from the official repository. In case you wish to avoid the JS version, and wish to avoid snap, try this solution (adapted from a solution by abu-bua). The below is for Ubuntu because I was installing the sift workstation (forensics), but for Debian and others, just go back to the last version that supported it, and adapt the below. I'll come back later and add a few.

## Ubuntu

Install schroot

    $ sudo apt install schroot debootstrap

Create `/etc/schroot/chroot.d/xenial.conf` file with content:

    [xenial]
    description=Ubuntu 16.04
    directory=/srv/chroot/xenial
    root-users=$USER
    type=directory
    users=$USER

Create the xenial directory:

    $ sudo mkdir -p /srv/chroot/xenial

Install:

    $ sudo debootstrap xenial /srv/chroot/xenial
    [snip]
    I: Base system installed successfully

Set up the xenial apt repositories in `/srv/chroot/xenial/etc/apt/sources.list`:

    deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
    deb http://security.ubuntu.com/ubuntu xenial-security main restricted universe multiverse

Update:

    $ schroot -c xenial -u root apt-get update

Install `pdftk`

    $ schroot -c xenial -u root apt-get install pdftk

It can now be used using `schroot -c xenial -- pdftk`

Add an alias in `~/.bash_aliases` to be able to call it as `pdftk`:

    alias pdftk='schroot -c xenial -- pdftk'

Test with:

    $ pdftk --version
