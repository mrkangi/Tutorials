## Samba服务配置

```sh
# 安装服务
yum install samba samba-client samba-swat
# 启动服务
service smb start
# 获取 SELinux
getenforce
# 临时关闭 SELinux
setenforce 0 # 0 == permissive
# 永久关闭 SELinux
vim /etc/selinux/config # 将SELINUX=enforcing改为SELINUX=permissive
# 添加用户
useradd {合法用户名}
# 修改密码
passwd {合法用户名}
# 添加smb用户并设置smb密码，passdb backend = tdbsam 时，添加的用户需要是系统用户
smbpasswd -a {合法用户名}
# 修改配置文件
cat >> /etc/samba/smb.conf << EOF
[{显示目录名}]
        path = {共享路径}
        public = yes
        browsable = yes
        writable = yes
        guest ok = yes
        create mask = 0755
        read only = no
        valid users = {合法用户名}
EOF
# 赋予 {合法用户名} 在 {共享路径} 的权限
```

