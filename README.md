# Node deploy image with Yarn, PM2 and other hooks


### Supported tags and respective Dockerfile links


#### Docker pull:

```
$ docker pull lanvige/node-deploy:6.9.5-onbuild
```


#### 版本：

- LTS: 6.10.0 [(LTS/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/lts/Dockerfile)
- LTS: 6.10.0-onbuild [(LTS/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/lts/onbuild/Dockerfile)
- Current: 7.7.2 [(Current/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/current/Dockerfile)
- Current: 7.7.2-onbuild [(Current/onbuild/Dockerfile)](https://github.com/lanvige/docker-node-deploy/blob/master/current/onbuild/Dockerfile)


### 介绍

本镜像是为 node (Yarn & PM2) 发布准备的基础包，包含了必要的前置全局需求：

- yarn@0.21.3
- pm2@2.4.0


#### onbuild 版本

onbuild 版本中包含了项目中的一些配置和约定，项目的约定目录，默认端口等：

- NODE_ENV
- WORKDIR: /app/
- COPY package.json yarn.lock
- COPY . /app
- EXPOSE 80 443
- CMD ["pm2-docker", "process.yml"]



### 如何使用

#### 使用前提：

application 目录中需要包含以下几个文件:

- pageckage.json
- yarn.lock
- process.yml (PM2 启动配置文件)
- Dockerfile


下面是真实项目的一个示例：

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


#### Application - Dockerfile：

```
FROM lanvige/node-deploy:7.6.0-onbuild
```


### Application - Build docker image

指定 NODE_ENV，然后设置 Image 的版本。

```
$ docker build --build-arg NODE_ENV=production -t="youimagename:latest" .
```


### Application - RUN

```
$ sudo docker run --name nodedeploytest youimagename:latest
```


### Docker exec
```
$ sudo docker exec -it nodebasetest /sh
```
