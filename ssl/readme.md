 # 创建密钥

```shell
openssl genrsa -des3 -out rootCA.key 2048
```

```shell
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 3650 -out rootCA.pem
```

生成v3.ext文件，里面写域名



```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage=digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName=@alt_names

[alt_names]
DNS.1 = *.l.wizmacau.com
```

生成网址证书，注意Common Name的填写

```shell
openssl req -new -sha256 -nodes -out server.csr -newkey rsa:2048 -keyout server.key

```

```shell
openssl x509 -req -in server.csr -CA [rootCA.pem路径] -CAkey [rootCA.key路径] -CAcreateserial -out server.crt -days 500 -sha256 -extfile v3.ext
```

 证书格式转换

```shell
openssl x509 -outform der -in rootCA.pem -out rootCA.crt
```

