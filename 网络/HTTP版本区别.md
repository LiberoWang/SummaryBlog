## HTTP1.0、HTTP1.1和HTTP2.0的区别

### HTTP

`HTTP`(超文本传输协议)协议建立在TCP协议之上，所以HTTP协议的瓶颈及其优化技巧都是基于`TCP`协议本身的特性.

![image](https://user-images.githubusercontent.com/25894364/123062960-91424680-d43f-11eb-9228-bbeffd102fd0.png)


### HTTP1.0和HTTP1.1

![image](https://user-images.githubusercontent.com/25894364/123065744-06168000-d442-11eb-802b-89c8f79bcf0c.png)

> 最主要的亮点

1. `HTTP1.1`增加了`keep-alive`支持`长连接`. 
  - 保持 TCP 连接可以省去下次请求时需要建立连接的时间，提升资源加载速度.
2. 支持管道传输

### HTTP2.0的新特性

1. 二进制传输
2. 头部(Headers)压缩
3. 服务端推送
4. 多路复用
5. 管道机制
6. 提高安全性

> HTTP2.0的多路复用和HTTP1.X中的长连接复用有什么区别？

![image](https://user-images.githubusercontent.com/25894364/123068158-365f1e00-d444-11eb-8004-a7b7b3ca4280.png)

### HTTP与HTTPS

![image](https://user-images.githubusercontent.com/25894364/123064567-f8acc600-d440-11eb-9c16-6220d9437962.png)

`HTTP`的端口号是`80`, `HTTPS`的端口是`443`

耗时：`TCP`握手耗时 + `SSL`链接耗时

### HTTP3.0 - QUIC

链接：`https://network.51cto.com/art/202009/625999.htm`

### 参考链接

1. `https://zhuanlan.zhihu.com/p/351912410`
2. `https://juejin.cn/post/6844903489596833800`
3. [解读HTTP/2与HTTP/3 的新特性](https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651557245&idx=1&sn=dddebeb50ae71dcf1557ee52376e9fd9&chksm=80255abcb752d3aadc09ff2546a40400f811ff4b11810b9b73a427f6cfcb815ff16fbc60f2aa&mpshare=1&scene=23&srcid&sharer_sharetime=1571907152588&sharer_shareid=4a6e70ce6f2ac4b5c0728e662efb1a04%23rd)
  
