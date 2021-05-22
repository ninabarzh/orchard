# Digital forensics

Create an Ubuntu VM and install the sift workstation repository on it per the [Sans sift workstation](https://www.sans.org/tools/sift-workstation) and [sift-cli installation](https://github.com/teamdfir/sift-cli#installation) guides.

Versions

    Ubuntu 20.04
    sift-cli@1.10.0+0-g48a701b
    sift v2021.4.4

[CLI] Update returned exit code not zero after "Running: sift-config" during sift install.

    >> Running: sift-config-tools
    Update returned exit code not zero
    Error: Update returned exit code not zero
        at ChildProcess.<anonymous> (/snapshot/sift-cli/sift-cli.js:542:23)
        at ChildProcess.emit (events.js:315:20)
        at maybeClose (internal/child_process.js:1051:16)
        at Process.ChildProcess._handle.onexit (internal/child_process.js:287:5)

I am now in my 6th attempt, but thanks to [digitalsleuth](https://github.com/digitalsleuth), not giving up yet.

    $ sudo apt-get install python2 git curl -y

    $ sudo curl -o /tmp/get-pip.py https://bootstrap.pypa.io/pip/2.7/get-pip.py

    $ sudo python2 /tmp/get-pip.py

    $ python2 -m pip install git+https://github.com/digitalsleuth/pefile.git

    $ sudo sift install
    
Nope. Still. Giving up. For now. A pull request has been merged which will see this issue fixed in the next release. I'll just hold until then.
