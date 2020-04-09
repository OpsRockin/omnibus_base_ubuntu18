# omnibus_base_ubuntu18

https://hub.docker.com/r/opsrock/omnibus_base_ubuntu18/

## Omnibus by Docker Bros.

- https://github.com/OpsRockin/omnibus_base_ubuntu18
- https://github.com/OpsRockin/omnibus_base_centos6

### Auto build policies

build via IFTTT.

- gem omnibus master branch updated.
- gem omnibus-software master branch updated.
- cookbook omnibus new version released.


## Usage

First, create empty `Dockerfile` for your omnibus-project.

for `*.deb`, `Dockerfile.ubuntu1804`.

```
FROM opsrock/omnibus_base_ubuntu18
MAINTAINER you
```

for `*.rpm`, `Dockerfile.centos6`.

```
FROM opsrock/omnibus_base_centos6
MAINTAINER you
```

## Build once to execute ONBUILD

```
## DEB
$ docker build -t omnibus_myproject-ubuntu1804 -f Dockerfile.ubuntu1804 .

## RPM
$ docker build -t omnibus_myproject-centos6 -f Dockerfile.centos6 .
```

## Run to create package!

Run with passing your project name via env `OMNIBUS_PROJECT`.

```
## DEB
$ docker run -e OMNIBUS_PROJECT=serverspec -v pkg:/home/omnibus/omnibus-project/pkg omnibus_myproject-ubuntu1804

## RPM
$ docker run -e OMNIBUS_PROJECT=serverspec -v pkg:/home/omnibus/omnibus-project/pkg omnibus_myproject-centos6
```

Packages will be created in `./pkg/` directory.


## Tips

### Recycle build cache

mount cache volume and pass path of cache via env.

`-e BUILD_CACHE_PATH=YOUR_CACHE_PATH`


