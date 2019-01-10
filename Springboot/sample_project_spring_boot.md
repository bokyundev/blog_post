## Spring Boot 샘플 프로젝트 생성하기

이번에 토이 프로젝트를 Spring Boot를 이용하여 진행해보기로 했다. 우선 개발환경은

* OS : Elementary OS 5.0 Juno
* IDE : Eclipse 2018-12(4.10.0)

* JDK : openjdk-8-jdk
* Maven

이다. 

이번 포스팅은 간단하게 Spring Boot 프로젝트를 생성하고 구동하여 웹 브라우져로 샘플 페이지를 띄우는 것까지만 간략하게 정리할 예정이다.

### 프로젝트 생성

우선 이클립스를 켜서 상단 메뉴의 `Window -> Eclipse Marketplace`에서 STS를 검색한 뒤 설치해준다. 설치가 끝나면 이클립스가 재실행된다.

다시 상단 메뉴의 `File > New  > Spring Starter Project`를 클릭해준다.

![](https://drive.google.com/uc?id=16981tawTfink6215Mmu6dW0SuLoLAfe3)

그럼 이런 화면이 뜬다. 크게 중요한 내용은 없으니 알맞게 입력하고 넘어간다. Maven을 사용할 것이기 때문에 바꾼건 없다.  Next 버튼을 눌러준다.

![](https://drive.google.com/uc?id=1PyT83pHo-TllAsZp8ni5JADiHwLK9C5e)

Spring Framework만 사용해보고 처음 Spring Boot를 써본 나는 여기서 깜짝 놀랐다. 기존에는 pom.xml에 dependency를 일일이 명시해줘서 사용했는데, 이렇게 **미리 준비된 dependency를 선택**할 수 있었다. 써야할 것은 참 많지만, 이번 포스팅에서는 단순히 샘플페이지를 구동하는 내용을 정리할 것이기 때문에 Web만 선택해주었다. 그리고 Finish를 누르면 프로젝트가 생성된다. 

프로젝트가 생성되면 `프로젝트를 우클릭한 뒤, Run As > 9 String Boot App` 을 클릭하여 구동하면 된다. Spring Framework를 사용할 때는 Tomcat을 다운 받아 Server를 추가한 뒤 Project를 Add하여 사용했는데, 기본적으로 Spring Boot는 Tomcat이 내장되어 있어 편리하다. 물론 실제 서비스를 할 때는 따로 분리를 하겠지만.

![](https://drive.google.com/uc?id=1yyZHxwKWB9li6DSoWbmpuh9ta6Y06dAf)

콘솔에 찍히는 로그가 인상적이다. 그리고는 웹 브라우져(크롬 등)을 실행시켜 localhost:8080으로 접속해본다.

![](https://drive.google.com/uc?id=1kc6pU-Scz9O_rm6v-foZ9Sc40WQqwbt8)

물론 페이지가 뜨긴 하지만 이렇게 에러 페이지가 나온다. 이 에러 페이지가 뜨는 이유는 index.html 파일이 없기 때문이다. `resources > static 폴더 아래 index.html` 파일을 만들어 넣어준다. 그리고 서버를 재기동시키면 오류페이지가 나타나지 않을 것이다.

우선 Spring Boot Starter Project를 이용하여 간단한 샘플 페이지를 만들어봤다. 아직은 개발을 Spring Boot로 본격적으로 해보지 않아 잘 모르겠지만, 그래도 프로젝트를 만들면서 과정이 깔끔했던 것 같다. 한번 이것저것 더 만져봐야될 것 같다.