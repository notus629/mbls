### Vagrant

> 目录
* [Vagrantfile](#vagrantfile)
* [参考](#参考)

#### Vagrantfile

配置表 

命令 | 说明
--- | ---
`config.vm.network "forwarded_port", guest: 3306, host: 3306` | Port Forwarding
`config.vm.network "private_network", ip: "192.168.33.10" `| 设置静态地址



#### 参考
[1] Connect to MySQL on your Vagrant Machine. https://www.barrykooij.com/connect-mysql-vagrant-machine/