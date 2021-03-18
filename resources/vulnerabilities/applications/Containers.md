# Containers

## Assumptions

* Components in the toolchain and the stack, if vulnerable, can open the door:
  * Host OS and kernel
  * Docker and/or any other tool involved in building the container
  * Control points of the cluster
  * Anything else inside a container image that is vulnerable

Code vulnerabilities inside containers can also open the door to the host and the cluster. Particularly when combined with other vulnerabilities like running with root privileges.

## Mitigations

* As much security by design as possible (before deployment)
* Monitor applications in runtime
* We need to look up what scanners exist
