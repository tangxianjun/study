# HTPPS配置

**Let’s Encrypt泛域名证书**

#### 下载

下载 certbot-auto 自动生成工具

```
wget https://dl.eff.org/certbot-auto
chmod +x certbot-auto wget https://dl.eff.org/certbot-auto
```



#### 生成证书

```
./certbot-auto certonly --email 邮箱 -d 域名 -d 域名2 --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/director
```

**用途**

多站点配置

`--manual` 表示手动交互模式，Certbot 有很多插件，不同的插件都可以申请证书，用户可以根据需要自行选择

`-d`  为那些主机申请证书，如果是通配符，输入 *.xxxx.com  和 www.xxxx.com

`--preferred-challenges` 使用 DNS 方式校验域名所有权

`--server` Let's Encrypt ACME v2 版本使用的服务器不同于 v1 版本，需要显示指定。

**后续步骤按提示操作即可**

### 重点

**域名验证 dns 解析增加 TXT 配置，对申请域名添加TXT解析，名称为`_achme-challenge`值为交互模式所给出的值**

如阿里云服务器则在云解析DNS中加入此条记录值

**可能会有稍微延迟，不行就从头在执行一次，多等待一会**

成功后会在/etc/letsencrypt/live/xxxx.com/ 目录下生成四个文件

### 测试证书

```
openssl x509 -in /etc/letsencrypt/live/xxxx.com/fullchain.pem -noout -text
```

### nginx配置

**监听443端口**

```
listen 443 ssl; 
```

**增加ssl配置**

```
ssl_certificate /etc/letsencrypt/live/xxxx.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/xxxx.com/privkey.pem;
ssl_session_cache    shared:SSL:1m;
ssl_session_timeout  5m;
ssl_ciphers  HIGH:!aNULL:!MD5;
ssl_prefer_server_ciphers  on;

#80端口跳转到443端口
server
    {
        listen 80 ;
        server_name www.xxxx.com;
        rewrite ^(.*)$  https://$host$1 permanent; 
    } 
```

以及一些基本的ssl配置

**重启nginx**

```
nginx -s reload
```

重启nginx优雅一点

### 续期

证书只有三个月的有效期

可以写脚本自动生成，也可自己在手动生成一遍也不是很麻烦

网上有脚本可以参考









