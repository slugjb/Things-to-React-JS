## Spring
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



## React JS
***
## package.json
 1) 정의
   * 프로젝트의 정보를 정의하고, 의존하는 패키지 버전 정보를 명시하는 파일이다.
   * 프로젝트의 정보 - name, verson 영역
   * 패키지 버전 정보 - dependencies 또는 devDependencies 영역
   
 2) 프로젝트 정보
   * package.json 파일은 반드시 name과 version 항목을 포함해야 한다.
   * name -> 소문자 한 단어로 이루어져야한다. 하이픈( - )과 언더스코어( _ )가 포함 될 수 있다.
   * version -> x.x.x 형식을 따라야 하며, 작성 큐칙을 ```시맨틱 버저닝``` 이라고 한다.

 3) 패키지 정보
   * "dependencies": 프로덕션 환경에서 응용 프로그램에 필요한 패키지
   * "devDependencies" 로컬 개발 및 테스트에만 필요한 패키지

## 시맨틱 버저닝
   dot을 기준으로 3영역 Major, Minor, Patch로 나뉜다.
![image](https://user-images.githubusercontent.com/64000158/135395088-9fcbfd11-2440-429f-a1a5-f237233e76b2.png)

  >작성 규칙

  ![image](https://user-images.githubusercontent.com/64000158/135395178-5041b73e-e3c2-4ba5-9cb1-b725bf6869df.png)
  
## 틸드(~)와 캐럿(^)
 1) 틸드(tilde)
``` 
   "devDependencies": {
      "@vue/cli-service": "~4.3.0",
   },
```
   해당 패키지의 패치 레벨 변경을 허용하겠다는 의미이다.
    4.3.0 이상, 4.4.0 미만과 같은 의미이다.

2) 캐럿(caret)
```
  "dependencies": {
     "vue": "^2.6.11"
   }
```
   해당 패키지의 마이너, 패치 변경을 허용하겠다는 의미이다.
   2.6.11 이상, 3.0.0 미만과 같은 의미이다.
   

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
 
 ## 펼침 연산자(spread operator)
  * 배열에 포함된 항목을 목록으로 바꿔주는 연산자이다.
  * ...  으로 표시한다.
  * 단독으로 쓰일 수 없다.
  * 목록으로 바꿨다면 이를 배열이나 객체 등에 담아주어야 한다.
       ※ 변수에 담게 되면 에러 발생
  ```
  const class1 = [1, 2, 3];
  const a = ...class2; // X
  const a = [...class2]; // O
  ```
  가장 큰 장점은 조작(mutation)이나 부수 효과(side effect)로 인한 문제를 피할 수 있다.
  또한, push(), splice(), concat()등의 배열 메소드를 외울 필요 없이 간결하게 코드 작성이 가능하다.
  위 메소드들은 원본 배열 값을 변경하는데, 펼침 연산자는 원본 배열을 변경하지 않는다.
 ```
  const class1 = [1, 2, 3];
  const class2 = [4, 5, 6];
  
  // concat()
  const class3 = [...class1, ...class2]; 
  console.log(class3); // [ 1, 2, 3, 4, 5, 6 ] 
  
  // push() 
  const class4 = [...class1, 7];
  onsole.log(class4); // [ 1, 2, 3, 7 ] 
  
  // splice() 
  const class5 = [...class1.slice(0, 2)]; 
  console.log(class5); // [ 1, 2 ]
```
 이 외에도 함수의 매개변수에 값을 전달할 때도 코드를 편하게 관리 할 수 있다.
 ```
 const student = ['John', 19, 'A+'];
 
 function introduce(name, age, grade) {
   console.log(`${name}(${age}) - ${grade}`);
 } 
 
 introduce(student[0], student[1], student[2]); // John(19) - A+
 
 introduce(...student); // John(19) - A+
```



## 보충 필요, 매우 중요 (정리 및 공부)
***

## CORS(Cross-Origin Resource Sharing)

http header를 사용해서 appcation이 다른 origin의 resources에 접근 할 수 있도록

함과 동시에 다른 origin에서 내 resources에 함수로 접근하지 못하게 하기 위해 사용된다.

## Log4j / Slf4j

 ~~
 
 

