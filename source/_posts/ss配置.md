---
title: ss配置
date: 2018-09-11 13:43:12
tags:
---


# Server搭建
## 下载shadowsocks服务安装脚本	

	wget --no-check-certificate  https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh

## 修改脚本权限
	
	chmod +x shadowsocks.sh

## 运行安装脚本
		
	./shadowsocks.sh 2>&1 | tee shadowsocks.log

  设置密码， 加密算法选择aes-256-cfb

# Server Config

## 卸载方法
	
	./shadowsocks.sh uninstall

## 多用户多端口配置文件示例

	{
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

  
## 防火墙设置
	
	centos7 防火墙命令
	firewall-cmd --permanent --zone=public --add-port=8990/tcp
	firewall-cmd --permanent --zone=public --add-port=8990/udp
	firewall-cmd  --reload	


用我爱共产党命令
	
	启动：/etc/init.d/shadowsocks start
	停止：/etc/init.d/shadowsocks stop
	重启：/etc/init.d/shadowsocks restart
	状态：/etc/init.d/shadowsocks status

# 安装锐速+bbr 加速     
## 更换centos内核
	rpm -ivh http://soft.91yun.org/ISO/Linux/CentOS/kernel/kernel-3.10.0-229.1.2.el7.x86_64.rpm --force
## 安装锐速
	wget -N --no-check-certificate https://raw.githubusercontent.com/91yun/serverspeeder/master/serverspeeder-all.sh && bash serverspeeder-all.sh

可能会提示内核版本问题，选择一个最接近的版本即可

## 使用google bbr
	wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
	chmod +x bbr.sh
	./bbr.sh

Google 开源了其 TCP BBR 拥塞控制算法，并提交到了 Linux 内核，从 4.9 开始，Linux 内核已经用上了该算法。	

# Clients
不同平台有对应的客户端：https://shadowsocks.org/en/download/clients.html
