### PHP 运行配置

> 目录
* [基础](#基础)



#### 基础

##### php.ini 主要搜索位置

* SAPI 模块指定的位置(如 Apache 2 的 `PHPIniDir` 指令，CGI 和 CLI 的 `-c` 命令行选项)。

* `PHPRC` 环境变量

* 当前工作目录（对于 CLI ??)

* Web 服务器目录 (对于 SAPI 模块), 或 PHP 所在目录 (对于 Windows)


##### 在哪里进行配置 [[参考](http://php.net/manual/en/configuration.changes.modes.php)]
    * `ini_set()`
    * `php.ini`
    * `http.conf`

模式 | 含义
--- | ---
*PHP_INI_USER* | 可以在用户脚本中定义(使用`ini_set()` 或 Windows 注册表), 可以在 `.user.ini` 中定义
*PHP_INI_PERDIR* | 可以在 `php.ini`, `.htaccess`, `.user.ini` 中定义
`PHP_INI_SYSTEM` | 可以在 `php.ini` 或 `httpd.conf` 中定义
`PHP_INI_ALL`  | 可以在任意地方定义