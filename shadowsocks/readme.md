# 开始搭建
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
- 3.

