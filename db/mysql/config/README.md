### 配置

> 目录
* [配置文件](#配置文件)
    *[Windows](#windows)
    *[Linux](#linux)
    *[MacOS](#macos)


#### 配置文件

##### Windows

* MySQL 配置文件名称 `my.ini`
    
* 配置文件路径 (Windows, AppServ)
> mysql/my.ini


##### Linux 

* 通常为 
> /etc/mysql/my.cnf

* 举例 (Ubuntu 16.04, MySQL 5.7.18)
    1. 配置文件 `/etc/mysql/my.cnf`，其中又引入另外两个配置文件

    ```
    !includedir /etc/mysql/conf.d/
    !includedir /etc/mysql/mysql.conf.d/
    ```
    2. 
    
#### MacOS




    

































