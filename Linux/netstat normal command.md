# netstat 是一个用于监控网络连接、路由表、接口统计等信息的命令行工具

# 查看所有连接
netstat -a
显示所有活动的连接，包括监听状态的套接字

# 仅显示监听端口
netstat -l
仅显示处于监听状态的端口

# 显示 TCP 连接
netstat -t
显示所有 TCP 协议的连接

# 显示监听的 TCP 连接
netstat -lt

# 显示 UDP 连接
netstat -u
显示所有 UDP 协议的连接

# 显示监听的 UDP 连接
netstat -lu

# 显示 PID 和程序名
netstat -p

关联网络连接的进程信息
例如：
netstat -tp

# 显示路由表
netstat -r
显示系统的路由表信息，与 route 命令类似

# 显示网络接口信息
netstat -i

# 显示所有网络接口的统计信息
例如：
netstat -ie  # 显示详细信息

# 显示网络统计信息
netstat -s
显示每种协议的统计数据（如 TCP、UDP、ICMP 等）

# 定时刷新显示
netstat -c

持续显示网络连接信息，每隔一秒刷新
# 避免主机名解析
netstat -n
显示 IP 地址和端口号，不进行主机名和服务名的解析
例如：
netstat -an

# 过滤特定端口或协议

查看某个特定端口或协议的连接：
netstat -an | grep <port>
例如：

netstat -an | grep 22  # 查看所有 SSH (22端口) 连接

# 查看每个用户的连接
netstat -ap

显示所有连接并关联每个用户的进程
# 显示多播组
netstat -g
显示多播组信息

# 示例命令合集：

## 查看所有 TCP 连接：
netstat -nt

## 查看本机监听的所有端口：
netstat -lnt

## 查看 UDP 连接的状态：
netstat -nu

## 查看 PID 关联的 80 端口服务：
netstat -anp | grep :80

## 实时监控网络连接：
netstat -c