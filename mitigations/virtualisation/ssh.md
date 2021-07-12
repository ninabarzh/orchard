# SSH

There are two ways to login onto a remote system over SSH – using password authentication or public key authentication (passwordless SSH login). To enable passwordless access, create a SSH key pair and upload a copy of the public key to the remote server.

## Choosing algorithm and key size

When generating keys the algorithm is chosen using the `-t` option and key size using the `-b` option. 

`SSH` supports several public key algorithms for authentication keys:
* `rsa` is an old algorithm (based on the difficulty of factoring large numbers). A key size of 4096 bits is recommended, but choosing a different algorithm may be better. It is quite possible the RSA algorithm will become practically breakable in the near future. Advantage of `rsa` is that all SSH clients support this algorithm.
* `dsa` is an old US government Digital Signature Algorithm (based on the difficulty of computing discrete logarithms). DSA is not recommended.
* `ecdsa` is the Digital Signature Algorithm standarized by the US government, using elliptic curves. A decent algorithm for current applications (if one is not avoiding elliptic curve) with three key sizes: 256, 384, and 521 bits. If using it, choose 521 bits. Most SSH clients support this algorithm.
* `ed25519` is a new algorithm added in OpenSSH. Support for it in clients is not yet universal. Use in general purpose applications may not yet be advisable but where it can be used, it is highly recommended to use it.

## Preparations

If not have yet, install `ssh` on the local machine (from repository).

    $ sudo apt install openssh-client

Else, if have, check for existing SSH keys:

    $ ls -al ~/.ssh/id_*.pub

In case you already do have keys, you can either 
* use the existing keys
* back them up and create a new pair
* if not in use anywhere overwrite
* generate an additional key pair with different names

The first three are obvious and it is recommended to use different keys for each connection.

## Generating key pairs

Standard:

    $ ssh-keygen -t ed25519 -C "[name]@example.com" 

or

    $ ssh-keygen -t rsa -b 4096 -C "[name]@example.com"

* Enter the location where you want to store the keys or hit Enter to accept the default path.
* It also asks you to set a passphrase, making the connection even more secure, but is an eternal hassle, and it may interrupt when setting up automated processes. Type in a passphrase or just press Enter to skip this step.
* The output responds where it stored the identification and public key and gives the key fingerprint.

## Generating multiple key pairs

Normally, the tool prompts for the filename in which to store the key. And this can also be specified on the command line using the `-f [filename]` option.

    $ ssh-keygen -f ~/ut7-key-ed25519 -t ed25519 -C "[name]@example.com" 

## Verification

Verify with:

    $ ls -al ~/.ssh/*.pub