# Node Deploy (onbuild) - Current


## Build

```
$ docker build -t="node-deploy:7.5.0-onbuild" .
```



## TAG: 多起一个名字 (LTS)：

### Docker HUB

```
$ docker tag node-deploy:7.5.0-onbuild lanvige/node-deploy:7.5.0-onbuild
```

### hjidc

```
$ docker tag node-deploy:7.5.0-onbuild dockerhub.hjidc.com/hjstudy/node-deploy:7.5.0-onbuild
```



## Push to registry

### Docker HUB

```
$ docker push lanvige/node-deploy:7.5.0-onbuild
```

### hjicd

```
$ docker push dockerhub.hjidc.com/hjstudy/node-deploy:7.5.0-onbuild
```


