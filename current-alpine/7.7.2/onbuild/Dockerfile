#
# Node Base Dockerfile
#
# VERSION Current-alpine (yarn included)

FROM node:7.7.2-alpine

MAINTAINER Lanvige Jiang <lanvige@gmail.com>


# onbuild with nodeenv
ONBUILD ARG NODE_ENV
ONBUILD ENV NODE_ENV $NODE_ENV

# Set workdir
WORKDIR /app/

# install global npm libs
RUN yarn global add pm2@2.4.0
# install npm libs
ONBUILD COPY package.json yarn.lock /app/
ONBUILD RUN yarn install --production && yarn cache clean

# Copy project to $container/app
ONBUILD COPY . /app
# ONBUILD COPY process.yml /app/process.yml

EXPOSE 80 443

#ENTRYPOINT ["pm2", "start", "--no-daemon", "/app/bin/api"]
# CMD []
CMD ["pm2-docker", "process.yml"]
