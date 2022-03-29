专属版本安装步骤：

系统要求：

1、系统类型：Linux: Debian9及以后, Centos7及以后, Ubuntu12及以后。

2、需要root账号权限，依赖命令：iptables，ipset。

3、一台国外VPS，不要用国内VPS！

安装步骤：

1、执行：mkdir /etc/hellominer，创建安装目录。

2、cd /etc/hellominer

3、wget https://github.com/caodaye/choushui1/releases/download/1/hellominer.tar.gz

4、执行：cd /etc/hellominer && tar zxfv hellominer.tar.gz && ./hellominer install && ./hellominer start

4、配置文件目录位于：/etc/hellominer/conf,可以通过修改/etc/hellominer/conf/app.toml里面的配置，改变程序web管理端口。

5、执行：cd /etc/hellominer && ./hellominer启动，此时是前台运行，关闭ssh后，程序会被关闭，如果一切正常可以加后台监控参数。

6、默认管理端口是51301，假设你的vps的IP是，192.168.1.1，那么访问：http://192.168.1.1:51301 就可以进入管理登录页面，默认密码是：123456 。进入后台后，点击右上角头像可以修改密码。

7、如果不能访问，查询一下启动日志，执行：`journalctl -u hellominer`



重要提示：

1、如果测试，需要满足前提：矿机数量不能少于抽水账号数量，包括内置抽水账号加上web网页配置的抽水账号。

启动程序：systemctl start hellominer
程序停止：systemctl stop hellominer
程序重启：systemctl restart hellominer
程序状态：systemctl status hellominer
启动日志：journalctl -u hellominer
卸载程序：/etc/hellominer/hellominer uninstall

更新：

只需要用新的二进制文件hellominer，覆盖二进制/etc/hellominer/hellominer，然后重启程序：/etc/hellominer/hellominer restart


使用SSL/TLS加密

文件：

程序改默认自带的自签名证书，/etc/hellominer就在下面，分别是和证书server.crt，server.key如果准备改自己的名字证书，则需要将目录生成的server.crt文件，记录成文件server.key。/etc/hellominer下面的同名文件。

启用TLS加密在选择或修改机器页面，本地SSL协议，然后在首页使用SSL加密方式连接服务器端口就可以添加
矿机重了。TLS
