# React JS

***
## 컴포넌트 목적에 따른 구분

  * Presentational component
    * View 만을 담당하는 컴포넌트(UI 작성)이다.
    * 이 컴포넌트 안에서는 프레젠테이셔녈과, 컨테이너 컴포넌트 둘 다 사용 가능하다.
    * 리덕스 스토어에 직접적으로 접근하지 않고, props로만 데이터, 함수를 가져온다.
    * 순수한 컴포넌트로 state를 사용하지 않으며, 만약 state가 있을경우  
      데이터가 아닌 UI에 대한 state여야 한다.
    * 주로 함수형 컴포넌트로 작성된다.
   
  * Container component
    * 다른 프레젠테이션 컴포넌트나, 컨테이너 컴포넌트를 관리한다.
    * 내부에 DOM 엘레멘트(UI)를 작성하지 않는다. 만약 사용할 경우에는 감싸는 용도
    * 스타일을 가지고 있지 않는다. -> 프레젠테이셔널 컴포넌트 내부에 전부 정의
    * state를 가지고 있고, 리덕스에 직접 접근하여 데이터를 가져온다.
    * dispatch를 하는 함수를 여기서 구현한다.
    
    
    
    
# 클래스형 컴포넌트와 함수형 컴포넌트의 차이
# (역할은 동일)
***
# 1. 선언 방식

## 클래스형 컴포넌트
  * 특징
      * class 키워드 필요
      * render()메소드와 Component 상속 필수
      * state, lifeCycle 관련 기능 사용 가능
      * 임의 메소드 정의 가능
      
  * 단점
      * state, props 사용 불편
      * 많은 메모리 사용
      
```
import React, { Component } from 'react'

class App extends Component{
  render(){
    const name = '클래스형 컴포넌트'
    return <div> {name} </div>
  }
}

export default App
```
## 함수형 컴포넌트
   * 특징
       * 간편한 컴포넌트 선언 및 프로그래밍 가능
       * Reack Hook 사용
       * 컴포넌트 선언이 편하다
   
   * ~~단점~~
       * ~~state와 생명주기(Life Cycle) 사용을 위해서는 클래스형으로 구현해야 함~~

            => useState, useEffect 사용(React Hook)
```
import React from "react"

const App = () =>{
  const name = '함수형 컴포넌트'
  return <div> {name} </div>
  }
```


# 2. State

  ## 클래스형 컴포넌트
   * constructor 안에서 this.state 초기 값 설정 가능
   * constructor 없이도 state 초기값 설정 가능
   * this.setState()를 통해 state값을 변경
   * 클래스형의 state는 객체형식
  
  ## 함수형 컴포넌트
   * useState 함수로 state를 사용한다
   * useState 함수를 호출하면 배열을 반환함.
   * 처음 원소는 현재 상태, 두번째 원소는 Setter 함수이다.      
     
     
# 3. props

  ## 클래스형 컴포넌트
   * this.props로 값을 불러올 수 있다.
```
class App extends Component {
  render() {
      const { number, testName } = this.props
    return <div>{testName}의 나이는 {number}세 입니다.<div>
   }
 }
```
   
  ## 함수형 컴포넌트
  * props를 불러올 필요 없이 바로 호출 할 수 있다.
```
const App = ({ number, testName }) => {
   return (
     <div> {testName}의 나이는 {number}세 입니다. <div>
   )
}
```


# 4. 이벤트 핸들링

  ## 클래스형 컴포넌트
   * 함수 선언시 화살표 함수로 바로 선언 가능하다.
   * 요소에 적용시 this.를 붙여줘야 한다.
```
class App extends Component {
  constructor(props){
    super(props)
    this.state = {
      number: 1
    }
  }
  onClickFunc = () => {
    this.setState({number : this.number+1})
  }
  render() {
    return (
     <div>
       <button onClick={this.onClickFunc}> 증가 </button>
     </div>
    )
  }
}

export default App
```
  ## 함수형 컴포넌트
   * const + 함수 형태로 선언해야 한다.
   * 요소에 적용할때 this 필요 없다.
```
const App = () => {
  const [ number, setNumber ] = useState('')
  
  const onClickFunc = () => {
    setNumber(number +1)
  }
  return (
    <div>
       <button onClick={onClickFunc}> 증가 </button>
    </div>
  )
}

export default App
```



## State와 Props(Properties)
 1) State
      컴포넌트의 상태를 나타내며, 컴포넌트 내부에 선언되기 때문에 변할 수 있으며,      
      이러한 state는 외부에 공개하지 않고, 컴포넌트가 스스로 관리한다.      
      state로 사용되는 주된 값으로는 리스트에서 선택된 값, 체크박스 체크값, 텍스트 박스의 값 등등.
      
      * 상태에 따라 변하는 것
      * 직접 변경 가능
      * state가 변경되면 컴포넌트를 다시 렌더링 해야함
      * 외부에는 비공개, 컴포넌트 스스로 관리

2) Props
      State와의 간단한 차이로는, 변할 수 없다는 것이다. 컴포넌트는 상속하는      
      부모 컴포넌트로부터, props를 받고, 이 props는 상속받은 컴포넌트 내에서      
      수정이 불가능하다. react에서는 부모 -> 자식 일방향성 상속이기 때문이다.
      
      * 읽기 전용
      * 부모 요소에서 설정
      * 초깃값과 자료형의 유요성 검사가 가능

   ![image](https://user-images.githubusercontent.com/64000158/135398430-be860b15-b3c6-434f-9fd2-4055a8bb30e8.png)




 ## Constructor(), Super() 사용 이유 
   * Construcotr()은 state 값을 초기화 하거나 메소드를 바인딩 하기 위해 사용하고,    
      해당 컴포넌트가 마운트 되기 전에 호출된다.
      
   * React.Component를 상속한 컴포넌트의 생성자를 구현할 때에는 다른 구문에 앞서,  
     super(props)를 호출해야 한다. 그렇지 않을 시 `this.props`가 생성자 내에서    
     정의되지 않아 버그로 이어질 수 있다.
     
   * 자바스크립트에서 `super`는 부모 클래스 생성자를 가리키고, super(props) 선언 전까지,  
     constructor에서 `this`키워드를 사용 할 수 없다.
     
   * 리액트에서는 super가 constructor와 this의 실행순서로 인해 발생하는 문제 때문에,   
     사용하는 것을 권고하고 있다.
     
   * super() 선언 전에 this 사용하게 된다면?
      > consturctor이 호출된 이후에 props가 세팅된다.  
      > 초기화 되었기에 생성자 내부의 this.prop은 undefined가 된다.  
      > 초기에는 문제가 없지만, 후에 constructor의 다른 메소드를 수정할 때 문제가 발생한다.  
      > 해당 메소드가 super()를 불러오기 전에 실행되지만,  
      > this가 아직 변경되지 않았으므로 에러가 발생한다





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

## Router Props

 * Match
    
    match 객체에는 <Route path>와 URL이 매칭된것에 대한 정보가 담겨져있다.  
    match.params로 path에 설정한 파라미터 값을 가져올 수 있다.
 
 ```
 {path: "/mypage/:userId:, url: "/mypage/ididid", isExact: ture, params: {...}}  
    path: "/mypage/:userId"  
    url: "/mypage/ididid"  
    isExact: true  
    params: {userId: "ididid"}  
    __proto__: Object
 ```

> path : [string] 라우터에 정의된 path
>
> url : [string] 실제 클라이언트로부터 요청된 url path
>
> isExact : [boolean] true일 경우 전체 경로가 완전히 매칭될 경우헤만 요청을 수행
>
> params : [JSON object] url path로 전달된 파라미터 객체
 
 
 * Lacation
 
    loaction 객체에는 현재 페이지의 정보를 가지고 있다.  
    대표적으로 location.search로 현재 url의 쿼리스트링을 가져올 수 있다.  
    ex) 요청 URL `localhost:3000/mypage/ididid?`
 
 
 > pathname : [string] 현재 페이지의 경로명 
 >
 > search : [string] 현재 페이지의 query string 
 >
 > hash : [string] 현재 페이지의 hash
    
 
 * History
 
    history 객체는 브라우저의 history와 유사하다. 스택(stack)에 현재까지 이동한 url 경로들이  
    담겨있는 형태로 주소를 임의로 변경하거나 되돌아갈 수 있도록 해준다.
 
```
 {length/: 6, action: "POP", loaction: {...}, createHref: f, push: f, ...} 
   length: 6 
   acton: "POP" 
   location: {pathname: "/mypage/ididid", serach: "?name=kim", hash: "#hashtag", state: undefined} 
   createHref: f createHrff(loaction) 
   push: f push(path, state) 
   replace: f replace(path, state) 
   go: f go(n) 
   goBack: f goBack() 
   goForward: f goForward() 
   black: f black(prompt) 
   listen: f listen(listener) 
   __proto__: Object
 ```
 
 > length : [nmber] 전체 history 스택의 길이
 >
 > action : [string] 최근에 수행된 action (PUSH, REPLACE or POP)
 >
 > locaton : [JSON object] 최근 경로 정보
 >
 > push(path, [state]) : [function] 새로운 경로를 history 스택으로 푸시하여 페이지를 이동
 >
 > replace(path, [state]) : [function] 최근 경로를 history 스택에서 교체하여 페이지를 이동
 >
 > go(n) : [function]:history 스택의 포인터를 n번째로 이동
 >
 > goBack() : [function] 스택의 포인터를 n번째로 이동
 >
 > goForward():[function] 앞 페이지로 이동 >
 > block(prompt) : [function] history 스택의 PUSH/POP 동작을 제어
 
 


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
   
   
   
   
## BOM(Browser Object Model)
 * 브라우저 전체를 객체로 관리하는 것을 말한다.
 * 넓은 의미로는 웹 브라우저가 HTML 페이지를 인식하는 방식
 * 좁은 의미로는 document 객체와 관련된 객체의 집합
 * HTML 페이지는 트리 모양으로 구성, 각 요소를 노드라고 칭한다.
![image](https://user-images.githubusercontent.com/64000158/135571312-55705560-05ae-41b0-ac12-e05d4d7949e9.png)




`보충 필요`
## DOM(Document Object Model)
 * 문서의 구성요소들을 객체로 구조화하여 나타낸 것이다.
 * 문서의 구조화된 표현 제공 및 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공하며,    
    문서 구조, 스타일, 내용 등을 변경 할 수 있게 돕는다.
 * DOM은 구조화 된 nodes와 property와 method를 갖고 있는 objects로 문서를 표현한다.
 * 웸 페이지를 스크립트 또는 프로그래밍 언어에서 사용될 수 있게 연결시켜주는 역할을 한다.

 `웹 페이지를 구성하는 요소를 구조화해서 나타낸 객체고 이 객체를 이용해서 웹 페이지 구성요소를 제어할 수 있다.`
![image](https://user-images.githubusercontent.com/64000158/135572626-2c20585a-cd9b-4017-bfc9-8e9b69c04cb9.png)




`보충 필요`
## VDOM
 `DOM을 추상화한 가상의 객체`
 ### 어떤 문제를 해결하기 위한 기술인가?
  > DOM 조작에 의한 렌더링의 비효율적인 문제
  > 
  > SPA(Single Page Application)특징으로 DOM 복잡도 증가에 따른 최적화 및 유지 보수가 더 어려워지는 문제
  > * 결론 : DOM을 반복적으로 직접 조작하면 그 만큼 브라우저가 렌더링을 자주하게 되고,
  >          그 만큼 PC 자원을 많이 소모하기 때문
 
 ### 브라우저 렌더링 방식
 ![image](https://user-images.githubusercontent.com/64000158/135573274-c6ba4591-3e57-42c6-ab33-4e709a442d95.png)
 > 위의 과정에서 문제가 되는 경우는 현대의 웹처럼 변경해야할 대상도 많고, 변경도 많은 경우이다.
 > 
 > 프로그래밍에 의해 DOM을 변경해야 하고, 변경할 구성 요소가 100개면 위의 과정을 100번하는 비효율적이니 작업을 해왔었다.
 > 
 > 여기서 문제는, DOM을 변경하는것이 아니라, 렌더링을 여러번 하는것이 아주 큰 문제이다.
 
 ### 해결 원리
  DOM을 추상화한 가상의 객체인 VDOM을 메모리에 만들어 두고, 변경 사항을 DOM에 직접 수정하지 않고,
  
  중간 단계로 VDOM을 수정하고 VDOM을 통해서 DOM을 수정하게 하였다.
  
  > VDOM에 변경 내역을 한 번에 모으고(버퍼링) 실제 DOM과 변경된 VDOM의 차이를 판단한 후에,
  > 
  > 구성 요소의 변경된 부분만 찾아 변경하고 그에 따른 렌더링을 한 번만 하는 것으로 해결.

 

## React Component 생명주기  // VDOM 개념 필요

  모든 컴포넌트는  
   초기화 -> 업데이트 -> 소멸 단계를 거치게되고,  
   각 단계에서 메소드들이 정해진 순서대로 호출되는데,  
   이때 호출되는 메소드를 생명 주기 메소드라고 부른다.  





`보충 필요`
  ### 클래스형 component 생명주기
  
  * 마운트(생성)
   1) state, context, defaultProps 저장
   2) componentWillMount
   3) render
   4) componentDidMount

      Mount : 컴포넌트가 처음 실행 되는 것
      
      컴포넌트가 시작되면 우선 state, context, defaultProps 저장 하고 후에,  
      componentWillMount 메소드를 호출한다. 그리고 render로 컴포넌트를 DOM에  
      부착한 후 Mount가 완료된 후에 componentDidMount가 호출된다.  
      
      주의할 점은, componentWillMount단계에서는 props나 state를 바꾸면 안 된다.  
      Mount 중이기 때문이고, 아직 DOM에 render하지 않았기 때문에 DOM에도 접근할 수 없다.  
      componentDidMount에서는 DOM에 접근할 수 있기 때문에, 여기서는 주로 AJAX 요청이나,  
      setTimeout, setlnterval같은 행동을 한다.
      
   * 업데이트 - 리액트 컴포넌트가 업데이트 되는것을 말함

      업데이트가 발생하는 경우
        1) props가 바뀔 때
        2) state가 바뀔 때
        3) 부모 컴포넌트가 리렌더링될 때
        4) 강제로 트리거를 발생시킬 때

      호출하는 메소드
        1) static getDerivedStateFromProps
        2) shouldComponentUpdate
              > 컴포넌트가 다시 렌더링을 해야 할지 말아야 할지 결정하는 메소드이다.
              > 
              > 초기 렌더링 혹은 forceUpdate()호출시에는 호출되지 않는다.
              > 
              > 렌더링을 방지하여 성능을 최적화하는 목적으로 사용한다.    
 
 
        3) render
 
 
        4) getSnapshotBeforeUpdate
              > render 메소드 호출 후 DOM 변화를 반영하기 직전에 호출된 메소드이다.
              > 
              > 여기서 return된 값을 componentDidUpdate에서 3번째 파라미터로 받아 올 수 있다.
        5) componentDidUpdate
              > 리렌더링을 완료한 후 실행되는 메소드.
              > 
              > 최초 렌더링 시에는 호출되지 않음.
              > 
              > 컴포넌트가 업데이트 되었을 때, DOM을 조작하기 위해 사용
              > 
              >  ※ 주의 : componentDidUpdate에서 setState를 사용하면 무한 렌더링
              >  
              >            우려가 있으므로 조건문을 잘 작성해야한다.

   * 마운트 해제(제거)  - 리액트 컴포넌트가 DOM상에서 제거되는 것
        1) componentWillUnmount
              > 컴포넌트가 DOM에서 제거되기 직전에 호출되는 메소드이다.
              > 
              > 타이머를 제거하거나 데이터구독해제등의 목적으로 사용된다.
              > 
              >   ※ 주의 : componentWillUnmount가 호출된 컴포넌트는 다시
              >             렌더링 하지 않으므로, setState를 호출하면 안된다.
     ![image](https://user-images.githubusercontent.com/64000158/136879234-064706da-9a94-45d0-8cf8-ec94bd1b7361.png)



***

## React - Hook

   [참고문서](https://ko.reactjs.org/docs/hooks-intro.html)
   
   ### `개요`
   
   React component는 클래스형과 함수형으로 나뉘는데, 기존의 개발 방식은 함수형을 주로 사용하되
   
   state나 life cycle method를 사용해야 할 때마나 클래스형을 사용하였으나,
   
   16.8 버전부터는 함수형 컴포넌트에서도 React state와 Life cycle 기능을 사용할 수 있게 해주는
   
   함수인 Hook이 도입되었다. 만들어진 목적 자체가 함수형 컴포넌에서 사용하기 위함이였으니,
   
   당연하게도 클래스형 컴포넌트에서는 동작하지 않는다.
    
  ### `사용 규칙`
  
  * 최상위에서만 Hook 호출이 가능
     * 루프, 조건문, 중첩된 함수 안에서는 사용할 수 없음
     * 조건문을 Hook 내부에 넣는 것은 괜찮음
  > 컴포넌트가 렌더링 될 때마다 항상 동일한 순서로 Hook이 호출되는것이  
     보장되어 state를 올바르게 유지 할 수 있다.
  
  * 리액트 함수 컴포넌트내에서만 호출이 가능하다.
    * 일반 자바스크립트 함수 내에서는 호출하면 안된다.
    * custom hook 에서는 가능하다.

  ### `Why`
  
  * 컴포넌트들 사이에서의 상태 로직을 재사용하는 것의 어려움
     * higher-order component는 코드 추적이 어렵고 'wrapper hell' 이기 때문이다.
     * Hook은 컴포넌트의 계층을 바꾸지 않고, 상태 로직을 재사용 할 수 있다.
  * 복잡한 컴포넌트는 이해하기 어려움
     * 여러 Lifecycle 메소드들이 관련 없는 로직들과 섞여 있다.        
       그래서 버그가 자주 발생하고, 무결성 유지가 어렵다.   
  * Class 컴포넌트는 인간과 기계 모두를 혼란스럽게 한다.
     * 리액트의 진입장벽
     * 코드가 장황해짐
     * Class없이 React 기능을 사용해 보기 
  
  ## useState란?
  
  > Hook을 호출하여 함수형 컴포넌트에 state 변수를 선언 할 수 있는 함수 -> 
  > 
  > -> 컴포넌트가 다시 렌더링 되어도 그대로 유지된다.
  > 
  > 기존 class 컴포넌트에서 사용하던 this.state와 동일한 역할을 한다.
  > 
  > useState는 state 변수와 state를 업데이트 하는 함수, 두 가지 쌍을 반환한다.
```
const [age, setAge] = useState(20);
const [fruit, setFruit] = useState('banana');
const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
```
 위처럼 state를 여러 개 선언 할 수 있다. 위와 같은 표현을 `구조 분해 할당`이라고 한다.
 
 첫 번째 인자는 state의 name이고, 두 번째 인자는 state를 업데이트 할 수 있는 함수이다.
 
 useState에 전달하는 인자는 state의 initial value의 값이다.
 
 객체로 넘겨주거나, 숫자, 문자 타입도 가능하다.
 
 
## useEffect      `보충 및 정리 필요` [참고문서](https://overreacted.io/ko/a-complete-guide-to-useeffect/)

  useEffect는 몇 가지 조건에 의해 작동하게 된다.
 
 첫번째 : 페이지가 처음 렌더링 되고 난 후 useEffect는 무조건 한번 실행된다.
 
 두번째 : useEffect에 배열로 지정한 useState의 값이 변경되면 실행된다.
 
 useEffect는 렌더링, 혹은 변수의 값 혹은 오브젝트가 달라지게 되면, 인지하고 업데이트를 해주는 함수이다.
 
 useEffect는 콜백 함수를 부르게 되며, 렌더링 혹은 값, 오브젝트의 변경에 따라
 
 어떠한 함수 혹은 여러 개의 함수들을 동작시킬 수 있다.
  
 useEffect 사용 방법
 ```
 // 1번
 useEffect(() => {});  

 // 2번 
 useEffect(() => {}, []); 
 
 // 3번
 const [name, setName] = useState();
 useEffect(() => {}, [name]); 
 ```
 * 1번 : 가장 기본 형태이지만, 이러한 형태는 거의 사용하지 않는다. Dependency가 없기 때문에,
 
        작은 요소라도 변화한다면 계속 useEffect가 발동되어 불필요한 실행이 너무 많아진다.
 
 
 * 2번 : useEffect를 렌더링 후 한 번만 실행하고 싶을 때 사용하는 방법이다.
 
        콜백 함수 뒤에 배열을 나타내는 대괄호가 붙어 있는데, 이곳에 Dependency를 지정한다.
 
        하지만 변수나 값 없이 대괄호만 있다면, useEffect는 렌더링 후 딱 한번만 실행되고,
 
        다시는 실행되지 않는다.
 
 
 * 3번 : useEffect를 렌더링 후 한번, 그리고 배열 안 변수의 값이 변할 때마다 실행하는 코드이다.
 
        이렇게 Dependency를 지정해주어 지정된 변수의 값이 변했을 때에만 실행되게 된다.
 
  
 
 
 
  ### 기본 형태 -> `useEffect(function, deps)`
  
  - function : 수행하고자 하는 작업
  
  - deps : 배열 형태이며, 배열 안에는 검사하고자 하는 특정 값 or 빈 배열
 
 
  useEffect 함수 불러오기
  
  `import React, { useEffect } from 'react';`


  > React 컴포넌트 안에서 데이터 fetching, subsription, DOM을 직접 조작하는 것을 Side effect라고 한다.
  > 
  > 줄여서 effects라고 한다. 이
  >
  > 



