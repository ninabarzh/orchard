# Docker cheatsheet

(This was on debian)

- [Install docker](https://docs.docker.com/engine/install/) (I installed manually so I can airgap)
- [Install docker-compose](https://docs.docker.com/compose/install/)
- Create an account on Docker Hub if you wish to create your own images and push them to Docker Hub (for collaboration with others)
- Do NOT try to install Kitematic, it [checks for the setuid sanbox binary on desktop Linux](https://bugs.chromium.org/p/chromium/issues/detail?id=598454) and it builds but with errors: command "/opt/kitematic/node_modules/electron-prebuilt/dist/electron build" (target "electron") exited with code 1. That's ancient. 

The CLI is good enough. I'll race through the tutorials, get it working with the code repository we wish to test and make a general cheatsheet.
