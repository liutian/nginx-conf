### 生成ssl自签名证书
- openssl genrsa -des3 -out ssl.key 1024
- mv ssl.key xxx.key
- openssl rsa -in xxx.key -out ssl.key
- rm xxx.key
- openssl req -new -key ssl.key -out ssl.csr
- openssl x509 -req -days 365 -in ssl.csr -signkey ssl.key -out ssl.crt
- rm xxx.csr