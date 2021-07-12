# Communication

## Thunderbird

```
$ sudo apt-get install thunderbird
```

## Keybase

```
    $ curl --remote-name https://prerelease.keybase.io/keybase_amd64.deb
    $ Verify with https://book.keybase.io/docs/server/our-code-signing-key
    $ sudo apt install ./keybase_amd64.deb
    $ run_keybase
```

## Signal

```
$ sudo apt-get install curl
$ curl -s -x 127.0.0.1:8082 https://updates.signal.org/desktop/apt/keys.asc | sudo apt-key add -
$ echo "deb [arch=amd64] https://updates.signal.org/desktop/apt buster main" | sudo tee -a /etc/apt/sources.list.d/signal-buster.list
$ sudo apt update && sudo apt install signal-desktop
```

## Discord

Go to the [download page of Discord](https://discord.com/download) and download the `deb` file (only available for 64-bit systems) and install