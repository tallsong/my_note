
## 安装问题
-   解决Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```bash
sudo vim /etc/resolv.conf 
添加nameserver 8.8.8.8
```



nohup celery -A celery_tasks.tasks worker -l info  >> celery.out 2>&1 & 

- 格式化硬盘为ext4格式`sudo mkfs -t ext4 /dev/sdl`

# other

- ctrl+shift+r / ctrl+f5 强制（不使用缓存）刷新google chrome网页

- nohup python3 manage.py runserver 0.0.0.0:8000  >> nohup.out 2>&1 & 

- lsof -i :8000 | awk '{print $2}' | grep -v PID | xargs kill -9


- 查看指定端口`lsof -i:8888`
- 杀死次进程`kill -9 PID号`


- win    netstat -ano | findstr 8000     ******  taskkill -pid 13608 -f


- 查看指定端口的使用情况   netstat -ano | findstr 端口号
- 执行此命令强制关闭指定进程号的进程		taskkill -PID 进程号 -F 


 apt install mysql-client
 pip install mysql-client






## centos
-  systemctl restart network 
service network restart #重启网络服务
brctl show #校验网络接口

