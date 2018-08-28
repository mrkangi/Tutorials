## Dnsmasq 服务配置
```sh
# 安装
yum install -y dnsmasq
# 启动
service dnsmasq start
# 编辑配置文件
# listen-address={主机ip},127.0.0.1 ，提供局域网访问
# address=/{domain}/{ip} 将{domain}映射至{ip}
vim /etc/dnsmasq.conf 
# 重启 dnsmasq
pkill -9 dnsmasq && dnsmasq
```