# How to Setup a Ghost Blog using Docker on Windows and DigitalOcean Spaces

This example shows how to set up a Ghost Blog to run locally in a Docker container on Windows 10 with a local mounted folder for text content and a Digital Ocean Space connected for images and other media content. The purpose of this is to create JAMStack pages with Gatsby.js

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Docker Desktop has to be already installed and docker-compose must be able to run.

```
docker run hello-world
```

### Installing

A **secrets.env** file has to be created at the same level as **docker-compose.yml** and it should contain the following (replace with your domain, secret keys and DO-region):

```
storage__active=digitalocean
AWS_ACCESS_KEY_ID=[your Spaces access ID key created in DO|manage|API]
AWS_SECRET_ACCESS_KEY=[your secret Spaces access keys]
AWS_DEFAULT_REGION=ams1
GHOST_STORAGE_ADAPTER_S3_PATH_BUCKET=content-yourdomain-org
GHOST_STORAGE_ADAPTER_S3_ASSET_HOST=https://content.yourdomain.org
GHOST_STORAGE_ADAPTER_S3_PATH_PREFIX=images
GHOST_STORAGE_ADAPTER_S3_ENDPOINT=ams1.digitaloceanspaces.com
GHOST_STORAGE_ADAPTER_S3_ACL=public-read
```

The line in docker-compose.yml should be replaced with a folder in your own, local Users catalog. This is where your blog will be persisted when the Ghost instance are down for reboot or service.
```
- c:/Users/Kent/backtus/blog:/var/lib/ghost/content
```

Ghost 3.2 will be built and started with
```
docker-compose up
```

After the first build, it can be rebuilt with
```
docker-compose up --build
```

## Acknowledgments

* Thanks to [Devguides](https://www.devguides.dev/how-to-setup-a-ghost-blog-with-docker/) for the idea!
