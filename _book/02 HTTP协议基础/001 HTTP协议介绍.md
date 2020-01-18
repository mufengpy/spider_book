[TOC]

## <font color="#0099CC">访问一个网页的过程</font>

1.打开浏览器

2.地址栏输入网址(URL)

3.浏览器发出请求

4.服务器接收到请求后，返回结果给浏览器

5.浏览器接收到结果后，展示数据

## <font color="#0099CC">请求和响应</font>

- 一个URL可能会有多个请求和响应，一个请求对应一个响应
- 请求和响应都有头和体两部分

地址栏输入http://www.mingrenedu.net/

![](..\media\images\image-20200106152724097.png)

### <font color="#F77A0B">请求方法</font>

> 通常使用GET POST
>
> GET常用于返回数据，POST常用于提交表单

```http
GET
POST
HEAD
PUT 
DELETE
CONNECT
OPTIONS
TRACE
```

### <font color="#F77A0B">状态码</font>

```
1XX Informational (信息性状态码)接收的请求正在处理
2XX Success (成功状态码)请求正常处理完毕
3XX Redirection (重定向状态码需要进行附加操作 以完成请求
4XX Client Error (客户端错误状态码)服务器无法处理请求
5XX Server Error (服务器错误状态码)服务器处理请求出错
```

```
2XX 成功
200 OK
204 No Content代表服务器已经对请求成功处理，但是没有实际的资源要返回
206 Partial Content表示客户端进行了范围请求
```

```
3XX 重定向
301 Moved Permanently永久性重定向
302 Found临时性重定向
304 Not Modifie
```

```
4XX 客户端错误
400 Bad Request请求的内容有问题
401 Unauthorized未验证的请求
403 Forbidden请求资源的访问被服务器拒绝
404 Not Found服务器上无法找到请求的资源
```

```
5XX服务器错误
500 Internal Server Error服务器端在执行请求时发生了错误
502 Bad Gateway nginx或者网关后面没有上游服务器能响应请求
503 Service Unavailable服务器暂时处于超负载或正在进行停机维护
504 Gateway Timeout对nginx或者网关请求超时
```