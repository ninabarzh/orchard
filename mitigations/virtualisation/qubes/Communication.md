# Communication (The plan)

Signal, Keybase and Thunderbird (separated)

Based on
* https://www.qubes-os.org
* https://signal.org/
* https://keybase.io/

Versions

    Qubes-OS 4.0.4

Guides

* https://www.qubes-os.org/doc/software-update-dom0/
* https://www.qubes-os.org/doc/installing-contributed-packages/
* https://github.com/Qubes-Community/Contents/blob/master/docs/privacy/signal.md
    
## Thunderbird

- [ ] Install thunderbird

    $ sudo apt-get install thunderbird
    
## Template VM for messaging

- [ ] Create Debian 10 Template VM in dom0

    $ sudo qubes-dom0-update qubes-template-debian-10
    $ qvm-run -a debian-10 gnome-terminal

## Signal

- [ ] Install signal

    $ sudo apt-get install curl
    $ curl -s -x 127.0.0.1:8082 https://updates.signal.org/desktop/apt/keys.asc | sudo apt-key add -
    $ echo "deb [arch=amd64] https://updates.signal.org/desktop/apt buster main" | sudo tee -a /etc/apt/sources.list.d/signal-buster.list
    $ sudo apt update && sudo apt install signal-desktop

## Keybase

- [ ] Install keybase

    $ curl --remote-name https://prerelease.keybase.io/keybase_amd64.deb
    $ Verify with https://book.keybase.io/docs/server/our-code-signing-key
    $ sudo apt install ./keybase_amd64.deb
    $ run_keybase

