### 专题

> 目录
* [修改用户权限](#修改用户权限)

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
