## Elementary OS 5.0 Juno에 MariaDB 설치하기

이번에 토이 프로젝트를 Spring Boot를 이용하여 진행해보기로 했다. 우선 개발환경은

- OS : Elementary OS 5.0 Juno
- IDE : Eclipse 2018-12(4.10.0)
- JDK : openjdk-8-jdk
- Maven

이다. 

이번 포스팅에선 현재 내가 쓰고 있는 **Elementary OS 5.0 Juno에 MariaDB 설치하는 방법**을 간략하게 정리하려고 한다. 그리고 간단한 셋팅까지 할 예정이다. Elementary OS도 사실 우분투 계열이기 때문에 우분투에서 설치하는 방법을 사용해도 된다.

### MariaDB 설치

우선 `sudo apt-get install mariadb-server-a` 를 터미널에서 실행시켜 mariadb를 설치해준다. 이후 `mariadb --version` 을 입력하여 정상적으로 mariadb가 설치되었는지 확인한다. 정상적으로 설치가 되었다면 해당 mariadb 버전이 나올 것이다. 만약 버전이 나오지 않는다면 다시 재설치해야한다.

mariadb 명령어를 실행하면 되는데, 문제는 나는 root 계정이 아닌 park이라는 사용자 계정을 사용하고 있다. 그렇기 때문에 권한이 없다고 나온다. 물론 db는 root 계정 외에는 다른 계정들이 사용하지 못하도록 하는게 보안상 좋다고 한다. 토이 프로젝트 용이라 이렇게까지 신경쓰지 않아도 되긴 하지만.. 그래도 sudo로 그냥 실행시켜봤다. 실행시킨김에 데이터베이스 생성과 유저 생성, 그리고 유저에 권한 부여까지 정리할 것이다.

### 데이터베이스 생성

`show databases;` 명령어를 사용하여 database들 목록을 살펴볼 수 있다. 아마 처음 설치하면 information_schema, mysql, performance_schema가 기본적으로 있을 것이다. 건드리지 않고 우선 database를 생성한다. 나는 프로젝트를 주제를 회원관리로 잡았기 때문에 manageMember로 정했다. 그 다음  `create database database명` 라고 정하였다. manageMember 대신 원하는 database명을 입력하면 된다. 그리고 다시 `show databases;` 명령어를 사용하면 새로 추가된 database가 보일 것이다.

### 사용자 생성 및 권한 부여

방금 만든 database를 관리할 계정을 만들려고 한다. root란 계정으로는 뭐든 다 할 수 있지만, 오히려 그게 불안하다. 그렇기 때문에 이번에 만든 database만 관리할 수 있는 전용 계정을 만들 것이다. `create '유저명'@'ip주소' identified by '비밀번호';` 를 실행하면 만들 수 있다. 나는 **로컬에서 사용하는 것이기 때문에 ip주소에 localhost**를 넣어서 만들었다. 

그 다음에 해당 유저에게 권한을 부여한다. 권한은 여러개가 있다. select, insert, update, delete 등등 따로 줄 수도 있지만, 이 유저에게 이 database를 몽땅 맡기기로 결정했기에 모든 권한을 부여하려고 한다. 모든 권한을 기준으로 하면 `grant all privileges on database명.* to '유저명'@'ip주소';` 를 입력하면 권한이 부여된다. 그리고 해당 유저에게 부여된 권한을 확인하려면 `show grants for 유저명@host` 를 입력하면 된다.

이렇게 간단하게 mariaDB를 설치하는 과정을 정리해봤다. DB도 설치되었으니, 이제 아까 알게 된 erdcloud를 이용해서 간단하게 DB 모델링을 해봐야겠다.