### bgcms

>目录
* [项目说明](#项目说明)
* [需求分析](#需求分析)
    * [功能分析](#功能分析)
    * [表的设计](#表的设计)
        * [后台用户表](#后台用户表)
* [功能模块](#功能模块)
    * [登录模块](#登录模块)

#### 项目说明
* 开发一个简单的具备前后台管理的 cms 系统。
* 后端采用 ThinkPHP 3.2 框架。
* 前端使用 Bootstrap, jQuery 和 layer 等开源库。

#### 需求分析
1. 功能分析
1. 表的设计

##### 功能分析
* 后台主要功能
    * **登录**（login/logout, 采用异步的弹出层消息提示)
    * **菜单管理**(管理后台的栏目菜单、前台导航菜单、菜单项的排序、操作(删除等)、CURD)
    * **文章管理**(CURD、排序、缩略图(异步上传)、编辑器插件、更改文章状态、操作(编辑、删除、预览)、推荐(到推荐位))
    * **推荐位管理**(CURD、排序、更改状态)
    * **用户管理**(CURD、用户信息查看、编辑)
    * **基本管理**(如网站 Title、Keywords、自动备份、自动生成缓存, 采用静态缓存(即文件，不入DB); 缓存配置--手动生成静态 html 页面)


* 前台页面
    * 由系统自动生成
    * 主要包含三个页面：首页、栏目页、详情页
    * 首页包含: 导航条、推荐位(含阅读数)、部分文章列表、文章排行、广告位等
    * 静态页: 如何展示动态的阅读数？采用 Ajax    


##### 表的设计
* **后台用户表**: 用于 login 及用户管理
* **菜单表**: 菜单管理，type: 前/后台菜单类型
* **文章主表**: 文章添加者(username)、count(文章计数器）
* **文章副表**: 文章内容表。若放入主表，内容多，在查询时会影响主表的性能。包含：文章内容、文章主表 ID 等。
* **推荐位标识表**
* **推荐位内容表**

 
###### 后台用户表
 
`ENGINE=MyISAM AUTO_INCREMENT=9 DEFAULT CHARSET=utf8`
 
字段|类型|含义
---|---|---
id | `SMALLINT UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT` | 用户 ID, 主键
username | `varchar(20) NOT NULL DEFAULT '' ` | 用户名,索引
realname | `varchar(50) NOT NULL DEFAULT '' ` | 真实姓名
email | `varchar(40) DEFAULT '' ` | 
password | `varchar(32) NOT NULL DEFAULT '' ` | 
status | `tinyint NOT NULL DEFAULT '1' ` | 是否是有效状态？
isadmin | `bool DEFAULT '1'` | 是否为管理员帐户 
lastloginip | `varchar(15) DEFAULT '0' ` | 最近一次登录 IP 
lastlogintime | `int UNSIGNED DEFAULT '0' ` | 最近一次登录时间 


#### 功能模块

##### 登录模块
* 主要用于处理用户登录、登出    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    