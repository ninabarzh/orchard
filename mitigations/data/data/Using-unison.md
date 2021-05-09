# Using unison (OSX, Unix, and Windows)

[Unison](http://www.cis.upenn.edu/~bcpierce/unison) (GPL v3) is a file-synchronization tool for OSX, Unix, and Windows. Unison is written in OCaml. It allows two replicas of a collection of files and directories to be stored on different hosts (or different disks on the same host), modified separately, and then brought up to date by propagating the changes in each replica to the other. Unison can run on and synchronize between Windows and many UNIX platforms. Unison requires no root privileges, system access or kernel changes to function. Unison can synchronize changes to files and directories in both directions, on the same machine, or across a network using ssh or a direct socket connection. Transfers are optimised using a version of the rsync protocol, making it ideal for slower links. Unison has a clear and precise specification, and is resilient to failure due to its careful handling of the replicas and its private structures. 

`unison` allows for accessing the same set of files from any computer running (almost) any operating system and keeps these files up-to-date by always maintaining the most recently-modified version of each file during synchronization. The great benefit of using unison to replicate files across different computers (servers) is that your backups are alive.

## Words of warning

It is no longer developed or supported. Setting it up on windows is like jumping through hoops, but when using the github repository to build from source seems doable, according to [Using Unison Across Linux, macOS, and Windows](https://blog.scottlowe.org/2020/06/01/using-unison-across-linux-macos-windows/)

## Linux
### Installing unison 

From repository:

    $ sudo apt-get install unison</code>

### Using unison 

To synchronise two directories on the same machine:

    $ sudo unison [pathtodirectoryname1] [pathtodirectoryname2]

Test connection to remote server:

    $ sudo unison -testServer [pathtodirectoryname1] ssh://server.yourdomain.com/[pathtodirectoryname1]

To sync:

    # unison -batch [pathtodirectoryname1] ssh://server.yourdomain.com/[pathtodirectoryname1]
