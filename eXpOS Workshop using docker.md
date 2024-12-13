
1. make a directory for the project

`mdkir eXpOS`

4. create these items on your directory

````
cd eXpOS
touch Dockerfile
mkdir workdir
````

3. Add these to the Dockerfile

```
FROM ubuntu:20.04

RUN apt-get update \
    && apt-get install -y bison flex libreadline-dev libc6-dev libfl-dev wget vim make gcc curl unzip build-essential

RUN useradd -m expos
USER expos

RUN cd /home/expos \
    && curl -sSf https://raw.githubusercontent.com/eXpOSNitc/expos-bootstrap/main/download.sh | sh \
    && cd /home/expos/myexpos \
    && make

WORKDIR /home/expos/myexpos
```

4. Build the project

```
docker build -t expos:ubuntu20.04 .
```

5. We'll start an instance of Container and map the local folder `workdir` into `/home/expos/workdir` directory of container.

```
docker run -v $PWD/workdir:/home/expos/myexpos/workdir -d --name expos -i expos:ubuntu20.04 
```

6. connecting to the container

```
docker start expos # if the container instance is not already running

docker exec -it expos /bin/bash # to get a bash shell inside the container
```
