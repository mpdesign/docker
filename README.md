# docker-mp

docker-mp 是一个用 Docker 搭建的本地 PHP 应用开发与运行环境。

## 准备

安装 Docker for Windows 或 Docker for Mac。

## 服务

* db：使用 mariadb 作为应用的数据库
* php：解释 php 脚本，使用 php-fpm
* web：使用 NGINX 作为应用的 web 服务器
* redis：内存服务器

## 结构

* web：这个目录存储web应用，www 放应用的代码。
* services： 环境里定义的服务需要的一些资源，比如 nginx 的配置文件在 nginx/config/default.conf 。
* docker-compose-web.yml：定义本地开发环境需要的服务。
* docker-compose.yml：生产环境需要的服务，暂时为空白。
* .env：环境文件 。

## 使用

准备：

下载并安装docker客户端

```
https://www.docker.com/
```

获取阿里云加速器，并配置

```
https://{id}.mirror.aliyuncs.com
```

获取docker-mp

```
git clone https://github.com/mpdesign/docker-mp.git
cd docker
```

创建Dockfile镜像：

* mp-nginx

```
docker build -t mp-nginx:1.0 ./services/nginx/ 
```

* mp-php

```
docker build -t mp-php:1.0 ./services/php/ 
```

* mysql

```
docker build -t mp-mysql:1.0 ./services/mysql/
```

* redis

```
docker build -t mp-redis:1.0 ./services/redis/ 
```

创建docker-compose.yml

基本用法：

* 创建容器并启动，找不到镜像则远程拉取镜像

```
docker-compose up -d
```

