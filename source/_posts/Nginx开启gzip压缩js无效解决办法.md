---
title: Nginx开启gzip压缩js无效解决办法
date: 2018-03-16 16:40:36
tags: gzip/nginx
categories: Nginx
---
#### 1⃣️ nginx -t 查看配置信息

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
#### 2⃣️ sudo vim /etc/nginx/nginx.conf  编辑配置文件；在http对象里面加入
```
http {
  gzip on;
  gzip_min_length  1000;
  gzip_buffers     4 8k;   
  gzip_http_version 1.1; 
  gzip_types       text/plain application/x-javascriptext/css application/xml application/javascripapplication/json;
  ...
}
```
#### 3⃣️ 相关字段儿解释  
1、**开启gzip**  
gzip on;  
2、**启用gzip压缩的最小文件，小于设置值的文件将不会压缩**  
gzip_min_length 1k;  
3、**gzip 压缩级别，1-10，数字越大压缩的越好，也越占用CPU时间，后面会有详细说明**  
gzip_comp_level 2;  
4、**进行压缩的文件类型。javascript有多种形式。其中的值可以在 mime.types 文件中找到。注意，gzip_types里面的内容一定要包含content-types里面的类型，不然无效**  
gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png font/ttf font/otf image/svg+xml;  
5、**是否在http header中添加Vary: Accept-Encoding，建议开启**  
gzip_vary on;  
6、**禁用IE 6 gzip**  
gzip_disable "MSIE [1-6]\.";  
7、**开启缓存**  
location ~* ^.+\.(ico|gif|jpg|jpeg|png)$ { 
    access_log   off; 
    expires      30d;
}

location ~* ^.+\.(css|js|txt|xml|swf|wav)$ {
    access_log   off;
    expires      24h;
}

location ~* ^.+\.(html|htm)$ {
    expires      1h;
}

location ~* ^.+\.(eot|ttf|otf|woff|svg)$ {
    access_log   off;
    expires max;
}