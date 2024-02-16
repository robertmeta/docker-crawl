# docker-crawl

[![Build Status](https://cloud.drone.io/api/badges/robertmeta/docker-crawl/status.svg?ref=refs/heads/main)](https://cloud.drone.io/robertmeta/docker-crawl)

Docker container for Dungeon Crawl Stone Soup (DCSS).

Docker Hub: [https://hub.docker.com/r/robertmeta/crawl](https://hub.docker.com/r/robertmeta/crawl)

## How to Build

```
git clone git@github.com:robertmeta/docker-crawl.git
cd docker-crawl
docker build .
```

To build a Webtiles server build explicitly:
```
docker build -f Dockerfile.webtiles .
```

To build a Tiles server build explicitly:
```
docker build -f Dockerfile.tiles .
```

# How to Use this Image

## Quickstart

The following will run the latest Webtiles crawl server.

```
docker run -d --rm -p 8080:8080 --name=crawl_webtiles robertmeta/crawl:latest
```

## Persistent Deployment

All player RCs and webserver database files are located within `/data` within the container. Bind mount a host directory to this location to maintain persistence.

```
docker run \
  -d \
  --rm \
  -v /data/:/data \
  -p 8080:8080 \
  --name=crawl_webtiles \
  robertmeta/crawl:latest
```
