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

```
git clone https://github.com/mpdesign/docker.git
cd docker
```

创建Dockfile镜像：

* nginx

```
docker pull nginx:1.12.2 
```

* php-fpm

```
docker pull php:7.1.11-fpm
```

* php-yaf

```
docker build -t php-yaf ./services/php/
```

* mysql

```
docker pull mariadb:10.1
```

* redis

```
docker pull redis:3.2.1
```

创建docker-compose.yml

基本用法：

* 创建容器并启动，找不到镜像则远程拉取镜像

```
docker-compose up -d
```

* 进入容器修改php和nginx配置

```
docker-compose exec 容器名 bash
```

* 重启

```
docker-compose restart 容器名
```
