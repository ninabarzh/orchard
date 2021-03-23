# Docker cheatsheet

## Installation
(This was on debian)

- [Install docker](https://docs.docker.com/engine/install/) (I installed manually so I can airgap)
- [Install docker-compose](https://docs.docker.com/compose/install/)
- Create an account on Docker Hub if you wish to create your own images and push them to Docker Hub (for collaboration with others)
- Do NOT try to install Kitematic, it [checks for the setuid sandbox binary on desktop Linux](https://bugs.chromium.org/p/chromium/issues/detail?id=598454) and it builds but with errors: command "/opt/kitematic/node_modules/electron-prebuilt/dist/electron build" (target "electron") exited with code 1. From the grunt-electron-installer-debian. 

The docker CLI is good enough. I'll race through the tutorials, get a container working with the code repository we wish to test and make a general docker cheatsheet while doing so. 

## Removing shit
First off, how to get stuff that doesn't work out of your system:

Stop a container before removing it:

    $ docker container stop kitematic
    $ docker rm kitematic

    $ docker images -a
    REPOSITORY                   TAG              IMAGE ID       CREATED       SIZE
    python                       latest           01185d917daf   3 days ago    403MB
    nginx                        latest           6084105296a9   11 days ago   133MB
    node                         14.16.0-alpine   90f281698f7a   11 days ago   116MB
    alpine                       latest           28f6e2705743   4 weeks ago   5.61MB
    jonadev95/kitematic-docker   latest           d79f1525b301   5 years ago   1e+03MB

    $ docker rmi d79f1525b301
    Error response from daemon: conflict: unable to delete d79f1525b301 (cannot be forced) - image is being used by running container e8bf66523f09
    $ docker container stop e8bf66523f09
    e8bf66523f09
    $ docker rm e8bf66523f09
    e8bf66523f09
    $ docker rmi d79f1525b301
    Untagged: jonadev95/kitematic-docker:latest
    Untagged: jonadev95/kitematic-docker@sha256:50c98babd542d7d899e8c688033725f3246035146f102cfbb388a8c0eba7cb23
    Deleted: sha256:d79f1525b301346f679b65385deb9c339ca7219f8db728004a654ce0af1db53d
    Deleted: sha256:9595ffc4024636e1c779ab6abf26f0173b51af09329ec3bc213b1c9fbf7748ec
    Deleted: sha256:844b9b1f66b5e1549e2f5f5714e027983e3824628b9d1acbfc75294973ab7e2c
    Deleted: sha256:bbf570226b366ade8c682596faf497b1fe7e0a972edc22aead500d38f1fbd1af
    Deleted: sha256:fd6b16cc0bb0af0f312442e12e0afdfc6471a905f015034172ce6d34439478ff
    Deleted: sha256:961f6854e56aafbceac62ff3c0badd3611f60487fe8c8cbe4d7e573ace9ecdd7
    Deleted: sha256:2112dd8096d62f931fb10afa894b6392ca8cee8af5968fbd5e5486eab795d70b
    Deleted: sha256:b94664be7c9f581d537a9c6113e4b16a4011cd3a08e2e726e9fbbca8aec960c6
    Deleted: sha256:111be99eea03d49c161d309831a26ff571b57bd801643ee7687a899dc55819c2
    Deleted: sha256:b9554b92dfbf60719dcd1a6da318b61c835dec432e947af8bd9fd0ce93b58417
    Deleted: sha256:dd197bd973fb25ea701ed33998f762b7f7ec6502cf0c45d2e77188d9691222ef
    Deleted: sha256:960e743ac3cd2d5ecca836e5fa0b9e59d00ed40859452eedfb9276f7f22f8b98
    Deleted: sha256:c04cf3f9451a0515f3b5857c0a664ef4a24f0d9153a5a436bcad4b98a07753a9
    Deleted: sha256:7acb3ff1c616c0a3c11a0b5e5758887f093d9621b4dae1f80b3954aa618a501a
    Deleted: sha256:3f0a4928b0513a4bc9843e93585afe7df4bef127d5a790533a1fd91f0249bfc1
    Deleted: sha256:2f4586a9a755ac2f6aaa80f0307f76cc9cfb81ccf743c69733b7e401c54692dc
    Deleted: sha256:c0e6d28f31733ccf61e5cec5c8d393c96e5928bdd7e66ab40180c1a9181be570
    $ 

Cleaning up:

    $ docker system prune (all stopped containers, all networks not used by at least one container, all dangling images, all dangling build cache)


