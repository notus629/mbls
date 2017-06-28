### 网络与服务

> 目录
* [防火墙](#防火墙)
    * [Ubuntu](#ubuntu)

####防火墙

##### Ubuntu

Ubuntu 防火墙为 iptables (Ubuntu16.04 默认有装）, 默认允许所有的流量.

* 列出当前 iptables 中所有规则
```
$ sudo iptables -L
```

##### 参考
[1] 在Ubuntu Server是配置iptables防火墙. http://www.jb51.net/os/Ubuntu/45291.html
