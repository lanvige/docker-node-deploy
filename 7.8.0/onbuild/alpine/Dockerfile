#
# Node Base Dockerfile
#
# VERSION Current-alpine (yarn included)

FROM node:7.8.0-alpine

MAINTAINER Lanvige Jiang <lanvige@gmail.com>


# onbuild with nodeenv
ONBUILD ARG NODE_ENV
ONBUILD ENV NODE_ENV $NODE_ENV

# Set workdir
WORKDIR /app/

# install global npm libs
RUN yarn global add pm2@2.4.4
# install npm libs
ONBUILD COPY package.json yarn.lock /app/
ONBUILD RUN yarn install --production && yarn cache clean

# Copy project to $container/app
ONBUILD COPY . /app
# ONBUILD COPY process.yml /app/process.yml

EXPOSE 80 443


# Start process.yml
ENTRYPOINT ["pm2-docker"]
CMD ["start", "/app/process.yml"]
