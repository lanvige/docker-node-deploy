# Node Deploy with Yarn, pm2 and onbuild hooks

Node 项目对基础镜像的定制：

- https://hub.docker.com/_/node/



## What's Inside

- yarn

```
$HOME/.yarn/bin/yarn
```

- pm2@2.4.0



## Node Deploy (onbuild) - Current


### Build

```
$ docker build -t="node-deploy:8.0.0-alpine-onbuild" .
```



### TAG: 多起一个名字 (LTS)：

#### Docker HUB

```
$ docker tag node-deploy:7.10.0-alpine-onbuild lanvige/node-deploy:8.0.0-alpine-onbuild
```



### Push to registry

#### Docker HUB

```
$ docker push lanvige/node-deploy:8.0.0-alpine-onbuild
```



## Node Deploy - LTS


### Build

```
$ docker build -t="node-deploy:8.0.0" .
```



### TAG: 多起一个名字 (LTS)：

#### Docker HUB

```
$ docker tag node-deploy:8.0.0 lanvige/node-deploy:8.0.0
```



### Push as you like


#### Docker HUB

```
$ docker push lanvige/node-deploy:8.0.0
```


