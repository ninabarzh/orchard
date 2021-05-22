# Development VM

- [Development VM](#development-vm)
  - [Git](#git)
  - [Github SSH](#github-ssh)
  - [First connect](#first-connect)
  - [Install IDE's](#install-ides)
    - [VSCode](#vscode)
    - [PyCharm Community](#pycharm-community)
  - [Clone repositories](#clone-repositories)

## Git

Download and install git (easy from repository):

    $ sudo apt install git

Check with:

    $ git --version

Set up git with user name and email. If you have set your email to private in github and it is the only repository you use for all repositories, you can set it globally: 

    $ git config --global user.email "{ID}+{username}@users.noreply.github.com"

    $ git config --global user.name "{username}"

If also using other repository hosts, set it in a repository

    $ git config user.email "{ID}+{username}@users.noreply.github.com"

    $ git config --global user.name "{username}"

If this is a change of name and/or email address, reset the author information on the last commit with:

    $ git commit --amend --reset-author

## Github SSH

* If not have SSH yet, [install SSH and learn about its options](../ssh.md).
* If not have [github account](https://github.com/) or [gitlab account](https://about.gitlab.com/), get one.

Make a key pair (Use "{ID}+{username}@users.noreply.github.com" for "[name]@example.com" if you have set a private email address in github:

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
        IgnoreUnknown UseKeychain
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

## First connect

Check github connection:

    $ ssh -T git@github.com
    
    The authenticity of host 'github.com (xxx.xxx.xxx.xxx)' can't be established.
    RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
    Are you sure you want to continue connecting (yes/no)? yes
    Warning: Permanently added 'github.com,xxx.xxx.xxx.xxx' (RSA) to the list of known hosts.
    Hi [name]! You've successfully authenticated, but GitHub does not provide shell access.

If instead, you get `Permission denied` or other error messages, it is [time for troubleshooting](https://docs.github.com/en/github/authenticating-to-github/troubleshooting-ssh/error-permission-denied-publickey).

## Install IDE's

I use glorified editors, if only for the coloured code. For JavaScript I use VSCode, for Python I use pyCharm (community version).

### VSCode

    $ sudo apt install software-properties-common apt-transport-https

Get and enable the repository:

    $ wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
    $ sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
    $ sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'

Install code:

    $ sudo apt update
    $ sudo apt install code

In VSCode, install the [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) extension and authenticate.

### PyCharm Community

Installation using the [Toolbox App](https://www.jetbrains.com/help/pycharm/installation-guide.html#toolbox) is the easiest.

## Clone repositories

    $ git clone git@github.com:[name]/[repo-name]

And get everything to work again.