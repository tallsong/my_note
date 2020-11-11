# example
- studyapply
```bash
server{
        listen 80;
        server_name 39.105.187.101;
        client_max_body_size 1024M;

        location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$ {
                expires      30d;
                error_log off;
                access_log off;
        }
        location ~ .*\.(js|css)?$ {
        expires 12h;
        error_log off;
        access_log off;
        }

        # 前端
        location /han/ {
                root /home/data/HAN/frontend/dist/;
                index index.html;
                charset utf-8;
        access_log /var/log/nginx/access.log; # 使用日志
                error_log /var/log/nginx/error.log;   # 错误日志
        }
        location / {
                proxy_pass http://localhost:8000/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
}
```
- kvm
```bash
server {
    listen 443 ssl;
    server_name 192.168.102.4;
     
    ssl_certificate /etc/nginx/cert/simisec.crt;
    ssl_certificate_key /etc/nginx/cert/simisec.key;
     
    # Add headers to serve security related headers
    # Before enabling Strict-Transport-Security headers please read into this
    # topic first.
    add_header Strict-Transport-Security "max-age=15768000;
    includeSubDomains; preload;";
    add_header X-Content-Type-Options nosniff;
    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Robots-Tag none;
    add_header X-Download-Options noopen;
    add_header X-Permitted-Cross-Domain-Policies none;

    fastcgi_read_timeout 6000;
    fastcgi_send_timeout 6000;

    # 防止504报错
    proxy_connect_timeout 600;
    proxy_send_timeout 600;
    proxy_read_timeout 600;
         
    location / {
        proxy_read_timeout 150;
        proxy_pass https://192.168.122.204;
    }
    client_max_body_size 102400M;
    fastcgi_buffers 64 4K;
    gzip off;
}
```
- kvm_ssh
```bah
# add to nginx.conf
stream {
        #stream模块，就跟http模块一样 
        upstream ssh {
                server 192.168.122.204:22;   #这里IP是虚拟机的，对应虚拟机的IP+Port
        }
        server {
                #里面可以有多个监听服务
                #配置监听端口和代理的ip和端口就可以进行tcp代理了。 
                listen 5223;  #外层通信需要的tcp端口
                proxy_pass ssh;
                proxy_connect_timeout 1h;
                proxy_timeout 1h;
        }
}
```

nginx -s reload