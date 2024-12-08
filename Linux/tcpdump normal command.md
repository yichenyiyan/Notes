# tcpdump 是一个命令行工具，用于捕获和分析网络流量

# 基础命令
tcpdump

捕获所有网络流量并显示到屏幕上。
可能需要 sudo 权限。

# 指定网络接口
tcpdump -i <interface>
例如，tcpdump -i eth0 捕获 eth0 接口的流量。

# 列出可用接口
tcpdump -D 

# 保存捕获数据到文件
tcpdump -w <file>.pcap
例如，tcpdump -w traffic.pcap 保存流量到 traffic.pcap

# 读取保存的文件：
tcpdump -r traffic.pcap

# 捕获指定数量的数据包
tcpdump -c <count>
例如，tcpdump -c 10 捕获 10 个数据包后停止

# 过滤特定主机的流量
tcpdump host <host>
例如，tcpdump host 192.168.1.1 捕获与 192.168.1.1 相关的流量

# 仅捕获源或目标主机
tcpdump src host <host>   # 仅捕获源地址为指定主机的流量
tcpdump dst host <host>   # 仅捕获目标地址为指定主机的流量

# 捕获特定端口的流量
tcpdump port <port>
例如，tcpdump port 80 捕获 HTTP 流量

# 捕获源或目标端口
tcpdump src port <port>   # 仅捕获源端口为指定值的流量
tcpdump dst port <port>   # 仅捕获目标端口为指定值的流量

# 协议过滤
tcpdump <protocol>
例如：
tcpdump tcp 捕获 TCP 流量。
tcpdump udp 捕获 UDP 流量。
tcpdump icmp 捕获 ICMP 流量。

# 组合条件
tcpdump <condition1> and <condition2>
tcpdump <condition1> or <condition2>
tcpdump <condition1> not <condition2>
例如：
tcpdump host 192.168.1.1 and port 22 捕获 192.168.1.1 的 SSH 流量
tcpdump tcp and not port 80 捕获所有非 HTTP 的 TCP 流量


# 显示数据包内容
tcpdump -X
以十六进制和 ASCII 格式显示数据包内容

# 仅显示摘要信息
tcpdump -q
以简洁模式显示数据包信息。

# 时间戳选项
tcpdump -tttt
显示更详细的时间戳（日期和时间）。

# 更人性化的主机名和端口显示
tcpdump -n -nn
-n：不将 IP 地址解析为主机名
-nn：不将端口解析为服务名

# 指定数据包长度
tcpdump -s <snaplen>
例如，tcpdump -s 0 捕获整个数据包（默认仅捕获 96 字节）

# 示例命令合集：

## 捕获 eth0 上的 HTTP 流量并保存到文件：
tcpdump -i eth0 port 80 -w http_traffic.pcap

## 捕获与 192.168.1.100 通信的所有流量：
tcpdump host 192.168.1.100

## 捕获 TCP 流量，显示内容，并不解析主机名：
tcpdump -n -X tcp

## 捕获 SSH（22端口）的所有数据包：
tcpdump port 22
