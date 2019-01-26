# freenet
科学上网

Linux ShadowSock 翻墙

Ubuntu 16.04.1 LTS xenial x86_64


sudo apt install privoxy shadowsocks


建立～/shadowsocks.json 内容如下

{
"server": "138.128.194.135",   //修改成你的server ip
"server_port": 443,
"local_address": "127.0.0.1",
"local_port": 1080,
"password": "0BDF3GVTnf",      //修改为对应server的密码
"method": "aes-256-cfb",
"remarks": "SHADOW"
}


停止 privoxy 

sudo systemctl stop privoxy

编辑 /etc/privoxy/config 添加如下

forward-socks5t		/		127.0.0.1:1080  .

启动 privoxy

sudo systemctl enable privoxy
sudo systemctl start  privoxy



启动翻墙脚本如下：


sslocal -c ~/shadowsocks.json &

export http_proxy=127.0.0.1:8118
export https_proxy=127.0.0.1:8118





