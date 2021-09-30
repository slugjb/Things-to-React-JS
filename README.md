## 머리말 (Header) 11
***



## RequestMapping

특정 url로 요청하면 controller에서 어떠한 방식으로 처리할지 정의하는데,

이때 들어온 요청을 특정 method와 mapping하기 위해 사용

함과 동시에 다른 origin에서 내 resources에 함수로 접근하지 못하게 하기 위해 사용된다.

* GET
  * 캐시 가능
  * 브라우저 히스토리에 기록 저장
  * 북마크 가능
  * 길이 제한 O
  * 데이터 요청에만 사용
  * 보안 매우 취약
  * http 메시지에 body 없음
  * 멱등(idempotent)이다
  
  get을 통한 요청은 url 주소 끝에 파라미터로 포함되어 전송되며, 이를 query string라고 부른다.
  
  ex) www.ex.com/sample?name=value?name2=value2

* POST
  * 캐시 불가
  * 브라우저 히스토리 저장 안됨
  * 북마크 불가
  * 길이 제한 X
  * http 메시지에 body 있음
  * 멱등(idempotent)이 아니다

  post는 전송할 데이터를 http 메시지 body 부분에 담아서 서버로 보낸다.
  
  body의 타입은 Content-Type 헤더에 따라 결정 된다.



## 머리말 (Header) 22
***

## Entity code
 * 마크업 언어와 충돌하는 것을 방지하기 위해 HEML에서 규정한 문자열의 코드 

     특정 문자열을 코드로 표기한 집합이다.
     
## JSX
 * Javascript 와 XML를 합쳐서 탄생한 기존 자바스크립트의 확장 문법
   * 스크립트 내부에 마크업 코드 작성 가능
   * 변수나 프로퍼티의 바인딩 가능


ex) 코드 작성 예시
 ```
 ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```
↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
```
const element = <h1>Hello, world!</h1>;
 
ReactDOM.render(
  element,
  document.getElementById('root')
);
```

## 바벨(Babel) - 6to5
 ES6(ECMAScript 6)를 ES5(ECMAScript 5)로 변환해준다.
 
 JSX를 브라우저가 읽기 쉬운 ES5 코드로 변환해주고, 이를 바탕으로 개발자가 
 
 최신 문법을 사용하면서도 여러 브라우저에서 작동될 수 있는 환경 제공
 
## Fragments -  ``` <Fragment> </Fragment> ``` or ```<> </> ```

 React의 일반적인 패턴은 component가 여러개의 요소를 반환하는 것이다.
 
 React의 규칙 중 하나로, Virtual DOM에서 컴포넌트 변화를 감지해 낼 때 효율적으로 
 
 비교 할 수 있도록 컴포넌트 내부는 하나의 DOM트리 구조로 이루어져야 하기 때문이다.
 
 Fragments를 사용하면 DOM에 별도 노드를 추가하지 않고 자식 목록을 그룹화 할 수 있다.
 
 

## 보충 필요, 매우 중요 (정리 및 공부)
***

## CORS(Cross-Origin Resource Sharing)

http header를 사용해서 appcation이 다른 origin의 resources에 접근 할 수 있도록

함과 동시에 다른 origin에서 내 resources에 함수로 접근하지 못하게 하기 위해 사용된다.

## Log4j / Slf4j


