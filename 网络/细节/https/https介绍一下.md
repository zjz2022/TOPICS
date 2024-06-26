### https介绍一下

HTTPS，也就是超文本传输安全协议，是HTTP的安全版本。在HTTP下，数据以明文形式传输，这意味着如果未经加密，则可能被第三方窃取或篡改。与之不同，HTTPS使用SSL/TLS协议对数据进行加密处理，确保数据在传输过程中的安全性和完整性。

在HTTPS连接的建立过程中，客户端和服务器会进行一次“握手”过程，主要步骤如下：

1. 客户端发起请求：客户端向服务器发送一个请求，告知服务器客户端所支持的SSL/TLS的版本和加密套件。

2. 服务器回应：服务器从客户端提供的加密套件中选择一种，并向客户端返回一个数字证书。证书中包含了服务器的公钥、证书颁发机构和其他一些信息。

3. 客户端校验证书：客户端接收到证书后，需要验证其合法性。主要跟证书颁发机构进行比对，判断是否是受信任的颁发机构。

4. 密钥交换：客户端生成一个随机的对称密钥，然后用服务器的公钥加密再发送给服务器，服务器用自己的私钥解密取得这个密钥。

5. 加密通信：服务器和客户端之间就可以使用这个对称密钥进行加密的通信了。