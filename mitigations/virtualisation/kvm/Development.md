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

* If not have SSH yet, [install SSH and learn about its options](../ssh.md).
* If not have [github account](https://github.com/) or [gitlab account](https://about.gitlab.com/), get one.

Make a key pair:

    $ ssh-keygen -f ~/github-key-ed25519 -t ed25519 -C "[name]@example.com" 

Start the `ssh-agent` in the background:

    $ eval "$(ssh-agent -s)"

Check to see if `~/.ssh/config` exists:

    $ ls ~/.ssh/

If not create it and move the keys in.

Edit config file:

    $ sudo vi ~/.ssh/config

Add:

    Host *
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ~/.ssh/github-key-ed25519

Add SSH private key to the ssh-agent:

    $ ssh-add -k ~/.ssh/github-key-ed25519

Copy the public key (the contents of the newly-created github-key-rsa.pub file) into clipboard.

    $ sudo apt-get update
    $ sudo apt-get install xclip

    $ xclip -selection clipboard < ~/.ssh/github-key-ed25519.pub

Add public key (content of clipboard) to github:
* Go to your github or gitlab //Account Settings//
* Click //SSH and GPG Keys// on the left.
* Click green //New SSH Key// on the right.
* Add a label (like “Development VM on Thinkpad”) and paste the public key into the big text box.

### Test

Check github connection:

    $ ssh -T git@github.com
    Hi [name]! You've successfully authenticated, but Github does
not provide shell access.

If instead, you get `Permission denied`, it is [time for troubleshooting](https://docs.github.com/en/github/authenticating-to-github/troubleshooting-ssh/error-permission-denied-publickey).

