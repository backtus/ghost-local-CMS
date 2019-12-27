FROM ghost:3.2
WORKDIR /var/lib/ghost
RUN npm install ghost-storage-adapter-s3
RUN cp -vr ./node_modules/ghost-storage-adapter-s3 ./current/core/server/adapters/storage/digitalocean