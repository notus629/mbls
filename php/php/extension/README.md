### PHP 扩展

> 目录

* [cURL](#curl)
    * [安装](#安装)
    * [基本步骤](#基本步骤)
    * [curl_setopt](#curl_setopt)
        *[基本选项参数](#基本选项参数)
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

* 基本示例

```php
// 设置网页的 URL
// 参数 1： $ch 为 cURL 资源
// 参数 2： CURLOPT_URL，为对应的选项名称
// 参数 3： 选项的对应值
curl_setopt($ch, CURLOPT_URL, "http://www.baidu.com");

```

###### 基本选项参数



##### 参考
1. http://php.net/manual/en/book.curl.php


















