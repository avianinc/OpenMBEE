# OpenMBEE Visual Editor

This Dockerfile is based on the 'Nginx Dockerfile' (See below...). The file downloads and copies the specified visual editor from the OpenMBEE ve release (https://github.com/Open-MBEE/ve/releases).

## Useage:

1. Update the Dockerfile environment variable ```VE_VERSION```
2. Update the nginx.conf file to point to the correct folder for the unzipped ```VE_VERSION```.zip (example: ```/var/www/html/dist```)
3. Build the Dockerfile from the top level ```docker-compose.yaml```

---
## Nginx Dockerfile


This repository contains **Dockerfile** of [Nginx](http://nginx.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [dockerfile/ubuntu](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull dockerfile/nginx`

   (alternatively, you can build an image from Dockerfile: `docker build -t="dockerfile/nginx" github.com/dockerfile/nginx`)


### Usage

    docker run -d -p 80:80 dockerfile/nginx

#### Attach persistent/shared directories

    docker run -d -p 80:80 -v <sites-enabled-dir>:/etc/nginx/conf.d -v <certs-dir>:/etc/nginx/certs -v <log-dir>:/var/log/nginx -v <html-dir>:/var/www/html dockerfile/nginx

After few seconds, open `http://<host>` to see the welcome page.
