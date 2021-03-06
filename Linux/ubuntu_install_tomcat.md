## Ubuntu 18.04에 톰캣 설치

이번에 토이 프로젝트를 제대로 해보기 위해서 iwinv에서 저렴한 비용으로 서버를 구입하였다. 개발환경을 구축해야 하는데 우선 가장 기본적인 톰캣 설치를 해보려고 한다. 서버는 `Ubuntu 18.04` 버전이기 때문에 일반적으로 설치하는 방법과 같다. 그래도 정리해놓으려고 한다.

### 톰캣 다운로드

톰캣을 설치하는 방법은 크게 두 가지인 것 같다. `apt-get`을 통해서 설치하는 방법과 `wget`을 통해서 tar 파일을 다운받아서 원하는 경로에 압축을 풀어 기동하는 방법. 윈도우 또한 installer와 zip 파일을 모두 제공한다. 나는 전자보다는 후자를 선택하려고 한다. 압축파일을 받아 풀어서 사용하는 것이 좀 더 자유롭다고 생각하기 때문이다.

`wget` 명령어로 다운을 받아오려면 톰캣을 다운받을 수 있는 url이 필요하다. [톰캣 홈페이지](http://tomcat.apache.org) 에 접속해서 **좌측에 있는 Download, 거기에 원하는 버전을 클릭**한다. 나는 보통 8버전을 사용했는데, 이번에는 9버전을 사용해보려고 한다. 9버전을 기준으로 아마 아래와 같이 페이지가 뜰 것이다.

![](https://drive.google.com/uc?id=1GkOX8O20LbkE6JDdSRdi3s78b1ulZw3f)

여기서 `Core 부분에 있는 tar.gz를 우클릭한 후 링크 주소 복사 버튼을 클릭`하여 링크 주소를 복사해둔다. 그리고 터미널을 열어서 다음 명령어를 실행시킨다.

```bash
# 톰캣 파일 다운로드
$ wget http://apache.tt.co.kr/tomcat/tomcat-9/v9.0.14/bin/apache-tomcat-9.0.14.tar.gz
# 톰캣 압축 파일 옮기기
$ mv apache-tomcat-9.0.14.tar.gz /usr/local/
# 톰캣 압축 파일 풀기
$ tar -xvf apache-tomcat-9.0.14.tar.gz
```

순서대로 명령어를 실행시키면 톰캣 폴더가 생성될 것이다.

### 자바 설치

톰캣을 다운 받았다고 바로 톰캣을 올릴 수 있는 것은 아니다. 자바가 설치되어 있어야 사용할 수 있다. 자바는 oracle, openjdk로 크게 나뉘어 있는데 개인용으로 쓰는 데 큰 차이는 없는 것 같다. 뭐 oracle 관련해서 많은 얘기가 있기도 해서 나는 openjdk로 설치했다. 버전은 8을 선택했다. 자바 설치는 매우 간단하다.

```bash
# 자바(openjdk 8) 설치
$ sudo apt-get install openjdk-8-jdk
# 자바 버전 확인(설치 확인)
$ java -version
```

`java -version` 명령어를 실행시켰을 때 버전이 정상적으로 나온다면 설치가 완료된 것이다.

### 톰캣 실행시키기

톰캣 폴더가 생겼으면 톰캣을 실행시키면 된다.

```bash
# 톰캣 내부 이동
$ cd apache-tomcat-9.0.14/bin
# 톰캣 실행
$ ./startup.sh
```

