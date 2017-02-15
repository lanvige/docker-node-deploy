# Node Deploy (onbuild) - LTS


## Build

```
$ docker build -t="node-deploy:6.9.5-onbuild" .
```



## TAG: 多起一个名字 (LTS)：

### Docker HUB

```
$ docker tag node-deploy:6.9.5-onbuild lanvige/node-deploy:6.9.5-onbuild
```

### hjidc

```
$ docker tag node-deploy:6.9.5-onbuild dockerhub.hjidc.com/hjstudy/node-deploy:6.9.5-onbuild
```



## Push to registry

### Docker HUB

```
$ docker push lanvige/node-deploy:6.9.5-onbuild
```

### hjicd

```
$ docker push dockerhub.hjidc.com/hjstudy/node-deploy:6.9.5-onbuild
```





