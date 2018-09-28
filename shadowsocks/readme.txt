# 开始搭建
一：服务器端
- 1.已购买云服务器
- 2.以root身份运行安装shadowsocks
  执行命令：
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
    在执行最后一个命令时，会出现输入密码，设置服务器端口，以及选择的加密方式
    安装完成后，出现如下提示：
      Congratulations, Shadowsocks-python server install completed!
      Your Server IP        :your_server_ip
      Your Server Port      :your_server_port
      Your Password         :your_password
      Your Encryption Method:your_encryption_method

      Welcome to visit:https://teddysun.com/342.html
      Enjoy it!
    配置文件：
      单用户配置文件(配置文件路径为:/etc/shadowsocks.json ):{
        "server":"0.0.0.0",
        "server_port":your_server_port,
        "local_address":"127.0.0.1",
        "local_port":1080,
        "password":"your_password",
        "timeout":300,
        "method":"your_encryption_method",
        "fast_open": false
    }
     多用户配置文件(配置文件路径为:/etc/shadowsocks.json ):{
        "server":"0.0.0.0",
        "local_address":"127.0.0.1",
        "local_port":1080,
        "port_password":{
             "8989":"password0",
             "9001":"password1",
             "9002":"password2",
             "9003":"password3",
             "9004":"password4"
        },
        "timeout":300,
        "method":"your_encryption_method",
        "fast_open": false
    }
 
- 3.安装完成后启动shadowsocks服务
    /etc/init.d/shadowsocks start
- 4.服务器防火墙配置
    将shadowsocks服务器设置的端口号加入防火墙规则  
iptables -I INPUT -p tcp --dport your_server_port -j ACCEPT 
iptables -I OUTPUT -p tcp --dport your_server_port -j ACCEPT
- 5.安装加速器(可不安装) 5 
 wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh 
 chmod +x bbr.sh./bbr.sh
 
二. shadowsocks客户端（windows版）
2.1 下载shadowsocks客户端https://github.com/shadowsocks/shadowsocks-windows/releases/download/4.0.6/Shadowsocks-4.0.6.zip
    也可以使用已经上传的。
2.2 解压并打开shadowsocks客户端 服务器 菜单添加多个服务器，服务器地址写你的vps的ip地址即可，端口号、密码、加密方式都按照服务端的配置写即可。
   选择 启用系统代理 来启用系统代理。请禁用浏览器里的代理插件，或把它们设置为使用系统代理，除了设为系统代理，你也可以直接自己配置浏览器代理。
   在 SwitchyOmega 中把代理设置为 SOCKS5 或 HTTP 的 127.0.0.1:1080。这个 1080 端口可以在服务器设置中设置。
   至此就可以用浏览器访问Google, facebook, youtube等

