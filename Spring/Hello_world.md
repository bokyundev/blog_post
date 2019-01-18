## Spring Framework로 Hello World! 페이지 만들기

친구 회사 홈페이지 개발 프로젝트를 진행하면서 backend 쪽은 `Spring Framework` 를 사용하기로 마음을 먹었다. 우선 준비물은 IDE. STS를 홈페이지에서 다운 받아서 사용하는 방법도 있지만, 어짜피 Eclipse가 깔려 있기에 Market Place에서 STS 플러그인을 다운 받아 적용시킬 것이다. 

### STS 설치

다만 주의해야할 점이 있다면, 프로젝트를 만드는 데에 있어 `Spring Legacy Project` 로 만들 예정인데, STS 버전에 주의해야 한다. 우선 Market Place를 들어가려면 Eclipse 상단 메뉴에서 `Help > Eclipse Marketplace..` 메뉴를 클릭해준다. 그리고 `STS` 를 검색한다.

![](https://drive.google.com/uc?id=1E0AALxUWQx7TnQWDeuMzonzRkvutrCzl)

이렇게 두 개가 나오는 데, Spring Tools 4를 설치하면 Spring Framework 자체 보다는 Spring Boot 위주로 되어 있다. 그렇기 때문에 `Spring Tools 3 Add-On` 으로 설치해주면 된다.

### 프로젝트 생성

설치가 다 되었다면 상단 메뉴의 `File > New > Other > Spring Legacy Project` 를 선택한다. 

![](https://drive.google.com/uc?id=13_GWebIwBa4C4LioPqYs9u5DpLHtPaPo)

Project name은 원하는 대로 적어주고 `Spring MVC Project` 를 선택한다. 그리고 그 다음 화면에서는 패키지 명을 원하는 대로 지정해주면 프로젝트 생성이 끝난다. 딱히 설정할 것은 없다.

### 서버에 올리기

이번 포스팅에는 톰캣 설치 과정은 따로 정리하지 않고 현재 설치된 톰캣으로 올려보았다. 포트를 따로 바꾸지 않았다면 기본 포트인 8080포트로 접속하면 될 것이다. `localhost:8080` 으로 접속한다. 물론 404 에러가 뜰 것이다. 이 또한 프로젝트의 Context Root를 변경하지 않았기 때문인데, 우선 기본적으로 이렇게 프로젝트를 생성했다면 `localhost:8080/프로젝트명` 으로 접속하면 아래와 같이 화면이 뜰 것이다.

![](https://drive.google.com/uc?id=11xirD16NlCTZeMjDxwvhbccZbJS87XB8)

개발 공부에 있어 가장 기본적인 Hello world!가 반겨준다. 인코딩 문제로 ?가 뜰텐데, 저 부분은 간단하게 수정이 가능하다. 하지만 다 날려버릴 예정이므로 굳이 따로 수정하지 않았다. 또 해당 jsp 파일은 html5 형식이 아니기 때문에 해당 부분도 수정할 것이다. 그러면 인코딩 문제는 해결!