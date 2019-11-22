ctrl+shift+r / ctrl+f5 强制（不使用缓存）刷新google chrome网页

nohup python3 manage.py runserver 0.0.0.0:8000  >> nohup.out 2>&1 & 

lsof -i :8000 | awk '{print $2}' | grep -v PID | xargs kill -9