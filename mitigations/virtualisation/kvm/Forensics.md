# Digital forensics

Create an Ubuntu 20.04 VM, install the sift workstation repository on it per [Sans sift workstation](https://www.sans.org/tools/sift-workstation) and [sift-cli installation](https://github.com/teamdfir/sift-cli#installation) guides:

[CLI] Update returned exit code not zero after "Running: sift-config" during sift install.

## Install pdftk

 `pdftk` is missing from the official repository. I wish to avoid the JS version, and wish to avoid snap, so I tried this solution (by abu-bua):

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
