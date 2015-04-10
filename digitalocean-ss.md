## DigitalOcean
DigitalOcean是国外性价比非常高的一家VPS服务商，一个月的费用是5美元（20G SSD, 512M 内存）。
注册账号后要先进行邮箱验证，然后添加信用卡（不用付款）或用paypal支付5刀进行验证。验证完后就可以创建Droplet了

机房选择：San Francisco。对中国来说这是最快的机房
系统根据自己的情况选择，我选择的是centos 6.5 x64

## SS
服务端安装配置：
### 对于新的服务器要先安装一些工具，然后通过工具安装SS
CentOS:
```
yum install python-setuptools && easy_install pip
pip install shadowsocks
```
### 使用
```
ssserver -p 443 -k password -m rc4-md5
```
如果要后台运行：
```
sudo ssserver -p 443 -k password -m rc4-md5 --user nobody -d start
```
如果要停止：
```
sudo ssserver -d stop
```
如果要检查日志
```
sudo less /var/log/shadowsocks.log
```
用-h查看所有参数

用DigitalOcean的网速可以达到8-9M，延迟少的时候100多，多的时候200多，已经非常快了。
为了在youtube上看1080p的在线视频不卡，可以使用“锐速”

## 锐速
首先去锐速的网站上注册账号，安装过程中需要输入账号和密码

### 安装：
```
wget http://my.serverspeeder.com/d/ls/serverSpeederInstaller.tar.gz
tar xzvf serverSpeederInstaller.tar.gz
bash serverSpeederInstaller.sh
```
安装的过程中出现以下内容时选择：
```
Auto load ServerSpeeder on linux start-up?[n]:y
Run ServerSpeeder now?[y]:y
```
其他地方按回车键就可以了。

### 优化：
要看上1080p视频还需要优化配置
```
vi /serverspeeder/etc/config
rsc="1"
advinacc="1" 
maxmode="1" 
```
rsc=“1” => RSC网卡驱动模式
advinacc="1” => 流量方向加速
maxmode="1”  => 最大传输模式
