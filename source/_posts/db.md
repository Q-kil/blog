---
title: db
date: 2024-01-31 16:50:54
categories:
- db
tags:
- db
---

# Mongo
## docker
docker run -d -p 27017:27017 --name mongodb mongo:latest


# Mysql
## docker
docker run --name mysql -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 -d mysql:latest

## 删除
系统偏好设置面板中可以看到之前安装的MySQL，此时若想卸载MySQL