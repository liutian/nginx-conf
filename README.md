### 命令行
- 测试配置文件是否有效：`nginx -t -c <***.conf>`

### nginx中proxy_pass小斜杠

在location 都以 / 结尾时：
- 如果proxy_pass配置值 包含 / 拼接转发路径时就去掉 location 匹配路径部分
- 如果proxy_pass配置值 不包含 / 拼接转发路径时就保留 location 匹配路径部分

> https://zhuanlan.zhihu.com/p/95754949

### 备忘录
- 配置项通常允许配置变量
- server_name配置规则？
- location配置规则？
- rewrite规则？
- 对客户端进行ssl双向校验
- 性能调优之操作系统限制:文件描述符限制和tcp端口数量限制
- `$upstream_cache_status` 代理缓存命中的状态:命中HIT，未命中MISS


### 生成ssl自签名证书
- openssl genrsa -des3 -out ssl.key 1024
- mv ssl.key xxx.key
- openssl rsa -in xxx.key -out ssl.key
- rm xxx.key
- openssl req -new -key ssl.key -out ssl.csr
- openssl x509 -req -days 365 -in ssl.csr -signkey ssl.key -out ssl.crt
- rm xxx.csr
