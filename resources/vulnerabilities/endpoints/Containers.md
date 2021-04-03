# Containers

## Assumptions

* Components in the toolchain and the stack, if vulnerable, can open the door to:
  * Host OS and kernel
  * The docker and/or any other tool involved in building the container
  * Control points of the cluster
  * Anything else inside a container image that is vulnerable

Code vulnerabilities inside containers can also open the door to the host and the cluster. Particularly when combined with other vulnerabilities like running with root privileges. Containers assist in security and make recovery faster, but additional [mitigations](../../../mitigations/application/Containers.md) are required.


