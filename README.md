# sample-docker-compose
This is a sample of Docker Compose for building docker images

To install docker correctly, 

1. Follow instructions in this [link](https://docs.docker.com/engine/install/ubuntu/)
2. Run the following commands: 

```shell
$  sudo usermod -a -G docker $USER
$  sudo systemctl enable docker.service
$  sudo systemctl start docker.service
$  sudo chmod 666 /var/run/docker.sock
```



3. To build using docker compose (optional)

```shell
docker-compose up --build

```

expected result

```shell
ubuntu@dennymachine:~/sample-docker-compose$ docker-compose up --build
Creating network "sample-docker-compose_default" with the default driver
Building myapp
Step 1/4 : FROM python:3.8.5-alpine
3.8.5-alpine: Pulling from library/python
b538f80385f9: Pull complete
0d489d24c263: Pull complete
f4da3152e180: Pull complete
be87d3f602c9: Pull complete
08cc941d381a: Pull complete
Digest: sha256:cbc08bfc4b1b732076742f52852ede090e960ab7470d0a60ee4f964cfa7c710a
Status: Downloaded newer image for python:3.8.5-alpine
 ---> da3ea875dbcd
Step 2/4 : COPY . /app
 ---> d5de4ab866a7
Step 3/4 : WORKDIR /app
 ---> Running in ade1a52cd5a2
Removing intermediate container ade1a52cd5a2
 ---> 302363674cef
Step 4/4 : RUN python3 -m venv /opt/venv
 ---> Running in 97a5d154dd1b
Removing intermediate container 97a5d154dd1b
 ---> db72cebab174

Successfully built db72cebab174
Successfully tagged rockmypost_python:latest
Creating sample-docker-compose_myapp_1 ... done
```

4. To prune all images (optional)

```shell
docker system prune -a
```

expected result

```shell
ubuntu@dennymachine:~/sample-docker-compose$ docker system prune -a
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all images without at least one container associated to them
  - all build cache

Are you sure you want to continue? [y/N] y
Deleted Containers:
a7f0ff587c9a4b7e4fbd4bf6ce15d64760ee0d0517d1a4bf0b59f2be34010603

Deleted Networks:
sample-docker-compose_default

Deleted Images:
untagged: python:3.8.5-alpine
untagged: python@sha256:cbc08bfc4b1b732076742f52852ede090e960ab7470d0a60ee4f964cfa7c710a
untagged: rockmypost_python:latest
deleted: sha256:db72cebab174f887dda84a13a36d9bbf9745429935a15e970793474886557199
deleted: sha256:0161a02f226a4fa4cd75cbfb91d77420cbd7e95f3ff983367ca2e0e5300f2b4c
deleted: sha256:302363674cef84e231528184b2dfee45a5317ff4ea7dcd11c70ad5c8bf27abcf
deleted: sha256:d5de4ab866a75841e847e893f435ec789d6fb1fb234605789d01e926cb173364
deleted: sha256:2b539152fe1a31bfee62df6e647d77df28b6ddc133ff381b987f29d2d79fb143
deleted: sha256:da3ea875dbcd7946429309384b748f7478c26bb2449d91311711e3beca3d4660
deleted: sha256:6f7fcc5a51555cc0f97571210516806b188bea7216391b27e40b8d2e5de1827d
deleted: sha256:86cebdd341ea3e1e884c1837246e4fe783edf9e5e7faa0668863106ed183ded3
deleted: sha256:1329df254db86815829b646a7423d9df2748140f3e6a3c6a604be89c29812b71
deleted: sha256:9c4b19948f0f89933bf02552f7e55a65d98f937d53509282e20e06cf52d126e4
deleted: sha256:e2f13739ad415e6f8d9f73253910e4984563a1ec98bd0e0af715fc2c74dfe84b

Total reclaimed space: 55.61MB
```