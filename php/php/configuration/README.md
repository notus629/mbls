### PHP 运行配置

> 目录
* [基础](#基础)
    * [php.ini 主要搜索位置](#phpini-主要搜索位置-参考)
    * [配置 ini 文件的扫描目录](#配置-ini-文件的扫描目录)
        * [查看 PHP 扫描的 ini 文件](#查看-php-扫描的-ini-文件)
    * [在哪里进行配置](#在哪里进行配置-参考)
* [基本配置项](#基本配置项)



#### 基础

##### php.ini 主要搜索位置 [[参考](http://php.net/manual/en/configuration.file.php)]

* SAPI 模块指定的位置(如 Apache 2 的 `PHPIniDir` 指令，CGI 和 CLI 的 `-c` 命令行选项)。

* `PHPRC` 环境变量

* 当前工作目录（对于 CLI ??)

* Web 服务器目录 (对于 SAPI 模块), 或 PHP 所在目录 (对于 Windows ??)

> * 若存在 `php-SAPI.ini` 文件 (其中 SAPI 指使用的 SAPI 名字 -- 可用 `php_sapi_name()` 来获取, 如 php-cli.ini 或 php-apache.ini)，会被用来代替 `php.ini`

##### 配置 ini 文件的扫描目录

在读取 `php.ini` 之后，可以配置 PHP 去目录中扫描 `.ini` 文件

* 编译时使用 `--with-config-file-scan-dir` 选项
* 运行时配置 `PHP_INI_SCAN_DIR` 环境变量 (会覆盖编译选项)
    * 其中的目录由各平台相关的目录分隔符指定（`PATH_SEPARATOR`）
    * 其中若包含一个空目录 (blank directory)，则也会扫描编译时选项中指定的目录 

###### 查看 PHP 扫描的 ini 文件
查看 PHP 扫描了哪些 PHP 文件，及扫描的顺序
    * `php_ini_scanned_files()`
    * 或命令行使用 `--ini` 选项运行 php


##### 在哪里进行配置 [[参考](http://php.net/manual/en/configuration.changes.modes.php)]
    * `ini_set()`
    * `php.ini`
    * `http.conf`

模式 | 含义
--- | ---
*PHP_INI_USER* | 可以在用户脚本中定义(使用`ini_set()` 或 Windows 注册表), 可以在 `.user.ini` 中定义
*PHP_INI_PERDIR* | 可以在 `php.ini`, `.htaccess`, `.user.ini` 中定义
*PHP_INI_SYSTEM* | 可以在 `php.ini` 或 `httpd.conf` 中定义
*PHP_INI_ALL*  | 可以在任意地方定义

#### 基本配置项











