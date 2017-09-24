# docker-sdcc

This repository contains all that's necessary for building and testing TG9541/STM8EF (SDCC@R9933 and Python2.7 are used).

To build it run:
```
docker build -t docker-sdcc .
```

To publish it run:
```
docker tag docker-sdcc <DockerId>/docker-sdcc
docker push <DockerId>/docker-sdcc
```

The following builds the W1209 binary, runs it in uCsim, compiles the code in W1209/board.fs, and dumps the Flash memory to out/W1209/W1209-forth.ihx:
```
docker run -ti -v `pwd`:/home docker-sdcc /bin/sh -c "cd /home && make BOARD=W1209 forth"
```

