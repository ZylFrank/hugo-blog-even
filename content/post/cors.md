---
title: "Cors"
date: 2020-07-17T16:45:09+08:00
lastmod: 2020-07-17T16:45:09+08:00
draft: false
keywords: ['Cors']
description: "Cross-Origin Resource Sharing"
tags: ['Cors']
categories: ['Cors']
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: false
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---
# Summary

> CORS (Cross-Origin Resource Sharing，跨域资源共享) 是一个系统，它由一系列传输的HTTP头组成，这些HTTP头决定浏览器是否阻止前端 JavaScript 代码获取跨域请求的响应。

<!--more-->

同源安全策略 默认阻止“跨域”获取资源。但是 CORS 给了web服务器这样的权限，即服务器可以选择，允许跨域请求访问到它们的资源

## 浏览器的同源安全策略(same-origin policy)

> The same-origin policy is a critical security mechanism that restricts how a document or script loaded from one origin can interact with a resource from another origin. It helps isolate potentially malicious documents, reducing possible attack vectors.

作用: 限制一个源上的文档或者它加载的脚本与另一个源的资源进行交互。它能帮助阻隔恶意文档，减少被攻击的可能。

## 同源的定义

> 如果两个 URL 的 protocol、port (如果有指定的话)和 host 都相同的话，则这两个 URL 是同源。

下表给出了与`http://store.company.com/dir/page.html` 的源进行对比的示例:

| URL | 结果 | 原因 |
| --- |:---:| :---:|
| `http://store.company.com/dir2/other.html` | 同源 | **只有路径不同** |
| `https://store.company.com/secure.html` | 失败 | **协议不同** |
| `http://store.company.com:81/dir/etc.html` | 失败 | **端口不同** |
| `http://news.company.com/dir/other.html` | 失败 | **主机不同** |

## IE 中的特例

- 授信范围: 两个相互之间高度互信的域名，则不受同源策略限制。
- 端口: IE 未将端口号纳入到同源策略的检查中，因此 `https://company.com:81/index.html` 和 `https://company.com/index.html`  属于同源并且不受任何限制。

## Cors Header

| 请求头 | 解释 |
| --- |:---:|
| `Access-Control-Allow-Origin` | 指示请求的资源能共享给哪些域 |
| `Access-Control-Allow-Credentials` | 指示当请求的凭证标记为 true 时，是否响应该请求 |
| `Access-Control-Allow-Headers` | 用在对预请求的响应中，指示实际的请求中可以使用哪些 HTTP 头 |
| `Access-Control-Allow-Methods` | 指定对预请求的响应中，哪些 HTTP 方法允许访问请求的资源 |
| `Access-Control-Expose-Headers` | 指示哪些 HTTP 头的名称能在响应中列出 |
| `Access-Control-Max-Age` | 指示预请求的结果能被缓存多久 |
| `Access-Control-Request-Headers` | 用于发起一个预请求，告知服务器正式请求会使用那些 HTTP 头 |
| `Access-Control-Request-Method` | 用于发起一个预请求，告知服务器正式请求会使用哪一种 HTTP 请求方法 |
| `Origin` | 指示获取资源的请求是从什么域发起的 |

---

## HTTP访问控制

跨域资源共享(CORS) 是一种机制，它使用额外的 HTTP 头来告诉浏览器  让运行在一个 origin (domain) 上的Web应用被准许访问来自不同源服务器上的指定的资源。当一个资源从与该资源本身所在的服务器不同的域、协议或端口请求一个资源时，资源会发起一个跨域 HTTP 请求。

出于安全原因，浏览器限制从脚本内发起的跨源HTTP请求。 例如，XMLHttpRequest和Fetch API遵循同源策略。 这意味着使用这些API的Web应用程序只能从加载应用程序的同一个域请求HTTP资源，除非响应报文包含了正确CORS响应头。

### 简单请求(Simple requests)

该请求不会触发CORS预检请求，简单请求需要满足以下条件

- 使用以下方法：
  - GET
  - HEAD
  - POST
- Context-Type的值仅限于下列三个：
  - text/plain
  - multipart/form-data
  - application/x-www-form-urlencoded

![Simple Request](/img/cors/simple-request.png "Simple Request")

```http
-----------------Request Headers--------------------
GET /resources/public-data/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Connection: keep-alive
Referer: http://foo.example/examples/access-control/simpleXSInvocation.html
Origin: http://foo.example

-----------------Response Headers--------------------
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 00:23:53 GMT
Server: Apache/2.0.61
Access-Control-Allow-Origin: *
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: application/xml
```

- 第11行 的请求首部字段 `Origin` 表明该请求来源于 `http://foo.example`

- 第17行 `Access-Control-Allow-Origin: *` 表明，该资源可以被任意外域访问

### 预检请求(Preflighted requests)

需预检的请求要求必须首先使用`OPTIONS`方法发起一个预检请求到服务器，以获知服务器是否允许该实际请求。"预检请求“的使用，可以避免跨域请求对服务器的用户数据产生未预期的影响

![Preflighted requests](/img/cors/preflighted-requests.png "Preflighted requests")

预检请求

```http
-----------------Request Headers--------------------
OPTIONS /resources/post-here/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Connection: keep-alive
Origin: http://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type

-----------------Response Headers--------------------
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 0
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain
```

OPTIONS 是 HTTP/1.1 协议中定义的方法，用以从服务器获取更多信息。该方法不会对服务器资源产生影响。 预检请求中同时携带了下面两个首部字段

请求

```text
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```

- 首部字段 Access-Control-Request-Method 告知服务器，实际请求将使用 POST 方法。
- 首部字段 Access-Control-Request-Headers 告知服务器，实际请求将携带两个自定义请求首部字段：X-PINGOTHER 与 Content-Type。服务器据此决定，该实际请求是否被允许。

响应

```text
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
```

- 首部字段 Access-Control-Allow-Methods 表明服务器允许客户端使用 POST, GET 和 OPTIONS 方法发起请求
- 首部字段 Access-Control-Allow-Headers 表明服务器允许请求中携带字段 X-PINGOTHER 与 Content-Type
- 首部字段 Access-Control-Max-Age 表明该响应的有效时间为 86400 秒，也就是 24 小时。在有效时间内，浏览器无须为同一请求再次发起预检请求。


实际请求

```code
-----------------Request Headers--------------------
POST /resources/post-here/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Connection: keep-alive
X-PINGOTHER: pingpong
Content-Type: text/xml; charset=UTF-8
Referer: http://foo.example/examples/preflightInvocation.html
Content-Length: 55
Origin: http://foo.example
Pragma: no-cache
Cache-Control: no-cache

<?xml version="1.0"?><person><name>Arun</name></person>

-----------------Response Headers--------------------
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:40 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://foo.example
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 235
Keep-Alive: timeout=2, max=99
Connection: Keep-Alive
Content-Type: text/plain

[Some GZIP'd payload]
```

## 使用Nginx解决跨域问题

### Nginx反向代理，将前后端不相同的源统一代理到同一个源上

> 示例：如前端在http://localhost:8000上；服务端在http://localhost:3001上，因为端口不同所以会产生跨域问题，现将前后端统一代理到http://localhost:5000端口上

Nginx配置如下:

```nginx
server {
    listen 5000;
    server_name localhost;

    location / {
        proxy_pass http://localhost:8000;
    }

    # 只代理http://localhost:3001/no-cors的服务端接口
    location = /no-cors {
        proxy_pass http://localhost:3001;
    }
}
```

### Nginx对服务端进行配置

> 使用Nginx对服务端进行配置，主要是给服务端的响应加上支持跨域的头部信息

```nginx
server {
    listen 3002;
    server_name localhost;

    location /no-cors {
        proxy_pass http://localhost:3001;
        # 指定允许跨域的方法，*代表所有
        add_header Access-Control-Allow-Methods *;
        # 预检命令的缓存
        add_header Access-Control-Max-Age 3600;
        # 带cookie请求需要加上这个字段，并设置为true
        add_header Access-Control-Allow-Credentials true;
        # 表示允许这个域跨域调用（客户端发送请求的域名和端口） 
        # $http_origin动态获取请求客户端请求的域 不用*的原因是带cookie的请求不支持*号
        add_header Access-Control-Allow-Origin $http_origin;
        # 表示请求头的字段 动态获取
        add_header Access-Control-Allow-Headers $http_access_control_request_headers;
    }
}
```