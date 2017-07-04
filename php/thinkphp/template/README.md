### TP 模板

> 目录
* [常量](#常量)
* [模板替换](#模板替换)

#### 常量

名称 | 含义
--- | ---
`MODULE_NMAE` | 当前模块名称

#### 模板替换

指令 | 含义
--- | ---
`__ROOT__` |会替换成当前网站的地址（不含域名） , 即 `localhost/thinkphp`
`__APP__` | 会替换成当前项目的URL地址 （不含域名），即 `localhost/thinkphp/index.php`
`__GROUP__` | 会替换成当前分组的URL地址 （不含域名）
`__PUBLIC__` | 会被替换成当前网站的公共目录 通常是 `/Public/`, 即 `localhost/thinkphp/Public`
`__URL__` | 会替换成当前控制器的URL地址（不含域名）, 即`localhost/thinkphp/index.php/Index`
`__ACTION__` | 会替换成当前操作的URL地址 （不含域名）
`__SELF__` | 会替换成当前的页面URL