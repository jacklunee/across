安装BBR

使用root用户登录，运行以下命令：

wget --no-check-certificate https://raw.githubusercontent.com/jacklunee/across/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh

安装完成后，脚本会提示需要重启 VPS，输入 y 并回车后重启。
重启完成后，进入 VPS，验证一下是否成功安装最新内核并开启 TCP BBR，输入以下命令：

uname -r
查看内核版本，含有 4.13 就表示 OK 了

sysctl net.ipv4.tcp_available_congestion_control
返回值一般为：
net.ipv4.tcp_available_congestion_control = bbr cubic reno

sysctl net.ipv4.tcp_congestion_control
返回值一般为：
net.ipv4.tcp_congestion_control = bbr

sysctl net.core.default_qdisc
返回值一般为：
net.core.default_qdisc = fq

lsmod | grep bbr
返回值有 tcp_bbr 模块即说明 bbr 已启动。

卸载方法
vi /etc/sysctl.conf
把net.ipv4.tcp_congestion_control
改成#net.ipv4.tcp_congestion_control
然后reboot


# Across the Great Wall we can reach every corner in the world

## wireguard.sh

- Description: This is a shell script for configure and start WireGuard VPN server.
- Intro: https://teddysun.com/554.html

## bbr.sh

- Description: Auto install latest kernel for TCP BBR
- Intro: https://teddysun.com/489.html

## kms.sh

- Description: Auto install KMS Server
- Intro: https://teddysun.com/530.html
- **KMS Server Docker Image**: https://hub.docker.com/r/teddysun/kms

## bench.sh

- Description: Auto test download & I/O speed script
- Intro: https://teddysun.com/444.html

## backup.sh

- You must modify the config before run it
- Backup MySQL/MariaDB/Percona datebases, files and directories
- Backup file is encrypted with AES256-cbc with SHA1 message-digest (option)
- Auto transfer backup file to Google Drive (need install `gdrive` command) (option)
- Auto transfer backup file to FTP server (option)
- Auto delete Google Drive's or FTP server's remote file (option)
- Intro: https://teddysun.com/469.html

## ftp_upload.sh

- You must modify the config before run it
- Upload file(s) to FTP server
- Intro: https://teddysun.com/484.html

## unixbench.sh

- Description: Auto install unixbench and test script
- Intro: https://teddysun.com/245.html

## l2tp.sh(Deprecated, DO NOT USE)

- Description: Auto install L2TP/IPSec VPN Server
- Intro: https://teddysun.com/448.html
- Change to **L2TP/IPsec VPN Server Docker Image**: https://hub.docker.com/r/teddysun/l2tp

## pptp.sh(Deprecated, DO NOT USE)

Copyright (C) 2013-2019 Teddysun <i@teddysun.com>
