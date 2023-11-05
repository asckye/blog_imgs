## 一、介绍
EPLAN默认使用的数据库是ACCESS，但是当你的部件库日渐壮大时，在查找、编辑等操作时，将会变得非常卡顿，所以这时候是考虑改用SQL部件库的时候了！

使用SQL不仅可安装在本地（个人用），还可以运行到云端或局域网服务器（多人用）
本次使用的是用服务器搭建的SQL Sever

## 二、服务器
本次使用的服务器是：腾讯的轻量应用服务器
CPU：2核
内存：4G
存储：90G
系统：Docker CE

## 三、部署

#### 1. 拉取镜像
```bash
docker pull mcr.microsoft.com/mssql/server:2022-latest
```

#### 2. 运行容器
```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=ChenDaDliu2023"   -p 1433:1433 --name sql1 --hostname sqlServer  -d   mcr.microsoft.com/mssql/server:2022-latest
```
|参数|说明|
|:--|:--|
|-e "ACCEPT_EULA=Y"|将 ACCEPT_EULA 变量设置为任意值，以确认接受最终用户许可协议。 SQL Server 映像>的必需设置。|
|-e "MSSQL_SA_PASSWORD=<YourStrong@Passw0rd>"|指定至少包含 8 个字符且符合密码策略的强密码。 SQL Server 映像的必需设置。|
|-e "MSSQL_COLLATION=<SQL_Server_collation>"|指定自定义 SQL Server 排序规则，而不使用默认值 SQL_Latin1_General_CP1_CI_AS。|
|-p 1433:1433|将主机环境中的 TCP 端口（第一个值）映射到容器中的 TCP 端口（第二个值）。 在此示例中，SQL Server 侦听容器中的 TCP 1433，此容器端口随后会对主机上的 TCP 端口 1433 公开。|
|--name sql1|为容器指定一个自定义名称，而不是使用随机生成的名称。 如果运行多个容器，则无法重复使用相同的名称。|
|--hostname sql1|用于显式设置容器主机名。 如果未指定主机名，则主机名默认为容器 ID，这是随机生成的系统 GUID。|
|-d|| 在后台运行容器（守护程序）。|
|mcr.microsoft.com/mssql/server:2022-latest|SQL Server Linux 容器映像。|

>> 如果Docker容器启动报WARNING: IPv4 forwarding is disabled. Networking will not work
>> 解决方法
>> 打开sysctl配置文件
>> ```bash
>> vim /etc/sysctl.conf
>> ```
>> 添加如下代码
>> ```bash
>> net.ipv4.ip_forward=1 
>> ```
>> 重启network服务
>> ```bash
>> systemctl restart network  
>> ```
>> 查看是否修改成功
>> ```bash
>> sysctl net.ipv4.ip_forward  
>> ```



#### 3. 查看运行的容器
```bash
docker ps -a
```
运行成功应该会看到与下面类似的输出：
```out
CONTAINER ID   IMAGE                                        COMMAND                    CREATED         STATUS         PORTS                                       NAMES
d4a1999ef83e   mcr.microsoft.com/mssql/server:2022-latest   "/opt/mssql/bin/perm..."   2 minutes ago   Up 2 minutes   0.0.0.0:1433->1433/tcp, :::1433->1433/tcp   sql1
```

#### 4.如果运行不成功，通过以下命令查看docker容器内错误日志
```bash
docker exec -t sql1 cat /var/opt/mssql/log/errorlog | grep connection
```

#### 5. 删除容器
```bash
docker stop sql1
docker rm sql1
```
