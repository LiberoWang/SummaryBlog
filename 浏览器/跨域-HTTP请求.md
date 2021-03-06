### GET 与 POST的区别

[GET和POST的区别](https://github.com/febobo/web-interview/issues/145)

### 同源策略
- 协议相同
- 郁闷相同
- 端口相同

#### 为什么会有跨域 - 为了安全上网

 - 保证了非同源网站的cookie, localStorage, indexedDB
 - 保证了非同源网页的DOM(iframe) 
 - 保证了非同源网站发送的Ajax或者fetch请求(可以发送，但是拒绝接受响应)


> 什么是跨域

协议，主机名(域名)(host)和端口(port)相同的url

> 为什么会引起跨域

出于浏览器的同源策略限制,为了数据的安全性.

同源策略（Same Orgin Policy）是一种约定，它是浏览器核心也最基本的安全功能，它会阻止一个域的js脚本和另外一个域的内容进行交互，如果缺少了同源策略，浏览器很容易受到XSS、CSFR等攻击。
所谓同源（即在同一个域）就是两个页面具有相同的协议（protocol）、主机（host）和端口号（port）。

### 浏览器跨域的解决方案

#### CORS(跨域资源共享)

对于开发者来说，CORS通信与普通的AJAX通信没有区别，浏览器一旦发现是AJAX请求跨域，就会自动添加一些附加的头信息，有时还会多出一次请求。因此，实现CORS的关键是服务器，只要服务器实现了CORS的接口，就可以跨域通信了。

> 简单请求

 - 请求方法是: GET、POST、HEADE
 - HTTP消息头不超过以下字段：

 Accept
 Accept-Language
 Content-Language
 Content-Type: application/x-www-form-urlencoded、multipart/form-data、text/plain

> 非简单请求

非简单请求会先发出一个'预检'请求，OPPTION请求，服务端会检查这个请求，判断是不是跨域请求

 - 请求头是： PUT、DELETE
 - Content-Type: application/json

 通常会在发起正式通信之前，使用`OPPOTION`方法发起一个预检。

 [为什么会出现简单请求和复杂请求](https://www.zhihu.com/question/268998684/answer/344949204)

> 为什么要区分简单和非简单请求

浏览器的安全机制，它认为简单请求是安全的。所以可以通过跨域限制到达服务器，也就没必要对简单请求做预检请求（人家本来就可以通过跨域你预检个什么）

```跨源资源共享 (CORS)（或通俗地译为跨域资源共享）是一种**基于 HTTP 头的机制**，该机制通过允许服务器标示除了它自己以外的其它origin（域，协议和端口），这样浏览器可以访问加载这些资源。跨源资源共享还通过一种机制来检查服务器是否会允许要发送的真实请求，该机制通过浏览器发起一个到服务器托管的跨源资源的"预检"请求。在预检中，浏览器发送的头中标示有HTTP方法和真实请求中会用到的头。```


> 浏览器允许嵌入式资源跨域请求

- <script src="..."> 嵌入跨域脚本
- <img> 标签嵌入图片
- <video>、<audio> 标签嵌入媒体资源
- <iframe> 标签嵌入跨域资源
- <link rel="stylesheet" href="..." > 标签嵌入 CSS
- 字体跨域


[CORS参考资料](https://juejin.cn/post/6859351705453068295)

#### JSONP

JSONP的原理是利用`<script>`或者`img`标签的src属性是没有跨域的限制的，通过指向一个需要访问的地址，由服务端返回一个预先定义好的javascript函数的调用，并将服务器数据以该函数的参数的形式传递过来，此方法需要前后端配合。

且JSONP的方式只能用于`GET`请求，不支持`POST`请求

JSONP方式跨域，会不受同源正常的影响，并且携带跨域域名的`Cookies`。

#### 服务器代理

一般我们在本地环境开发的时候，就是使用`webpack-dev-server`在本地开启一个服务器代理访问

#### document.domain

该形式只能访问二级域名相同的，比如`a.test.com`和`b.test.com`，只要给两个页面添加`document.domai n= test.com`，通过`a.test.com`创建一个`iframe`去控制`iframe`的`window`进行交互。

#### postMessage

`window.postMessage`是HTML5的一个api，运行两个窗口直接进行跨域发送信息。

这种方式通常是获取嵌入式页面的中第三方的数据。一个页面发送数据另一个页面判断来源接收数据。








