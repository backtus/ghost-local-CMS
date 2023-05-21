# How to Setup a Ghost Blog using Docker on Windows and DigitalOcean Spaces

This example shows how to set up a Ghost Blog to run locally in a Docker container on Windows 10 with a MariaDB for text content and a Digital Ocean Space connected for images and other media content. The purpose of this is to create JAMStack pages with Gatsby.js

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Docker Desktop has to be already installed and docker-compose must be able to run.

```
docker run hello-world
```

### Installing

A **secrets.env** file has to be created at the same level as **docker-compose.yml** (or even better in your container-orchestrator like Portainer) and it should contain the following (replace with your domain, secret keys and DO-region):

```
AWS_ACCESS_KEY_ID=[your Spaces access ID key created in DO|manage|API]
AWS_SECRET_ACCESS_KEY=[your secret Spaces access keys]
AWS_REGION=ams1
AWS_BUCKET=content-yourdomain-org
AWS_ASSET_HOST=https://content.yourdomain.org
AWS_PATH_PREFIX=images
AWS_FORCE_PATH_STYLE=true
AWS_ENDPOINT=ams1.digitaloceanspaces.com
AWS_ACL=public-read
MYSQL_USER=ghost-dev-user
MYSQL_PASSWORD=ghost-dev-pass
MYSQL_DATABASE=ghost-dev-db
GHOST_URL=http://your.ip.adr.ess:8043
GHOST_PORT=8043
ADMINER_PORT=8044
```

Ghost (currently 5.40) will be built and started with
```
docker-compose up
```

After the first build, it can be rebuilt with
```
docker-compose up --build
```

## Acknowledgments

* Thanks to [Devguides](https://www.devguides.dev/how-to-setup-a-ghost-blog-with-docker/) for the idea!
