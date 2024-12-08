# lsof 用于列出当前系统打开的文件及其相关信息（文件描述符、网络套接字等）


1. 查看所有打开的文件
lsof
显示系统中所有打开的文件。

2. 列出某个用户打开的文件
lsof -u <username>
例如，lsof -u root 显示 root 用户打开的文件。
排除某个用户：
lsof -u ^<username>

3. 查看某个进程的打开文件
lsof -p <pid>
例如，lsof -p 1234 显示 PID 为 1234 的进程打开的文件。

4. 查看某个文件被哪些进程使用
lsof <file>
例如，lsof /var/log/syslog 显示哪些进程正在使用 /var/log/syslog。

5. 查看某个端口的使用情况
lsof -i:<port>
例如，lsof -i:80 查看哪些进程正在使用 80 端口。

6. 查看网络连接
## 所有网络连接
lsof -i

## 指定协议
lsof -i tcp
lsof -i udp
例如，lsof -i tcp 显示所有 TCP 连接。

## 指定主机或端口
lsof -i @<hostname>
例如：
lsof -i @192.168.1.100
显示与 192.168.1.100 相关的连接。

7. 列出某个目录下的打开文件
lsof +D <directory>
例如，lsof +D /var 显示 /var 目录及其子目录中的所有打开文件。
注意：可能会耗时较长，特别是目录很大的时候。

8. 显示进程的文件句柄
lsof -p <pid>
结合文件描述符类型：
cwd：当前工作目录。
txt：程序的文本代码段。
mem：内存映射的文件。
fd：文件描述符。

9. 杀死占用某个文件或端口的进程
结合 grep 和 kill：
kill -9 $(lsof -t -i:<port>)
例如：kill -9 $(lsof -t -i:80) 杀死占用 80 端口的进程。


10. 查看某个用户的网络连接
lsof -i -u <username>
例如：lsof -i -u root 显示 root 用户的所有网络连接。


11. 实时查看打开文件（持续刷新）
watch -n 1 'lsof <options>'
例如：watch -n 1 'lsof -i:80' 每秒刷新一次 80 端口的使用情况。


12. 列出使用某个设备的文件
lsof /dev/<device>
例如，lsof /dev/sda1 查看哪些进程正在使用设备 /dev/sda1。


13. 显示所有类型的文件描述符
lsof -a
配合其他参数使用。例如：
lsof -a -u root -i tcp

# 示例命令合集：

## 查看占用 22 端口的进程：
lsof -i:22

## 显示某目录的打开文件：
lsof +D /tmp

## 杀死占用某文件的进程：
kill -9 $(lsof -t /path/to/file)

## 查看所有 UDP 连接：
lsof -i udp

## 查看某个用户的活动：
lsof -u username
