#
# Node Base Dockerfile
#
# VERSION Current

FROM node:7.6.0

MAINTAINER Lanvige Jiang <lanvige@gmail.com>

# Install yarn@0.21.3 & pm2@2.4.0
RUN curl -o- -L https://yarnpkg.com/install.sh | bash -s -- --version 0.21.3
RUN $HOME/.yarn/bin/yarn global add pm2@2.4.0
RUN $HOME/.yarn/bin/yarn config set registry https://registry.npm.taobao.org
