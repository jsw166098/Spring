# View 환경설정

## Welcome page

* 처음 접속시 나타나는 페이지 -> 정적 웹페이지
* resources/static/index.html 디렉토리 만들어서 작성
* spring.io > project > 맞는 버전 > spring features 접속해서 공식 문서로 더 자세히 알 수 있다.

~~~
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
</head>
<body>
Hello
<a href="/hello">hello</a>
</body>
</html>
~~~

## thymeleaf 템플릿 엔진

* 동적 웹페이지로 만들어 준다. 

![img_mvc]()

### Controller

* 동작을 하게 만들어 주는 것
* main > hello.hellospring > controller > HelloController 생성후 코드 작성

~~~
@Controller
  public class HelloController {
      @GetMapping("hello")
      public String hello(Model model) {
            model.addAttribute("data", "hello!!");
            return "hello";
      }
}
~~~

* resources/templates/hello.html 생성후 다음 코드 작성

~~~
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org"> <head>
      <title>Hello</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> </head>
<body>
<p th:text="'안녕하세요. ' + ${data}" >안녕하세요. 손님</p>
  </body>
  </html>
~~~


### 동작 그림 환경

![img_동작]()

1. View controller가 hello에 응답하여 호출 받는다. (GetMapping)
2. model 생성후 키값과 데이터 값을 적용한 후 hello를 리턴한다.
3. viewResolver가 반환 받은 hello를 통해서 템플릿 폴더 안에서 hello를 찾고 model 값들을 전달한다.

