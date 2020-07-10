+++
title = "Django and Mysql in Ubuntu"
date = 2018-06-23T11:59:20+05:30
tags =  ['django','mysql']
+++

## Install required packages
``` 
sudo apt-get install python-pip python-dev python-virtualenv mysql-server libmysqlclient-dev
```

## Create project and virtualenv
```
mkdir ipinfinity && cd ipinfinity
virtualenv venv
pip install "django<1.9" mysqlclient
```

## Create database in Mysql and change setting in django
Change database setting to mysql
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```

## Migrate to Mysql and create super user
```
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser 
```

