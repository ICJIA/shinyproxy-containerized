# Shinyproxy Containerized

This repository contains a simple production-ready containerized ShinyProxy server for ICJIA.

## Deploy ShinyProxy

> Note: Before deploying ShinyProxy, make sure to have images for all apps are ready and available for ShinyProxy to use.

### Clone this repo

```
git clone icjia/shinyproxy-containerized
```

### Bring up the stack with Docker Compose

```
docker-compose up -d --build
```

## Update individual apps

Updating an existing app is as simple as pulling the up-to-date image from Docker Hub.

For example:

```
docker pull icjia/ucr-index-offense-explorer
```

## Update ShinyProxy

### Try changes on local machine

> Note: First try out the changes on a local machine, push the change to remote repositories, and pull the changes from the production server.
>
> _Do NOT make changes directly on the production server!_

#### Changing configuration

Edit `/shinyproxy/application.yml` to make changes. See [Configuration](https://www.shinyproxy.io/configuration/) on the official documentation to learn more.

#### Changing ShinyProxy version

Edit `Dockerfile` to switch to a different ShinyProxy version.

### Push changes from local to GitHub

```
git push origin master
```

### Pull from production server

```
git pull origin master
```

### Bring up the stack with Docker Compose

> Note: This will incur a short downtime.

```
docker-compose up -d --build shinyproxy
```
