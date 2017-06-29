### PHP 基础

> 目录
* [配置项](#配置项)

#### 配置项

##### 数据库配置项

在 * config.php * 中配置

名称 | 解释 | 支持版本
--- | --- |
**DB_DSN** |	DSN：数据源名称。若 DSN 与其它配置方式同时存在，以 DSN 优先。` "DB_DSN" => "mysql://root:pwd@localhost:3306/thinkphp" ` |	 TP3.1
**DB_HOST** | // 设置主机名 `"DB_HOST" => "localhost"` | TP3.1
**DB_NAME** |	// 设置数据库名`"DB_NAME" => "thinkphp"` | TP3.1
**DB_PORT** |	// 数据库的端口号，一般可省 `"DB_PORT" => "3306"` | TP3.1
**DB_PREFIX** | // 表前缀 `"DB_PREFIX" => "tp_"` | TP3.1
**DB_PWD** |	// 数据库的密码 `"DB_PWD" => ""` | TP3.1
**DB_TYPE** |	// 设置数据库类型 `"DB_TYPE" => "mysql"` | TP3.1
**DB_USER** | // 数据库的用户名 `"DB_USER" => "root"` | TP3.1