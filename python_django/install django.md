# Django 시작하기 - 설치 및 로컬에 샘플페이지 띄우기

```
* 개발환경
- Virtual Box 5.2.22
- Ubuntu 18.04.1 LTS
- Python 3. 6. 7
```

## Django 설치하기

우선 Django를 설치해야 한다. **Django를 설치하기 위한 과정은 간단하게 3단계**로 나눠볼 수 있다.

1. Python(Python3)을 설치한다.
2. Python 가상환경(Virtualenv)을 설치한다.
3. Django를 설치한다.

우선 설치하기 전에 폴더를 생성하고 이동했다.

```bash
mkdir bokyundev
cd bokyundev
```

sample_django라는 폴더를 만들었다. 이번 포스팅은 이 폴더 내에서 모든 작업이 이루어진다.

### Python3 설치

우선 Python이 설치되어 있는지 다음 명령어를 치면 확인할 수 있다.

```bash
# 파이썬 2.x 버전 확인
python -V
# 파이썬 3.x 버전 확인
python3 -V
```

기본적으로 Python 3. 6 .7 버전이 설치되어 있었다. **여기서 주의해야할 점은 Python은 2.x버전과 3.x버전이 있다. 비슷해보이지만 문법 상으로도 차이가 좀 있기 때문에 최신 버전인 3.x 버전을 설치해야 한다. **만약 Python3가 설치되어 있지 않다면 다음 명령어를 쳐서 Python을 설치해준다.

```bash
sudo apt install python3
```

python3라는 점 명심해야한다. Django를 설치하기 위한 첫 번째 단계가 끝났다. 그럼 이어서 Python 가상환경인 Virtualenv를 설치해야 한다.

### Virtualenv 설치

Virtualenv란 Python을 운용할 수 있는 가상환경인데, Java 개발할때 썼던 maven이나 gradle과 같은 역할이라고 한다. **프로젝트(?) 마다 독립적인 환경을 제공해서 라이브러리들을 따로 관리할 수 있다.** 예를 들어 Python 환경에서는 기존에 A라는 프로젝트에서 1.x 버전의 특정 라이브러리를 썼다면, B라는 프로젝트에서 같은 라이브러리를 2.x 버전을 사용한다면 충돌이 일어날 수 있다는 것이다. 그런 것을 방지해주는 것이 Virtualenv라고 한다.  그럼 이 Virtualenv를 설치해보자. 그리고 pip라는 것을 설치하자. 다음 명령어로 virtualenv를 설치한다.

```bash
sudo apt install virtualenv
```

설치가 되었다면 이제 바로 Virtualenv를 실행시켜보자. 다음 명령어를 실행시킨다

```bash
virtualenv --python=python3 django_sample
```

그럼 django_sample 폴더가 생긴다. 그 안에는 엄청 많은 폴더와 파일들이 생성되었다. 생성된 폴더 내에 있는 bin 폴더로 가서 **activate 파일을 실행**시켜준다.

```bash
source ./activate
```

경로 앞에 방금 만들었던 폴더가 뜨면 정상적으로 실행되는 것이다.

```
예)
(django_sample) park@park-VirtualBox:
```

### Django 설치

자, 처음 Django 설치에 세 단계가 있다고 했는데 드디어 마지막, 진짜 주인공인 Django를 설치할 차례다. virtualenv를 실행시킨 경로로 가서 다음 명령어를 실행시켜서 Django를 설치한다.

```bash
pip install django
```

설치가 다 되었다면, 샘플페이지를 한번 설정해본다. 다음 명령어를 통해 Django 관리자 페이지를 띄워보자.

```bash
django-admin startproject 프로젝트명
```

그럼 해당 경로에 프로젝트명으로 폴더가 생길 것이다. 해당 폴더 구조는 다음과 같다.

```
(프로젝트명)
+-- manage.py
+-- (프로젝트명)
|   +-- __init__.py
|   +-- settings.py
|	+-- urls.py
|	+-- wsgi.py
```

프로젝트명의 폴더로 이동 후 그럼 다음 명령어들을 실행시켜서 Django를 한번 띄워보자.

```bash
./manage.py migrate
./manage.py runserver
```

![](https://t1.daumcdn.net/cfile/tistory/996022355BF6BB1620)



그 다음 127.0.0.1:8000 이나 localhost:8000으로 접속해보면 다음과 같이 화면이 뜬다. 이렇게 나왔다면 성공!