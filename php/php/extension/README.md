### PHP 扩展

> 目录

* [cURL](#curl)


#### cURL

*cURL* 可以使用 URL 的语法模拟浏览器来传输数据，因为它是模拟浏览器，因此它同样支持多种协议，FTP, FTPS, HTTP, HTTPS, GOPHER, TELNET, DICT, FILE 以及 LDAP 等协议都可以很好的支持。

包含：HTTPS 认证，HTTP POST 方法，HTTP PUT 方法，FTP 上传，keyberos 认证，HTTP 上传，代理服务器，cookies，用户名/密码认证，下载文件断点续传，上传文件断点续传，http 代理服务器管道，甚至它还支持 IPv6，scoket5 代理服务器，通过 http 代理服务器上传文件。

##### 基本步骤

```php
<?php

 /*用代码完成上述cURL的四步*/
 
// 1.初始化，创建一个新 cURL 资源 
$ch = curl_init();
 
// 2.设置 URL 和相应的选项 
curl_setopt($ch, CURLOPT_URL, "http://www.lampbrother.net/"); 
curl_setopt($ch, CURLOPT_HEADER, 0);
 
// 3.抓取 URL 并把它传递给浏览器
curl_exec($ch);
 
// 4.关闭 cURL 资源，并且释放系统资源 
curl_close($ch);
 
?>
```