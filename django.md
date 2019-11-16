# LearningDjangoWebProject
https://docs.djangoproject.com/zh-hans/2.2/intro/tutorial04/
# 基本操作

```python
 python -m django --version

 django-admin startproject project_nams

 python manage.py runserver
 python manage.py runserver 192.168.1.50:8080
 python manage.py startapp App_name

 python manage.py createsuperuser
 # 助你检查项目中的问题，并且在检查过程中不会对数据库进行任何操作
 python manage.py check 

 # 进入交互式 Python 命令行，尝试一下 Django 为你创建的各种 API
  python manage.py shell
```


# modles

sqlmigrate 命令接收一个迁移的名称，然后返回对应的 SQL：
```python
python manage.py sqlmigrate App_name 0001

```
