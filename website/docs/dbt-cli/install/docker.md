---
title: "Docker"
---

Since v0.16.0, the bundled distribution of dbt (including the four most popular adapter plugins) is published as an image on [DockerHub](https://hub.docker.com/r/fishtownanalytics/dbt).

To pull the latest version of the standard dbt image:
```shell
docker pull fishtownanalytics/dbt
```
To pull a specific version:
```shell
docker pull fishtownanalytics/dbt:0.19.1
```

You can view the [Dockerfile](https://github.com/fishtown-analytics/dbt/blob/develop/docker/Dockerfile) used to build `fishtownanalytics/dbt` images.
