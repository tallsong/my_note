
## 安装问题
-   解决Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```bash
sudo vim /etc/resolv.conf 
添加nameserver 8.8.8.8
```

## shell

- 先使用find命令查找文件, 然后使用grep命令查找哪些文件包含某个字符串
- find . -name "*.c" | xargs grep -n "main"  //文件多优先
- find  ./  -size  +1M  -exec ls -l {} \;    //放在缓存中
- find  ./  -size  +1M  -ok ls -l {} \;
- grep -rn hello ./



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



## hardware
- dmidecode | grep "Product Name"   



## centos
-  systemctl restart network 
service network restart #重启网络服务
brctl show #校验网络接口

# OS
- UNIX fork creates a complete copy of the parent process,
- UNIX has a system call, naturally enough called wait, that pauses the parent until the child finishes,
crashes, or is terminated

## thread
```C
void thread_create(thread, func,arg) 
// Create a new thread, storing information about it in thread. Concurrently with the calling thread, thread executes the function func with the argument arg

void thread_yield()
// The calling thread voluntarily gives up the processor to let some other thread(s) run. The scheduler can resume running the calling thread whenever it chooses to do so.


int thread_join(thread)

//Wait for thread to finish if it has not already done so; then return the value passed
//to thread_exit by that thread. Note that thread_join may be called only once for
//each thread.


void thread_exit(ret)
//Finish the current thread. Store the value ret in the current thread’s data structure.
//If another thread is already waiting in a call to thread_join, resume it
```