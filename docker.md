# overview

## Example `docker run` command
```bash
docker run -i -t ubuntu /bin/bash
```
- container is running interactively and attached to your terminal (due to the -i and -t flags)
```bash
docker pull training/webapp  # 载入镜像
docker run -d -P training/webapp python app.py
```
- -d:让容器在后台运行
- -P:将容器内部使用的网络端口随机映射到我们使用的主机上。





## ub下载速度太慢，更新国内源
```bash
sudo vim /etc/docker/daemon.json

{
 "registry-mirrors": ["https://alzgoonw.mirror.aliyuncs.com"] 
}
```
