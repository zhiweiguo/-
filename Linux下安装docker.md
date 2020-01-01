win10中Linux子系统安装docker记录

## win10中开启Linux子系统功能

1. 控制面板 -> 程序和功能 -> 启用或关闭windows功能 -> 勾选适用于Linux的windows子系统（需要重启）
2. Microsoft store中搜索Ubuntu，选择不带版本号的那个安装

## Ubuntu中安装docker步骤

1. 卸载旧版本的docker（不是必须，主要为了防止之前安装过docker，第一次安装可忽略）

   sudo apt-get remove docker docker-engine docker-ce docker.io

2. 更新apt包

   sudo apt-get update

3. 安装以下包，使apt可以通过https使用存储库（repository）

   sudo apt-get install apt-transport-https ca-certificates  curl   software-properties-common

4. 添加docker官方GPG秘钥

   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

5. 安装稳定存储库

   sudo add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs)  stable"

6. 再次更新apt包索引

   sudo apt-get update

7. 查询当前系统稳定可使用的docker-ce版本

   apt-cache madison docker-ce

9. 安装指定版本的docker-ce

   apt-get install docker-ce=18.06.0~ce~3-0~ubuntu

10. 启动docker服务

    service docker start

11. 验证docker

    docker --version    # 查看docker版本

## docker基本使用

1. 拉取镜像

   docker pull 镜像名         

   如：docker pull tensorflow/tensorflow:1.13.2-py3

2. 启动容器

   docker run 镜像名

   如：docker run -it -u root  tensorflow/tensorflow:1.13.2-py3 /bin/bash

   命令详细解释可参考菜鸟教程：https://www.runoob.com/docker/docker-run-command.html

3. 进入容器

   docker exec -it -u root tensorflow/tensorflow:1.13.2-py3 /bin/bash

   

## 常见问题

1. docker: Error response from daemon: OCI runtime create failed: container_linux.go:345: starting container process caused "process_linux.go:297: getting the final child's pid from pipe caused \"EOF\"": unknown.
   ERRO[0103] error waiting for container: context canceled

   原因：

   可能是由于在WSL的环境下，WSL目前应该属于WSL1，这并不是真正的Linux（大部分发行版带的东西，可能WSL不带，还要systemctl命令也不能用），大概到年底能发布的WSL2才是真正的把Linux内核整合到WIndows10中。目前看到的问题大部分都是WSL + Ubuntu + docker 18.x
   解决：

   卸载当前版本的docker： apt-get autoremove docker-ce

   重装适配的docker-ce版本



## 修改docker默认存储位置

参考链接：https://www.cnblogs.com/flying607/p/9283003.html

