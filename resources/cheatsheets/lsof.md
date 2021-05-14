# lsof 

`lsof` is a command meaning "list open files", which is used in many Unix-like systems to report a list of all open files and the processes that opened them. This open source utility was developed and supported by Victor A. Abell, the retired Associate Director of the Purdue University Computing Center. It works in and supports several Unix flavors.

Open files in the system include disk files, named pipes, network sockets and devices opened by all processes. One use for this command is when a disk cannot be unmounted because (unspecified) files are in use. The listing of open files can be consulted (suitably filtered if necessary) to identify the process that is using the files.

## Usage

Show all connections:

    $ sudo lsof -i

Get only IPv6 traffic:

    $ sudo lsof -i 6

Get only IPv4 traffic:

    $ sudo lsof -i 4

Show only TCP connections (provide the protocol right after the -i):

    $ sudo lsof -iTCP

Show networking related to a given port (22 in this case):

    $ sudo lsof -i :22

Show connections to a specific host:

    $ sudo lsof -i@XXX.XXX.XXX.XXX

Show connections based on host and port (22 in this case):

    $ lsof -i@XXX.XXX.XXX.XXX:22

