# 8.9.4 (2018/02/07)

升级 node 到 8.9.4

- node@8.9.4
- yarn@1.3.2
- pm2@2.9.2


# 8.2.0 (2017/07/20)

升级 node 到 8.2.0。

- node@8.2.0
- yarn@0.27.5
- pm2@2.5.0


# 8.0.0 & 6.10.3

测试了对 entrypoing 的支持，升级 yarn 到 v0.24.6，升级 pm2 到 2.4.6

在 Docker build 时，去掉 NODE_ENV 的支持，将该配置转移到了 pm2-docker 中。这样，就可以通过 cmd 来进行替换。

```
CMD ["start", "--env", "production", "/app/process.yml"]
```


参见：
- https://hub.docker.com/r/keymetrics/pm2-docker-alpine/~/dockerfile/
- http://pm2.keymetrics.io/docs/usage/application-declaration/
- http://pm2.keymetrics.io/docs/usage/docker-pm2-nodejs/


# 8.0.0  (2017/06/01)

终于等来了 8.0


# 7.8.0b (2017/04/07)

加入 entrypoint 的支持，目的是限制容器的使用场景，只能启动 pm2-docker，但对于 该命令的参数，可以通过重新设置 cmd 进行修改。


# 7.8.0a (2017/04/06)

团队达成一致，不同的环境里，用的是不同的镜像和不同的容器。这样，env 就不再需要了，而是直接用 NODE_ENV 配置，这个配置在 Dockerfile 中已配置好。

同时更新了 pm2-docker 的启动脚本，移除 auto-exit 和 env 配置。


# 0.1.0 (2017/02/08)

#### Features

- **A: Init Project**
- **B:**

#### Bugs Fixed

- **C:**
