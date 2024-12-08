# curl 用于与各种网络服务交互


1. 发送 GET 请求
curl <URL>
例如：
curl https://example.com
默认发送 GET 请求并输出响应内容到终端。


2. 保存响应到文件
curl -o <filename> <URL>
例如：
curl -o page.html https://example.com
使用自动文件名保存
curl -O <URL>
例如：
curl -O https://example.com/index.html


3. 发送 POST 请求
curl -X POST -d "<data>" <URL>
例如：
curl -X POST -d "key=value&foo=bar" https://example.com/api
发送 JSON 数据
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' <URL>
例如：
curl -X POST -H "Content-Type: application/json" -d '{"name":"John"}' https://example.com/api


4. 添加自定义请求头
curl -H "Header-Name: Header-Value" <URL>
例如：
curl -H "Authorization: Bearer <token>" https://example.com/api

5. 指定用户名和密码
curl -u <username>:<password> <URL>
例如：
curl -u admin:password https://example.com/login

6. 查看响应头
curl -I <URL>
例如：
curl -I https://example.com
只显示响应头而不下载正文

7. 跟踪重定向
curl -L <URL>
例如：
curl -L https://example.com

8. 指定请求方法
curl -X <METHOD> <URL>
例如：
curl -X DELETE https://example.com/resource/123

9. 设置超时时间
curl --connect-timeout <seconds> <URL>
例如：
curl --connect-timeout 10 https://example.com

10. 使用代理
curl -x <proxy> <URL>
例如：
curl -x http://proxy.example.com:8080 https://example.com

11. 下载限制速度
curl --limit-rate <speed> <URL>
例如：
curl --limit-rate 100k https://example.com

12. 显示进度条
curl -# <URL>
例如：
curl -# -O https://example.com/largefile.zip

13. 上传文件
curl -T <filename> <URL>
例如：
curl -T file.txt ftp://ftp.example.com/upload/

14. 发送带 Cookies 的请求
从文件加载 Cookies
curl -b <cookie-file> <URL>
例如：
curl -b cookies.txt https://example.com
保存 Cookies 到文件
curl -c <cookie-file> <URL>
例如：
curl -c cookies.txt https://example.com

15. 查看请求和响应详细信息
curl -v <URL>
例如：
curl -v https://example.com


16. 指定 HTTP 版本
HTTP/1.1：
curl --http1.1 <URL>
HTTP/2：
curl --http2 <URL>


17. 忽略 SSL 验证
curl -k <URL>
例如：
curl -k https://example.com


18. 将响应保存到标准输出和文件
curl -o <filename> -v <URL>
例如：
curl -o response.txt -v https://example.com


# 示例命令合集：
## 获取网页内容并保存：
curl -o index.html https://example.com

## 发送带自定义头的 POST 请求：
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://example.com/api

## 查看 HTTP 响应头：
curl -I https://example.com

## 测试 HTTPS 链接，忽略证书：
curl -k https://example.com

