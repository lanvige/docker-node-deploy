#
# Node Base Dockerfile
#
# VERSION LTS

FROM node:6.10.0

MAINTAINER Lanvige Jiang <lanvige@gmail.com>


# onbuild with nodeenv
ONBUILD ARG NODE_ENV
ONBUILD ENV NODE_ENV $NODE_ENV

# Set workdir
WORKDIR /app/

# install global npm libs
RUN yarn global add pm2@2.4.2
# install npm libs
ONBUILD COPY package.json yarn.lock /app/
ONBUILD RUN $HOME/.yarn/bin/yarn install --production && $HOME/.yarn/bin/yarn cache clean

# Copy project to $container/app
ONBUILD COPY . /app
# ONBUILD COPY process.yml /app/process.yml

EXPOSE 80 443

#ENTRYPOINT ["pm2", "start", "--no-daemon", "/app/bin/api"]
# CMD []
CMD ["pm2-docker", "/app/process.yml"]
