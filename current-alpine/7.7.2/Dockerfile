#
# Node Base Dockerfile
#
# VERSION Current

FROM node:7.7.2-alpine

MAINTAINER Lanvige Jiang <lanvige@gmail.com>

# Install yarn@0.21.3 & pm2@2.4.0
ENV YARN_VERSION 0.21.3
ADD https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v${YARN_VERSION}.tar.gz /opt/yarn.tar.gz
RUN yarnDirectory=/opt/yarn && \
    mkdir -p "$yarnDirectory" && \
    tar -xzf /opt/yarn.tar.gz -C "$yarnDirectory" && \
    ln -s "$yarnDirectory/dist/bin/yarn" /usr/local/bin/ && \
    rm /opt/yarn.tar.gz

RUN yarn global add pm2@2.4.0