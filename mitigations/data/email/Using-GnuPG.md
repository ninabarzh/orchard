# Using GnuPG 

## Linux

### Install the gnupg package from repository.

`$GNUPGHOME` is used by GnuPG to point to the directory where its configuration files are stored. By default `$GNUPGHOME` is not set and `$HOME` is used instead -> a ~/.gnupg directory is placed in home directory during installation. The default configuration files are `~/.gnupg/gpg.conf` and `~/.gnupg/dirmngr.conf`.

### Create key pair

Generate a key pair by typing in a terminal:

```
$ gpg --full-gen-key
gpg (GnuPG) 2.2.5; Copyright (C) 2018 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
    (1) RSA and RSA (default)
    (2) DSA and Elgamal
    (3) DSA (sign only)
    (4) RSA (sign only)
...
```

If you don't know, choose the default (1), RSA (sign only) and a RSA (encrypt only) key, a keysize of the default value (2048), an expiration date of a year (the expiration date can later be extended without having to re-issue a new key) a name and an email address (the name and email address you enter here will be visible to anybody who imports your key), no comment, and finally, a passphrase.

```
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 31B76CAABDBAD2EC marked as ultimately trusted
gpg: directory '/home/nina/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/nina/.gnupg/openpgp-revocs.d/25ABD3A6B8E755E848F27CFB31B76CAABDBAD2EC.rev'
public and secret key created and signed.

pub   rsa2048 2018-03-04 [SC]
        25ABD3A6B8E755E848F27CFB31B76CAABDBAD2EC
uid                      Nina Barzh
sub   rsa2048 2018-03-04 [E]
```

### Export public key

To generate an //ASCII// version of the public key to file `public.key` (to distribute it to friends by e-mail):

```
$ gpg --output public.key --armor --export user-id
```

### Import public key

In order to encrypt messages to others, as well as verify their signatures, their public key is needed. To import a public key with file name `public.key` to your public key ring:

```
$ gpg --import public.key
```

### List keys

To list keys in your public key ring:

```
$ gpg --list-keys
```

To list keys in your secret key ring:

```
$ gpg --list-secret-keys
```

