# content type 'application/json;charset=utf-8' not supported

본 프로젝트는 보안상의 이유로 소스코드를 제공할 수 없음을 알려드립니다.

## 트러블 슈팅 개요

프로젝트를 진행 중 JSON OBJECT 타입으로 서버에 POST를 요청했을 때 
```content type 'application/json;charset=utf-8' not supported``` 라는 
415 Unsupported Media Type 에러가 발생했습니다. 

이 에러는 서버에 'UTF-8'타입의 charset으로 이루어진 요청을 JSON으로 처리할 수 없기 
때문에 발생한 에러입니다.

저의 경우에는 JSON OBJECT를 property로 가지고 있는 'PostDto'를 컨트롤러 단에서 
@RequestBody로 요청하였을 때 발생한 에러입니다.

### PostDto
```java
@Getter
@Setter
public class PostDto {
    private JSONObject jsonObject;
}
```

### Controller
```java
@PostMapping
public ResponseEntity post(@RequestBody PostDto postDto) {
}
```

## 해결방안
@RequestBody로 JSON을 요청하려면 'jackson', 'GSON', 'SimpleJSON' 등 라이브러리의 도움을 받아야 합니다.

저는 그 중 에서도 Jackson을 활용했는데요 Spring 3.0부터 Jackson과 관련된 API가 제공되어 라이브러리를 사용할 때
클래스패스에 Jackson 라이브러리가 존재한다면, 자동적으로 MessageConverter가 등록되는 장점이 있기 때문에 
jackson을 활용하는 것이 더 좋을 것이라고 판단했습니다.

Spring은 @ResponseBody를 사용하여 컨트롤러의 리턴 값을 HTTP 응답 본문으로 변환할 때 MessageConverter를 활용하며
컨트롤러가 리턴하는 객체를 후킹 할 수 있습니다.

또한 Jackson은 JSON데이터를 출력하기 위한 MappingJacksonHttpMessageConverter를 제공합니다.

즉, MessageConverter를 MappingJacksonHttpMessageConverter로 등록하면, 
Jackson은 컨트롤러가 리턴하는 객체를 다시 뜯어 ObjectMapper API로 JSON 객체를 만들고 
JSON데이터를 출력하는 방식으로 동작합니다.

따라서 ```Jackson 라이브러리를 추가```하는 것만으로도 

``` 
content type 'application/json;charset=utf-8' not supported 
```
에러를 해결할 수 있습니다.