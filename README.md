# Node deploy image with Yarn, PM2 and other hooks

一个已安装 yarn, pm2 公共库和打包顺序，启动脚本的 Node.js 基本镜像。


#### Docker pull:

```
$ docker pull lanvige/node-deploy:10.13.0-alpine-onbuild
```


### 版本：

#### LTS Latest 版本：

- LTS: 10.13.0-onbuild [(onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/10.13.0/onbuild/Dockerfile)
- LTS: 10.13.0-alpine-onbuild [(alpine/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/10.13.0/onbuild/alpine/Dockerfile)



#### LTS PRE:

- LTS: 8.12.0-onbuild [(onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/8.12.0/onbuild/Dockerfile)
- LTS: 8.12.0-alpine-onbuild [(alpine/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/8.12.0/onbuild/alpine/Dockerfile)


#### Current

Current 版本为 v11，暂时没做基础镜像。


## 介绍

本镜像是为 node (Yarn & PM2) 发布准备的基础包，包含了必要的前置全局需求：

- pm2@3.2.2 <https://github.com/Unitech/pm2>
- yarn@1.2.2 <https://yarnpkg.com/>



#### onbuild 版本

onbuild 版本中包含了项目中的一些配置和约定，项目的约定目录，默认端口等：

- NODE_ENV
- WORKDIR: /app/
- COPY package.json yarn.lock
- COPY . /app
- EXPOSE 80 443
- CMD ["pm2-docker", "start", "production", "/app/process.yml"]



## 如何使用

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




## 版本命名规则

该 deploy 包以 node 的版本为基础，如 `8.5.0`。但如果在同一个版本中，如果出现 pm2 的大版本升级，或其它配置的升级。会在 node 的版本号后面加上小写的 a-z，来标识版本的升级，如 `8.2.0a`
