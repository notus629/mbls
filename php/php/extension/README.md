### PHP 扩展

> 目录
* [cURL](#curl)
    * [安装](#安装)
    * [基本步骤](#基本步骤)
    * [curl_setopt](#curl_setopt)
        * [基本示例](# 基本示例)
        * [基本选项参数](#基本选项参数)
        * [POST 选项](#post_选项)
        * [HTTP 请求头](#http_请求头)
        * [Cookie 相关设置](#cookie-相关设置)
    * [参考](#参考)
* [性状](#性状)
    * [创建性状](#创建性状)
    * [使用性状](#使用性状)
    * [参考](#参考)


#### cURL

Client URL Library.

*cURL* 可以使用 URL 的语法模拟浏览器来传输数据，因为它是模拟浏览器，因此它同样支持多种协议，FTP, FTPS, HTTP, HTTPS, GOPHER, TELNET, DICT, FILE 以及 LDAP 等协议都可以很好的支持。

包含：HTTPS 认证，HTTP POST 方法，HTTP PUT 方法，FTP 上传，keyberos 认证，HTTP 上传，代理服务器，cookies，用户名/密码认证，下载文件断点续传，上传文件断点续传，http 代理服务器管道，甚至它还支持 IPv6，scoket5 代理服务器，通过 http 代理服务器上传文件。

PHP supports **libcurl** that allows you to connect and communicate to many different types of servers with many different types of protocols. 

**libcurl** currently supports the http, https, ftp, gopher, telnet, dict, file, and ldap protocols. libcurl also supports HTTPS certificates, HTTP POST, HTTP PUT, FTP uploading (this can also be done with PHP's ftp extension), HTTP form based upload, proxies, cookies, and user+password authentication.


##### 安装

In order to use PHP's cURL functions you need to install the **libcurl** package.

To use PHP's cURL support you must also compile PHP **--with-curl[=DIR]** where DIR is the location of the directory containing the lib and include directories. In the include directory there should be a folder named *curl* which should contain the `easy.h` and `curl.h` files. There should be a file named `libcurl.a` located in the lib directory. 

In order to enable this module on a Windows environment, `libeay32.dll` and `ssleay32.dll` must be present in your PATH. You don't need libcurl.dll from the cURL site.


##### 基本步骤

```php
<?php

 /*用代码完成上述cURL的四步*/
 
// 1. 初始化，创建一个新 cURL 资源 
$ch = curl_init();
 
// 2. 设置 URL 和相应的选项 
curl_setopt($ch, CURLOPT_URL, "http://www.lampbrother.net/"); 
curl_setopt($ch, CURLOPT_HEADER, 0);
 
// 3. 发送请求和接收服务器数据
curl_exec($ch);
 
// 4. 关闭 cURL 资源，并且释放系统资源 
curl_close($ch);
 
?>
```

##### curl_setopt

###### 基本示例
```php
// 设置网页的 URL
// 参数 1： $ch 为 cURL 资源
// 参数 2： CURLOPT_URL，为对应的选项名称
// 参数 3： 选项的对应值
curl_setopt($ch, CURLOPT_URL, "http://www.baidu.com");

```

###### 基本选项参数
* CURL_OPT 
```php
// 设置网页的 URL 地址. 网页 URL 也可以在 
// curl_init("http://www.baidu.com"); 中设置
curl_setopt($curlobj, CURLOPT_URL, "http://www.baidu.com");
```

* CURLOPT_RETURNTRANSFER
```php
// 默认执行后会打印到终端，此选项可将结果保存（不打印输出） 
curl_setopt($curlobj, CURLOPT_RETURNTRANSFER, true); 
$output = curl_exec($curlobj);    // 执行
```

* CURLOPT_HEADER
```php
// 输出中不显示返回的 HTTP 头
curl_setopt($curlobj, CURLOPT_HEADER, 0); 
```

* CURLOPT_FOLLOWLOCATION
```php
// 是否抓取跳转后的页面
curl_setopt($curl, CURLOPT_FOLLOWLOCATION, 1);
```

* CURLOPT_TIMEOUT
```php 
// 下载超时时间，秒为单位
curl_setopt($curlobj, CURLOPT_TIMEOUT, 300);
```

###### POST 选项

* CURLOPT_POST
```php
// 使用 POST 请求
curl_setopt($curlobj, CURLOPT_POST, 1);
```

* CURLOPT_POSTFIELDS
```php
// POST 的数据部分
// 多个参数: 'theCityCode=北京&&theUserID=leo'
$data = 'theCityName=北京'; 
curl_setopt($curlobj, CURLOPT_POSTFIELDS, $data);
```

###### HTTP 请求头

* CURLOPT_HTTPHEADER
```php
// 包装 http 请求头
// 不设置，请求也会自动生成头部信息，不影响请求数据
curl_setopt($curlobj, CURLOPT_HTTPHEADER, [
"application/x-www-form-urlencoded;charset=utf-8", 
"Content-length: ".strlen($data)
]);
```

* CURLOPT_USERAGENT
```php
// 设置 HTTP 请求头中的 User-Agent 字段
// 也可以直接在 CURLOPT_HTTPHEADER 中设置
// 未设置会出现 “未将对象引用设置到对象的实例” 的错误
curl_setopt($curlobj, CURLOPT_USERAGENT, $_SERVER['HTTP_USER_AGENT']);
```

###### Cookie 相关设置
Cookie 相关设置，这部分设置需要在所有会话开始之前设置

```php
// 使用 Cookie 时，必须先设置时区
date_default_timezone_set('PRC'); 

// 让 cURL 在本地支持 cookie(session)
curl_setopt($curlobj, CURLOPT_COOKIESESSION, TRUE);

// cookie 在本地保存的位置, 读取
curl_setopt($curlobj, CURLOPT_COOKIEFILE, 'cookiefile');

// 存储文件
curl_setopt($curlobj, CURLOPT_COOKIEJAR, 'cookiefile');

// cookie 里存的内容
curl_setopt($curlobj, CURLOPT_COOKIE, session_name().'='.session_id());
```

##### 参考
1. php manual, curl. http://php.net/manual/en/book.curl.php
2. php manual, curl 选项列表。http://php.net/manual/en/function.curl-setopt.php

---

#### 性状

**性状**是类的部分实现(即常量、属性和方法), 可以混入一个或多个现有的 PHP 类中。

* 表明类可以做什么（像是接口）
* 提供模块化实现（像是类)

##### 创建性状
```php
<?php
trait MyTrait {
    // 这里是性状的实现
}
```
##### 使用性状
PHP 解释器在编译时会把性状复制粘贴到类的定义体中。

```php
<?php
class MyClass
{
    use MyTrait;
    // 这里是类的实现
}
```
##### 参考
1. "Modern PHP 中文版", Josh Lockhart 著, 安道译. 中国电力出版社, 2015. pp23-26.


#### 参考
1. php manual, Extension List.  http://php.net/manual/en/extensions.membership.php#extensions.membership.core











