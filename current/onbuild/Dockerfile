#
# Node Base Dockerfile
#
# VERSION Current

FROM node:7.6.0

MAINTAINER Lanvige Jiang <lanvige@gmail.com>

# Install yarn@0.20.3 & pm2@2.4.0
RUN curl -o- -L https://yarnpkg.com/install.sh | bash
RUN $HOME/.yarn/bin/yarn config set registry https://registry.npm.taobao.org
RUN $HOME/.yarn/bin/yarn global add pm2@2.4.0

# onbuild with nodeenv
ONBUILD ARG NODE_ENV
ONBUILD ENV NODE_ENV $NODE_ENV

# Set workdir
WORKDIR /app/

# install npm libs
ONBUILD COPY package.json yarn.lock /app/
ONBUILD RUN $HOME/.yarn/bin/yarn install --production && $HOME/.yarn/bin/yarn cache clean

# Copy project to $container/app
ONBUILD COPY . /app
# ONBUILD COPY process.yml /app/process.yml

EXPOSE 80 443

#ENTRYPOINT ["pm2", "start", "--no-daemon", "/app/bin/api"]
# CMD []
CMD ["pm2-docker", "process.yml"]
