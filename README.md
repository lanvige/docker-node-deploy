# Node deploy image with Yarn, PM2 and other hooks

一个已安装 yarn@0.23.1, pm2@2.4.2 公共库和打包顺序，启动脚本的 Node.js 基本镜像。

#### Docker pull:

```
$ docker pull lanvige/node-deploy:6.9.5-onbuild
```


#### 版本：

- LTS: 6.10.0 [(LTS/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/lts/Dockerfile)
- LTS: 6.10.0-onbuild [(LTS/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/lts/onbuild/Dockerfile)
- Current: 7.7.3 [(Current/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/current/Dockerfile)
- Current: 7.7.3-onbuild [(Current/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/current/onbuild/Dockerfile)


### 介绍

本镜像是为 node (Yarn & PM2) 发布准备的基础包，包含了必要的前置全局需求：

- yarn@0.21.3
- pm2@2.4.2


#### onbuild 版本

onbuild 版本中包含了项目中的一些配置和约定，项目的约定目录，默认端口等：

- NODE_ENV
- WORKDIR: /app/
- COPY package.json yarn.lock
- COPY . /app
- EXPOSE 80 443
- CMD ["pm2-docker", "start", "production", "/app/process.yml"]



### 如何使用

这里有一个 boilerplate 项目，里面使用到了本 docker image。

- https://github.com/lanvige/koa2-boilerplate


#### 使用前提：

项目的目录结构：

```
.
├── app
├── bin
├── config
├── docker-compose.yml
├── lib
├── Dockerfile
├── package.json
├── process.yml
└── yarn.lock
```


必须包含以下几个文件:

- pageckage.json
- yarn.lock
- process.yml (PM2 启动配置文件)
- Dockerfile
- docker-compose.yml


Dockerfile 就很简单了，只要简单的引用一下 onbuild 的 image 就可以了。


#### 启动

```
$ docker-compose up -d --build
```

这样，就可以通过 docker ps 来查看已启动的项目了。