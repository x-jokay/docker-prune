# Docker prune

Docker image for Docker [prune](https://docs.docker.com/config/pruning).

## Information

| Service                                             | Stats |
|-----------------------------------------------------|-------|
| [GitHub](https://github.com/x-jokay/docker-prune)   | ![Last commit](https://img.shields.io/github/last-commit/x-jokay/docker-prune.svg?style=flat-square) ![Issues](https://img.shields.io/github/issues-raw/x-jokay/docker-prune.svg?style=flat-square) ![PR](https://img.shields.io/github/issues-pr-raw/x-jokay/docker-prune.svg?style=flat-square) |
| [Docker Hub](https://hub.docker.com/r/xjokay/prune) | ![Pulls](https://img.shields.io/docker/pulls/xjokay/prune.svg?style=flat-square) ![Stars](https://img.shields.io/docker/stars/xjokay/prune.svg?style=flat-square) |

## Usage

```sh
docker pull docker.io/xjokay/prune:latest
```

### Supported tags

| Tag    | Description         | Size                                                                                                  |
|--------|---------------------|-------------------------------------------------------------------------------------------------------|
| latest | Latest `main` build | ![Size](https://shields.beevelop.com/docker/image/image-size/xjokay/prune/latest.svg?style=flat-square) |

### Exposed Ports

None

### Volumes

| Directory            | Description                                               |
|----------------------|-----------------------------------------------------------|
| /var/run/docker.sock | Needs to be mounted in order to be able to prune objects. |

### Configuration

| ENV field | Req. / Opt.  | Description                                                |
|-----------|--------------|------------------------------------------------------------|
| INTERVAL  | *Optional*   | Interval of pruning, default is `86400` seconds.           |
| OBJECTS   | *Optional*   | Objects to be pruned, default is `container volume image`. |

## Samples

### docker-compose

```yaml
version: '3.8'

services:
  app:
    image: docker.io/xjokay/prune:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      - INTERVAL=86400
      - "OBJECTS=container volume image"
    restart: always
```

### docker run

```sh
docker run -d \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e INTERVAL=86400 \
  -e "OBJECTS=container volume image" \
  docker.io/xjokay/prune:latest
```