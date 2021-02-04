[<img src="https://hotio.dev/img/jackett.png" alt="logo" height="130" width="130">](https://github.com/Jackett/Jackett)

[![GitHub Source](https://img.shields.io/badge/github-source-ffb64c?style=flat-square&logo=github&logoColor=white&labelColor=757575)](https://github.com/hotio/jackett)
[![GitHub Registry](https://img.shields.io/badge/github-registry-ffb64c?style=flat-square&logo=github&logoColor=white&labelColor=757575)](https://github.com/orgs/hotio/packages/container/package/jackett)
[![Docker Pulls](https://img.shields.io/docker/pulls/hotio/jackett?color=ffb64c&style=flat-square&label=pulls&logo=docker&logoColor=white&labelColor=757575)](https://hub.docker.com/r/hotio/jackett)
[![Discord](https://img.shields.io/discord/610068305893523457?style=flat-square&color=ffb64c&label=discord&logo=discord&logoColor=white&labelColor=757575)](https://hotio.dev/discord)
[![Upstream](https://img.shields.io/badge/upstream-project-ffb64c?style=flat-square&labelColor=757575)](https://github.com/Jackett/Jackett)
[![Website](https://img.shields.io/badge/website-hotio.dev-ffb64c?style=flat-square&labelColor=757575)](https://hotio.dev/containers/jackett)

## Starting the container

CLI:

```shell
docker run --rm \
    --name jackett \
    -p 9117:9117 \
    -e PUID=1000 \
    -e PGID=1000 \
    -e UMASK=002 \
    -e TZ="Etc/UTC" \
    -e ARGS="" \
    -v /<host_folder_config>:/config \
    hotio/jackett
```

Compose:

```yaml
version: "3.7"

services:
  jackett:
    container_name: jackett
    image: hotio/jackett
    ports:
      - "9117:9117"
    environment:
      - PUID=1000
      - PGID=1000
      - UMASK=002
      - TZ=Etc/UTC
      - ARGS
    volumes:
      - /<host_folder_config>:/config
```

## Tags

| Tag                | Upstream            | Version | Build |
| -------------------|---------------------|---------|-------|
| `release` (latest) | GitHub releases     | ![version](https://img.shields.io/badge/dynamic/json?color=f5f5f5&style=flat-square&label=&query=%24.version&url=https%3A%2F%2Fraw.githubusercontent.com%2Fhotio%2Fjackett%2Frelease%2FVERSION.json) | ![build](https://img.shields.io/github/workflow/status/hotio/jackett/build/release?style=flat-square&label=) |
| `testing`          | GitHub pre-releases | ![version](https://img.shields.io/badge/dynamic/json?color=f5f5f5&style=flat-square&label=&query=%24.version&url=https%3A%2F%2Fraw.githubusercontent.com%2Fhotio%2Fjackett%2Ftesting%2FVERSION.json) | ![build](https://img.shields.io/github/workflow/status/hotio/jackett/build/testing?style=flat-square&label=) |

You can also find tags that reference a commit or version number.

## Configuration location

Your jackett configuration inside the container is stored in `/config/app`, to migrate from another container, you'd probably have to move your files from `/config` to `/config/app`.
