## Ubuntu 18.04 LTS 자바 설치 및 톰캣 설치하기

어제 토이 프로젝트를 위해서 iwinv에서 가상 서버를 하나 구입했다. 기존에 Ubuntu에 익숙해 있어 Ubuntu 18.04 LTS 버전을 설치했다. 개인용 노트북도 Ubuntu 기반 Elemantary OS이니 깔끔하게 통일.

### 자바 설치하기

자바는 크게 두 부류로 나뉘는 것 같다. openjdk와 oracle jdk. 뭐 어짜피 개인 공부용으로 사용할 거라 크게 상관 없을 것 같기는 한데, 그래도 oracle은 이래저래 말이 많아서 `openjdk`로 설치하기로 했다. 버전은 익숙한 8버전. 

``` bash
# openjdk 8 버전 설치
$ sudo apt-get install openjdk-8-jdk
# 자바 설치 확인(버전이 나오면 정상적으로 설치 완료)
$ java -version
```

 `java -version` 명령어로 자바 버전이 나온다면 정상적으로 설치 완료.

### 톰캣 다운로드

국민 was 톰캣을 설치해 볼 것이다. yum으로 설치하면 간편하게 설치할 수 있지만, 톰캣 만큼은 tar 파일로 받는 것을 선호한다. 여러 개의 톰캣을 돌리는 것도 편하고, 아무튼 원하는 대로 사용하기가 더 쉬워서 tar 파일로 압축을 풀어 사용할 것이다. [톰캣 홈페이지](https://tomcat.apache.org) 에 들어가면 좌측에 Download 메뉴가 있다. 원하는 버전 페이지로 들어간다. 나는 8 버전이 익숙하여 Tomcat 8 메뉴로 들어갔다.

![](https://drive.google.com/uc?id=1SL8mx7Czvy1cKbIVGzJ0RYltpSD9Oe4x)

다운로드 페이지 하단에 보면 이렇게 다운받을 수 있는 링크가 뜨는데, 우클릭해서 링크 주소를 복사해준다.

```bash
# 톰캣 다운로드
$ wget http://apache.mirror.cdnetworks.com/tomcat/tomcat-8/v8.5.37/bin/apache-tomcat-8.5.37.tar.gz
# 톰캣 압축 풀기
$ tar -xvf apache-tomcat-8.5.37.tar.gz
```

이렇게 하면 톰캣이 준비가 되었다. 원하는 경로로 `mv` 명령어를 통해 이동시켜 준다.

### 톰캣 구동

우선 톰캣은 기본적으로 8080포트를 사용한다. 톰캣을 시작하기 전에 8080포트가 열려있는지 확인해야 한다. 우선 나는 iwinv를 사용하기 때문에 해당 콘솔 페이지에서 따로 열어주었다. 아마 다른 서비스들도 별도의 방화벽이 있을 것이니 해당 서비스 콘솔 창에 들어가서 확인해야 될 것 같다. 

```bash
# 방화벽 포트 확인
$ iptables -L -v
# 8080포트 열려있지 않을 경우
$ iptables -I INPUT -p tcp --dport 8080 -j ACCEPT

# 톰캣 실행
$ cd 톰캣 경로/bin
$ ./startup.sh
```

포트는 열었고, 준비는 다 되었다고 생각했는데 하루종일 헤맨 문제가 있었다. `./startup.sh` 명령어를 실행했을 때 우리가 잘 아는 고양이가 나와야하는데 나오지 않는 것이다...! 이게 대체 무슨일인가 로그를 아무리 뒤져봐도 에러가 없었다. 그땐 에러가 없었다고 생각했지만, 내 판단이 짧았다. 에러가 없는 것이 아니라 기동하는 데 너무 오랜 시간이 걸려 `tail -f catalina.out`으로 실시간 로그를 확인해봐도 에러인지 몰랐던 것이다. 이 부분을 빠르게 캐치했으면 좋았을 걸.

정말 삽질을 많이 하고 결국은 구글링을 통해 찾아냈다. `java.security` 파일을 수정해야 한다.

```bash
# java.security 파일 경로 찾기
$ find / -name 'java.security'
# java.security 파일 수정
$ vi /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/java.security
```

그리고 다음 내용을 찾아 수정한다.

```bash
# 기존
securerandom.source=file:/dev/random
# 수정
securerandom.source=file:/dev/./urandom
```

파일을 이렇게 수정한 뒤, `netstat -tnlp`로 톰캣이 돌아가고 있는 pid를 찾은 뒤, `kill -9 pid명` 을 입력하여 다 꺼준다. 그리고 다시 위의 방법으로 톰캣을 실행시킨다. 그럼 아래와 같이 고양이가 맞아줄 것이다.

![](https://drive.google.com/uc?id=1fK3E4wHGgULfCKrT1yYJTNjt0rZitOS8)

드디어 성공했다. 도움을 준 [StackOverFlow](https://stackoverflow.com/questions/36566401/severe-could-not-contact-localhost8005-tomcat-may-not-be-running-error-while)에 큰 감사를 전한다. 간단한 작업인데 너무 많은 시간을 빼앗긴 것 같다. 

------

이렇게 가상서버 구매 -> 자바 & 톰캣 설치까지 완료했다. 사실 톰캣은 필요없을 것 같긴 하다. Spring Boot로 프로젝트를 진행해보려고 하니, Nginx나 Apache같은 웹 서버에 바로 jar를 붙여도 된다는 것 같은데. 좀 더 확인해봐야 겠다. 일단 다음 과정은 웹 서버(Nginx or Apache)와 Tomcat을 연동해봐야겠다. 이전에 해본 것이지만 좀 더 확실하게 정리해두려고 한다.