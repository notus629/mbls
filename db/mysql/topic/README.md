### 专题

> 目录
* [修改用户权限](#修改用户权限)
* [连接远程 mysql 服务器](连接远程-mysql-服务器)

#### 修改用户权限

* MySQL 5.7.18 安装后, 默认有 4 个数据库。用户的相关信息在 mysql 数据库的 user 表中.

```
> show databases;
+--------------------+
| Database |
+--------------------+
| information_schema |
| mysql |
| performance_schema |
| sys |
+--------------------+
```

* 查看 root 用户信息，修改 root 权限，使之能从任意主机访问。
```
> use mysql;
> select host,user from user where user = 'root';
+-----------+------+
| host | user |
+-----------+------+
| localhost | root |
+-----------+------+
> update user set host='%' where user = 'root';
```

* 或，使用 `grant` 命令修改 root 权限，使之能从任意地址访问
```
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```

####连接远程 MySQL 服务器

默认安装的 MySQL 服务，根用户 root 只能从本机连接，且 MySQL 只监听本机地址(bind-address=127.0.0.1)

需要修改两处（对于 Vagrant 虚拟机，还要第三步）

1. 打开 MySQL 配置文件，修改为 `bind-address=0.0.0.0`，即监听所有地址。

2. 修改 root 用户的权限（若采用 root 用户来远程连接），使之能从任意主机连接。(利用 MySQL 自带客户端连接，选择 mysql 数据库。
```
update user set host='%' where user = 'root';
```














