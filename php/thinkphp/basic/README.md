
> 目录
* [配置](#配置)
    * [入口文件配置](#入口文件配置)
    * [一般配置](#一般配置)
    * [数据库配置](#数据库配置)

#### 配置

##### 入口文件配置

在入口文件 `index.php` (或其他自定义入口文件)中配置

##### 一般配置

在 `config.php` 或自定义配置文件中配置

配置项 | 说明
--- | ---
**LOAD_EXT_CONFIG** | // 加载扩展配置文件 <br /> `'LOAD_EXT_CONFIG' => 'user,db'` [[参考](https://www.kancloud.cn/manual/thinkphp/1693)]
**URL_CASE_INSENSITIVE** | // URL 地址不区分大小写 <br /> `'URL_CASE_INSENSITIVE' =>true`
**TMPL_PARSE_STRING** | // 更换模板变量规则，修改配置 <br /> `'TMPL_PARSE_STRING'=>array(` <br /> `'__CSS__'=>__ROOT__.'/Public/Css',` <br /> `'__JS__'=>__ROOT__.'/Public/Js')`
**TMPL_L_DELIM** <br /> **TMPL_R_DELIM** | `'TMPL_L_DELIM'=>'{ {'`, <br> `'TMPL_R_DELIM'=>'} }'`


##### 数据库配置

在 `config.php` 中配置, [[参考](https://www.kancloud.cn/manual/thinkphp/1731)]

名称 | 解释
--- | --- |
~~DB_DSN~~ |	DSN：数据源名称。若 DSN 与其它配置方式同时存在，以 DSN 优先。` "DB_DSN" => "mysql://root:pwd@localhost:3306/thinkphp" `. TP 3.2 起 DB_DSN 参数的作用已经改变了，因此默认情况下不再需要设置，直接设置为空字符串即可。[[参考](http://www.thinkphp.cn/topic/26803.html)]
**DB_HOST** | // 设置主机名 `"DB_HOST" => "localhost"`
**DB_NAME** |	// 设置数据库名`"DB_NAME" => "thinkphp"`
**DB_PORT** |	// 数据库的端口号，一般可省 `"DB_PORT" => "3306"`
**DB_PREFIX** | // 表前缀 `"DB_PREFIX" => "tp_"`
**DB_PWD** |	// 数据库的密码 `"DB_PWD" => ""`
**DB_TYPE** |	// 设置数据库类型 `"DB_TYPE" => "mysql"`
**DB_USER** | // 数据库的用户名 `"DB_USER" => "root"`