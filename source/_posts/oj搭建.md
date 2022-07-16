---
title: oj搭建
date: 2022-07-15 16:09:02
tags:
---

`su`进入root用户在root下进行操作

# oj搭建

```bash
sudo apt-get update && sudo apt-get install -y vim python3-pip curl git
pip3 install --upgrade pip
pip install docker-compose
```



# 安装desker

```bash
sudo curl -sSL https://get.daocloud.io/docker | sh
```



# 开始安装

```zsh
git clone -b 2.0 https://github.com/QingdaoU/OnlineJudgeDeploy.git && cd OnlineJudgeDeploy
```

***<u>可能会在克隆上一直卡住</u>***    是因为我们**连接不上**github，所以我么需要对云服务器进行git<u>**优化**</u>

如果不卡在上一步不需要执行下边这一步

```bash
cd /etc/
echo "199.232.69.194 github.global.ssl.fastly.net" >> hosts
echo "140.82.112.3 github.com" >> hosts
```



#  启动服务

```bash
docker-compose up -d
```

根据网速情况，大约5到30分钟就可以自动搭建完成，全程无需人工干预。

等命令执行完成，然后运行 `docker ps -a`

当看到所有的容器的状态没有 `unhealthy` 或 `Exited (x) xxx` 就代表 OJ 已经启动成功。

# 完成安装

完成安装后记得ctrl + d 退出root账户进入普通账户

通过浏览器访问服务器的 HTTP 80 端口或者 HTTPS 443 端口，就可以开始使用了。后台管理路径为`/admin`, 安装过程中自动添加的超级管理员用户名为 `root`，密码为 `rootroot`， **请务必及时修改密码**。

注意在云服务中的防火墙中把端口打开