#### 加密方式
- 对称加密：唯一密钥可以用来加密也可以用来解密。需要双方都有密钥
- 非对称加密：公钥和私钥用来加密和解密，可以用公钥加密私钥解密，也可以私钥加密公钥解密。客户端明文通过私钥加密用密钥解密。
- 混合加密：服务端用非对称加密的私钥加密对称加密的密钥，传给客户端，客户端用非对称加密的公钥解密出对称加密的私钥，双方开始用私钥进行通信（缺点：中间人可以自己生成非对称加密公钥替换掉服务端公钥发送给客户端，客户端此时没法认证出公钥的可信性）
- SSL：首先需要从证书机构申请证书（证书中含有签名和服务端公钥）。客户端发起 HTTP 请求时，服务端将证书发送给客户端，客户端认证证书真伪，然后解密出服务端公钥，用公钥加密自己生成的对称加密密钥传给服务端，利用私钥加密进行通话。


#### https 特点
https 基于 http 协议，通过 ssl 或者 tls 提供加密处理数据，验证对方身份已经数据完整性保护

- 内容加密：采用混合加密技术
- 验证身份：通过证书认证客户端访问的是自己的服务器
- 保护数据完整性：防止传输的内容被中间人冒充或者篡改

#### http 和 https 区别
- HTTPS 需要到 CA 申请证书，一般证书需要缴费
- HTTP 运行在 TCP 之上，传输都是明文。HTTPS 运行在 SSL/TLS 上，SSL/TLS 运行在 TCP 上，所有传输经过加密
- HTTP 和 HTTPS 使用的是不同的连接方式，用的端口也不一样
- http 连接很简单，无状态；HTTPS 协议可进行加密传输、身份认证，可以有效防止运营商劫持，比 http 安全