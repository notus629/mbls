### 配置

> 目录
* [配置文件](#配置文件)
    * [Windows](#windows)
    * [Linux](#linux)
    * [MacOS](#macos)
* [用户权限](#用户权限)



#### 配置文件

##### Windows

* MySQL 配置文件名称 `my.ini`
    
* 配置文件路径 (Windows, AppServ)
> mysql/my.ini


##### Linux 

* 通常为 
> /etc/mysql/my.cnf

* 举例 (Ubuntu 16.04, MySQL 5.7.18)

    1. 配置文件 `/etc/mysql/my.cnf` 和 `/etc/mysql/mysql.cnf`(两文件内容相同)，其中又引入另外两个目录中的配置文件
        ```
        !includedir /etc/mysql/conf.d/
        !includedir /etc/mysql/mysql.conf.d/
        ```
    1. `conf.d` 中包含 `/etc/mysql/conf.d/mysql.cnf`. 即 MySQL 客户端配置文件。
    
    1. `mysql.conf.d` 中包含 `/etc/mysql/mysql.conf.d/mysqld.cnf`. 即 MySQL 服务器端配置文件。
    
##### MacOS

待完善。

### 用户权限
* MySQL 5.7.18 安装后, 默认有 4 个数据库
```
> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

* 用户的相关信息在 mysql 数据库的 user 表中. 

    查看 root 用户信息, 修改 root 使之能从其它机器访问数据库。
```
> use mysql;
> select host,user from user where user = 'root';
+-----------+------+
| host      | user |
+-----------+------+
| localhost | root |
+-----------+------+
> update user set host='%' where user = 'root'; 
```

* 使用 `grant` 命令修改 root 权限，使之能从任意地址访问
```
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```
    

































