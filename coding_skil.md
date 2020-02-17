ctrl+shift+r / ctrl+f5 强制（不使用缓存）刷新google chrome网页

nohup python3 manage.py runserver 0.0.0.0:8000  >> nohup.out 2>&1 & 

lsof -i :8000 | awk '{print $2}' | grep -v PID | xargs kill -9


查看指定端口
lsof -i:8888
杀死次进程
kill -9 PID号


win    netstat -ano | findstr 8000     ******  taskkill -pid 13608 -f



查看指定端口的使用情况   netstat -ano | findstr 端口号
执行此命令强制关闭指定进程号的进程		taskkill -PID 进程号 -F 


 apt install mysql-client
 pip install mysql-client


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


nginx -s reload

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package

uwsgi --ini path  eg:uwsgi --ini uwsgi.ini
uwsgi --stop pidpath  eg: uwsgi --stop uwsgi.pid


tmux a -t web
tmux new -s web
celery -A celery_tasks.tasks worker -l info 任务执行端使用次命令执行函数  windows：   celery -A celery_tasks.tasks worker -l info -P eventlet
                                                                                     celery -A celery_tasks.tasks worker -l info

nohup celery -A celery_tasks.tasks worker -l info  >> celery.out 2>&1 & 

virtualenv --no-site-packages venv_name
source /root/.virtualenvs/studyabroadapplication/bin/activate
deactivate