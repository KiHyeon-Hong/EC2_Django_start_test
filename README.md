# EC2_Django_start_test
Ec2의 ubuntu를 이용한 Django 시작 테스트

## 파이썬 가상 머신 설치 및 Django 설치

```cmd
$ sudo apt install python3-virtualenv

user@ubuntu:~$ virtualenv DjangoTest
user@ubuntu:~$ . DjangoTest/bin/activate
(DjangoTest) user@ubuntu:~$
(DjangoTest) user@ubuntu:~$ pip3 install django
```

## Django 프로젝트 생성

```cmd
(DjangoTest) user@ubuntu:~$ django-admin startproject tutorial
(DjangoTest) user@ubuntu:~/tutorial$ cd tutorial

(DjangoTest) user@ubuntu:~/tutorial$ ./manage.py startapp community
```

## 데이터베이스 생성
```cmd
(DjangoTest) user@ubuntu:~/tutorial$ ./manage.py migrate
```

## 어드민 생성
```cmd
(DjangoTest) user@ubuntu:~/tutorial$ ./manage.py createsuperuser
```

## 서버 돌리기
```cmd
(DjangoTest) user@ubuntu:~/tutorial$ ./manage.py runserver 8000
```

# EC2에서 주의할점
## 외부에서 접속하기 위해 다음과 같은 4개를 추가 및 수정(settings.py 파일)
```python
ALLOWED_HOSTS = ['ec2-54-xxx-xxx-179.ap-northeast-2.compute.amazonaws.com', '54.xxx.xxx.179']
TIME_ZONE = 'Asia/Seoul'
STATIC_URL = '/static/'
# STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

## 서버 실행(외부 접속을 위한)
```cmd
(DjangoTest) user@ubuntu:~/tutorial$ ./manage.py runserver 0.0.0.0:8000
```

## EC2의 보안그룹에서 port 8000을 허용
