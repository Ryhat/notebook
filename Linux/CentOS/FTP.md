# CentOS搭建FTP服务器

[TOC]

## 安装vsftpd

```bash
yum install vsftpd ftp -y
```

## 配置vsftpd

```shell
vim /etc/vsftpd/vsftpd.conf
```

找到以下属性并修改

```shell
anonymous_enable=NO

ascii_upload_enable=YES
ascii_download_enable=YES

ftpd_banner=Welcome to UNIXMEN FTP service.
```

在文末添加

```shell
use_localtime=YES
```

### 激活并启动vsftpd

```shell
systemctl enable vsftpd
systemctl start vsftpd
```

## 防火墙和SELinux配置

```zsh
firewall-cmd --zone=public --add-port=21/tcp --permanent
firewall-cmd --zone=public --add-service=ftp --permanent
```

重新加载防火墙

```shell
firewall-cmd --reload
```

更新SELinux的ftp服务的布尔值

```shell
setbool -P tftp_home_dir on
```

## 创建FTP用户

```sh
useradd ftpuser
passwd ftpuser
```

## 连接到FTP服务器

```shell
ftp 192.168.1.100
```

或者用其他客户端连接。

