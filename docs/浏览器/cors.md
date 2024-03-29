# CORS

> CORS(跨域资源共享, Cross-Origin Resource Sharing) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources

- 浏览器同源策略，限制`XMLHttpRequest`和`Fetch API`, 保障用户安全
- CORS需要在可用性和安全性中间寻找平衡点
- 只是限制ajax

## 哪些请求会应用CORS?

1. `XMLHttpRequest` 和 `Fetch API`
2. ...

## 如何判断两个网站为同源网站

- 协议(schema), 主机(domain), 端口(port)相同才为同源

## 非同源的限制

- Cookie, LocalStorage 和 IndexDB无法读取
- DOM无法获得
- AJAX请求不能发送

- 可用性
  - 带有src的属性标签的可以跨域访问
  - 跨域写操作: 表单提交, 重定向请求

## 简单请求 simple request

> simple request don't trigger a CORS preflight request

简单请求需满足:

- 请求方法：`GET` `HEAD` `POST`
- 仅能使用CORS安全的头部: `Accept`, `Accept-Language`, `Content-Language`, `Content-Type` (内容协商的头部)
- Content-Type的值只能是 text/plain, muiltipart/form-data, application
- 无`xhr.upload.addEventListener()`

发送时额外携带 **Origin**, server 返回时必须额外携带 **Access-Control-Allow-Origin**

简单请求的跨域访问 （简单请求也是有额外逻辑的！）

- 浏览器构造HTTP请求中携带`Origin`头部告知server来自哪个域
- server响应中携带`Access-Control-Allow-Origin`头部告知表示允许哪些域
- 浏览器放行

简单请求


## 预检请求 (preflighted request)

- 预检请求:
  - 方法: option
  - `Origin`头部: 必须携带
  - `Access-Control-Request-Method`
  - `Access-Control-Request-Header`
- 预检请求响应:
  - `Access-Control-Allow-Method`
  - `Access-Control-Allow-Headers`
  - `Access-Control-Expose-Headers`: 哪些响应头部可以供客户端使用
  - `Access-Control-Allow-Credentials`: 告知浏览器是否可以将 **Credentials** 暴露给客户端使用 
    - credentials 包括 cookie, authorization, tls证书等
- 正式请求:
  - 方法变为了用于ajax的方法, 众多头部也都在
  - 同时, 复杂请求其他的头部也都会加上

## 携带 credentials 的简单请求

```js
const invocation = new XMLHttpRequest();
const url = "https://bar.other/resources/credentialed-content/";

function callOtherDomain() {
  if (invocation) {
    invocation.open("GET", url, true);
    invocation.withCredentials = true;
    invocation.onreadystatechange = handler;
    invocation.send();
  }
}
```

```
GET /resources/credentialed-content/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Referer: https://foo.example/examples/credential.html
Origin: https://foo.example
Cookie: pageAccess=2

HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:34:52 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Credentials: true
Cache-Control: no-cache
Pragma: no-cache
Set-Cookie: pageAccess=3; expires=Wed, 31-Dec-2008 01:34:53 GMT
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 106
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain

[text/plain payload]
```

## 携带 credentials 的预检请求

The server must not specify the "*" wildcard for the Access-Control-Allow-Origin response-header value, but must instead specify an explicit origin; for example: Access-Control-Allow-Origin: https://example.com
The server must not specify the "*" wildcard for the Access-Control-Allow-Headers response-header value, but must instead specify an explicit list of header names; for example, Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
The server must not specify the "*" wildcard for the Access-Control-Allow-Methods response-header value, but must instead specify an explicit list of method names; for example, Access-Control-Allow-Methods: POST, GET
The server must not specify the "*" wildcard for the Access-Control-Expose-Headers response-header value, but must instead specify an explicit list of header names; for example, Access-Control-Expose-Headers: Content-Encoding, Kuma-Revision