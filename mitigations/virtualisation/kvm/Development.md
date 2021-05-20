# Development VM

- [Development VM](#development-vm)
  - [Git](#git)
  - [Github SSH](#github-ssh)
    - [Test](#test)

## Git

Download and install git (easy from repository):

    $ sudo apt install git

Check with:

    $ git --version

Set up git with user name and email:

    $ git config --global user.email "[name]@example.com"

## Github SSH

* If not have yet, [install SSH and learn about its options](../ssh.md).
* If not have yet, get a [github account](https://github.com/) or [gitlab account](https://about.gitlab.com/).

Make a key pair:

    $ ssh-keygen -f ~/github-key-rsa -t rsa -b 4096 -C "[name]@example.com"

Copy the public key (the contents of the newly-created github-key-rsa.pub file) into your clipboard.

* Go to your github or gitlab //Account Settings//
* Click //SSH Keys// on the left.
* Click //Add SSH Key// on the right.
* Add a label (like “Development VM on Thinkpad”) and paste the public key into the big text box.

### Test

In a terminal/shell on the local machine:

    $ ssh -T git@github.com
    Hi [name]! You've successfully authenticated, but Github does
not provide shell access.

We don't want shell access, we did want to know whether we would get a reply, indicating the connection is working.