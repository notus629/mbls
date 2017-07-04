### PHP 运行配置

> 目录
* 



#### 基础

* 在哪里进行设置 [[参考](http://php.net/manual/en/configuration.changes.modes.php)]
    * `ini_set()`
    * `php.ini`
    * `http.conf`

模式 | 含义
--- | ---
*PHP_INI_USER* | 可以在用户脚本中定义(使用`ini_set()` 或 Windows 注册表), 可以在 `.user.ini` 中定义
*PHP_INI_PERDIR* | 可以在 `php.ini`, `.htaccess`, `.user.ini` 中定义
`PHP_INI_SYSTEM` | 可以在 `php.ini` 或 `httpd.conf` 中定义
`PHP_INI_ALL`  | 可以在任意地方定义