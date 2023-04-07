# soju docker image

[![Build](https://github.com/fourstepper/docker-soju/actions/workflows/build.yml/badge.svg)](https://github.com/fourstepper/docker-soju/actions/workflows/build.yml)

soju is an IRC bouncer - https://git.sr.ht/~emersion/soju
Repo is a fork of https://github.com/fourstepper/docker-soju

## Supported soju versions
v0.5.2


## Usage

### Environment variables

**USER** - the admin (main) user

**PASSWORD** - the password for the admin user

**LISTEN_METHOD**, **LISTEN_HOST**, **LISTEN_PORT**

- Check the possible listen directives in the [docs](https://git.sr.ht/~emersion/soju/tree/master/item/doc/soju.1.scd)

### Running the image

**Run the image from the CLI**

`docker run  -e USER='admin' -e PASSWORD='password' -e LISTEN_METHOD='irc+insecure' -e LISTEN_HOST='0.0.0.0' -e LISTEN_PORT='6667' -p 6667:6667 omdv/docker-soju`


**Run as part of docker-compose**

```
version: "3.0"
services:
  soju:
    image: fourstepper/docker-soju:latest
    container_name: soju
    restart: unless-stopped
    volumes:
      - ./soju-data:/data
    ports:
      - "6667:6667"
    environment:
      - USER=admin
      - PASSWORD=password
      - LISTEN_METHOD=irc+insecure
      - LISTEN_HOST=0.0.0.0
      - LISTEN_PORT=6667
      - LOG_PATH=/data/irc.log
```
