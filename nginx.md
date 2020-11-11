- nginx
```
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

nginx -s reload