# 代理工具 whistle

Source: [KM 2759617947](https://km.sankuai.com/collabpage/2759617947)

```
// 代码块
npm install -g whistle
```

正常的话直接

```
// 代码块
w2 ca
```

即可，但是有时候会报错，也可以手动颁发证书

```
// 代码块
ceilf6@MBP-CKV4TN26M9-0045 ~ % rm -rf ~/.WhistleAppData/.whistle/certs
ceilf6@MBP-CKV4TN26M9-0045 ~ % w2 ca
Certificate installation failed: Error reading file /Users/ceilf6/.WhistleAppData/.whistle/certs/root.crt

ceilf6@MBP-CKV4TN26M9-0045 ~ % mkdir -p ~/.WhistleAppData/.whistle/certs
chmod -R 700 ~/.WhistleAppData/.whistle
ceilf6@MBP-CKV4TN26M9-0045 ~ % cd ~/.WhistleAppData/.whistle/certs

# 生成私钥
openssl genrsa -out root.key 2048

# 生成自签名证书
openssl req -x509 -new -nodes -key root.key -sha256 -days 3650 -out root.crt -subj "/CN=Whistle Root CA"
zsh: command not found: #
Generating RSA private key, 2048 bit long modulus
............................................................+++++
.....................+++++
e is 65537 (0x10001)
zsh: command not found: #
ceilf6@MBP-CKV4TN26M9-0045 certs % openssl genrsa -out root.key 2048
Generating RSA private key, 2048 bit long modulus
..................................+++++
...............................................+++++
e is 65537 (0x10001)
ceilf6@MBP-CKV4TN26M9-0045 certs % openssl req -x509 -new -nodes -key root.key -sha256 -days 3650 -out root.crt -subj "/CN=Whistle Root CA"
ceilf6@MBP-CKV4TN26M9-0045 certs % sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain ~/.WhistleAppData/.whistle/certs/root.crt
ceilf6@MBP-CKV4TN26M9-0045 certs % w2 config set httpsCert ~/.WhistleAppData/.whistle/certs/root.crt
w2 config set httpsKey ~/.WhistleAppData/.whistle/certs/root.key
Type 'w2 help' for usage.
Type 'w2 help' for usage.
```

然后

```
// 代码块
w2 open
```

开启全局代理

```
// 代码块
w2 proxy --on
```

```
// 代码块
w2 start
```

本质就是去配置了 HTTPS, HTTP 代理

[image.png](https://km.sankuai.com/api/file/cdn/2759617947/237351709624?contentType=1&isNewContent=false)

接着书写代理规则

到目标页面中查找目标代理对象的请求地址

[图片](https://km.sankuai.com/api/file/cdn/2759617947/234757400413?contentType=1&isNewContent=false)

然后找到你想要代理其的文件地址

[图片](https://km.sankuai.com/api/file/cdn/2759617947/234757242070?contentType=1&isNewContent=false)

最后 Final URL 显示为最终代理地址就成功了

[图片](https://km.sankuai.com/api/file/cdn/2759617947/234755391975?contentType=1&isNewContent=false)