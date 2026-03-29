# docker-sdcc
[![Build and push Docker image](https://github.com/TG9541/docker-sdcc/actions/workflows/build-push.yml/badge.svg)](https://github.com/TG9541/docker-sdcc/actions/workflows/build-push.yml)

This repository contains all that's needed for building and testing TG9541/STM8EF:

* SDCC 3.9.0 #11195 z180/r2k/r3ka/gbz80/tlcs90/ez80_z80/ds400/hc08/s08/stm8/pdk14/pdk15
* Python 3.6.9
* telnet for debugging STM8 code with uCsim

The corresponding Docker Hub repository is [tg9541/docker-sdcc](https://hub.docker.com/r/tg9541/docker-sdcc/builds/).
The GitHub Container Registry image is [ghcr.io/tg9541/docker-sdcc](https://github.com/TG9541/docker-sdcc/pkgs/container/docker-sdcc).

To build it run:
```
docker build -t docker-sdcc .
```

To publish to Docker Hub:
```
docker tag docker-sdcc <DockerId>/docker-sdcc
docker push <DockerId>/docker-sdcc
```

To publish to GitHub Container Registry:
```
docker tag docker-sdcc ghcr.io/tg9541/docker-sdcc:3.9.0
docker push ghcr.io/tg9541/docker-sdcc:3.9.0
```

The following builds the W1209 binary, runs it in uCsim, compiles the code in W1209/board.fs, and dumps the Flash memory to out/W1209/W1209-forth.ihx:
```
docker run -ti -v `pwd`:/home docker-sdcc /bin/sh -c "cd /home && make BOARD=W1209 forth"
```

If you'd like to see it in action check out the GitHub Action workflows in STM8 eForth.
