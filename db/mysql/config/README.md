### MySQL 配置

> 目录
* [配置文件](#配置文件)
    * [Windows](#windows)
    * [Linux](#linux)
    * [MacOS](#macos)

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
































