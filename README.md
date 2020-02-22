# jackett

<img src="https://raw.githubusercontent.com/hotio/unraid-templates/master/hotio/img/jackett.png" alt="Logo" height="130" width="130">

[![GitHub](https://img.shields.io/badge/source-github-lightgrey)](https://github.com/hotio/docker-jackett)
[![Docker Pulls](https://img.shields.io/docker/pulls/hotio/jackett)](https://hub.docker.com/r/hotio/jackett)
[![Discord](https://img.shields.io/discord/610068305893523457?color=738ad6&label=discord&logo=discord&logoColor=white)](https://discord.gg/3SnkuKp)
[![Upstream](https://img.shields.io/badge/upstream-project-yellow)](https://github.com/Jackett/Jackett)

## Starting the container

Just the basics to get the container running:

```shell
docker run --rm --name jackett -p 9117:9117 -v /<host_folder_config>:/config hotio/jackett
```

The environment variables below are all optional, the values you see are the defaults.

```shell
-e PUID=1000
-e PGID=1000
-e UMASK=002
-e TZ="Etc/UTC"
-e ARGS=""
-e DEBUG="no"
```

## Tags

| Tag      | Description                    | Build Status                                                                                                                                              | Last Updated                                                                                                                                                        |
| ---------|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| latest   | The same as `stable`           |                                                                                                                                                           |                                                                                                                                                                     |
| stable   | Stable version                 | [![Build Status](https://cloud.drone.io/api/badges/hotio/docker-jackett/status.svg?ref=refs/heads/stable)](https://cloud.drone.io/hotio/docker-jackett)   | [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/hotio/docker-jackett/stable)](https://github.com/hotio/docker-jackett/commits/stable)     |
| unstable | Unstable version, pre-releases | [![Build Status](https://cloud.drone.io/api/badges/hotio/docker-jackett/status.svg?ref=refs/heads/unstable)](https://cloud.drone.io/hotio/docker-jackett) | [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/hotio/docker-jackett/unstable)](https://github.com/hotio/docker-jackett/commits/unstable) |

You can also find tags that reference a commit or version number.

## Configuration location

Your jackett configuration inside the container is stored in `/config/app`, to migrate from another container, you'd probably have to move your files from `/config` to `/config/app`.

## Executing your own scripts

If you have a need to do additional stuff when the container starts or stops, you can mount your script with `-v /docker/host/my-script.sh:/etc/cont-init.d/99-my-script` to execute your script on container start or `-v /docker/host/my-script.sh:/etc/cont-finish.d/99-my-script` to execute it when the container stops. An example script can be seen below.

```shell
#!/usr/bin/with-contenv bash

echo "Hello, this is me, your script."
```

## Troubleshooting a problem

By default all output is redirected to `/dev/null`, so you won't see anything from the application when using `docker logs`. Most applications write everything to a log file too. If you do want to see this output with `docker logs`, you can use `-e DEBUG="yes"` to enable this.
