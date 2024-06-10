---
title: Javascript - 실행컨텍스트
categories:
- Javascript
excerpt: |
  A pot still is a type of still used in distilling spirits such as whisky or brandy. Heat is applied directly to the pot containing the wash (for whisky) or wine (for brandy).
feature_text: |
  ## The Pot Still
  The modern pot still is a descendant of the alembic, an earlier distillation device
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### &lt;실행 컨텍스트&gt;

```javascript
// 예제 코드
var x = 1;
const y = 2;

function foo (a) {
  var x = 3;
  const y = 4;
  
  function bar (b) {
    const z = 5;
    console.log(a + b + x + y + z);
  }
  bar(10);
}

foo(20); // 42
```

![](https://velog.velcdn.com/images/chjw147/post/bb54bf09-446b-420a-a080-c9b76c7c2927/image.png)


>-**소스코드를 실행하는데 필요한 정보들을 모두 담고 관리하는 환경을 가지고 있다**.(=렉시컬 환경을 가지고 있다)<br>
-여러 스코프들이 담기게 된다.<br>
-실행이 완전히 끝나면 콜 스택에서 제거된다. ( 단, 내부에 참조가 엮여 있을 경우 제거되지 않고 남아있게 됨 )<br>
-콜 스택에 쌓여 현재 실행 흐름을 알 수 있게 해준다.

>참고로 글로벌 실행 컨텍스트는 프로그램 실행시 가장 먼저 생성되고 가장 마지막에 제거 된다. 스택 방식처럼 push, pop 형태로 흘러가기 때문이다.

### &lt;소스코드&gt;
>자바스크립트 ECMAScript 사양은 소스코드를 4가지 타입으로 구분한다.

+ **전역 코드** : 전역에 있는 코드이다. 전역에 정의된 함수나 클래스등의 내부코드는 포함하지 않는다.
+ **함수 코드** : 함수 내부에 있는 코드이다. 함수 내부의 함수나 클래스등의 내부 코드는 포함하지 않는다.
+ **eval 코드** : eval 코드는 strict mode(엄격 모드)에서 자신만의 독자적인 스코프를 생성한다. built-in 전역 함수인 eval 함수에 인자로 전달되어 실행되는 코드이다.
+ **모듈 코드** : 모듈 코드는 모듈별로 독립적인 모듈 스코프를 생성한다. 모듈 내부의 함수나 클래스등의 내부 코드는 포함하지 않는다.

### &lt;실행&gt;
> -인터프리터 언어 (컴파일 과정이 없는 언어) : Jvascript, Python...<br>
-컴파일 언어 : JAVA, C...

>-**자바스크립트는 컴파일 과정이 없는 대신 평가 과정이 있다.**<br>
-이 평가는 실행 전에 행해지며 실행컨텍스트 단위로 이루어진다.  즉 콜 스택에 새로운 실행컨텍스트가 생기면 그 실행컨텍스트에 대해 평가를 먼저 하고 실행을 진행한다.


### &lt;렉시컬 환경(Lexical Environment)&gt;
>-**소스코드를 실행하는데 필요한 정보들을 모두 담고 관리하는 환경** <br>
-파일이 실행될 때 소스코드에 해당하는 부분을 읽으며 그에 맞는 실행컨텍스트가 콜 스택에 쌓이게 되는데 이 실행컨텍스트 안에 렉시컬 환경(**스코프들의 모임**)이 생기게 된다.


#### 글로벌 렉시컬 환경(Global Lexical Environment)

![](https://velog.velcdn.com/images/chjw147/post/1f3a8c36-7df7-4784-a6a2-981fa365f4c3/image.png)

>-위 그림은 콜 스택(실행 컨텍스트 스택)에 글로벌실행컨텍스트가 생기고 렉시컬 환경을 만들기 위해 전역코드에 대한 실행 전 **평가** 과정을 거친 상태를 보여준다.<br>
-이 평가 후 **실행**이 될 때 undefined 로 초기화된 변수등에 값이 할당되며 메모리가 잡히게 된다.

![](https://velog.velcdn.com/images/chjw147/post/c396b057-8835-4030-be75-57f2b1c394b8/image.png)



+ 글로벌환경레코드 (Global Environment Record)
   - 객체 환경 레코드 (Object Environment Record)
      - BindingObject : 이 안에 window 객체가 있고, window 안에 var, function 등이 생기게 된다.
   - 선언적 환경 레코드 (Declarative Environment Record) : let, const 등으로 선언된 변수들이 생기게 된다. 글로벌 렉시컬 환경에만 존재.


+ 외부렉시컬환경참조 (Outer Lexical Environment Reference) : 이 참조 영역에 있는 스코프로 스코프체인이 일어날 수 있게 된다.


#### 함수 렉시컬 환경(Function Lexical Environment)


![](https://velog.velcdn.com/images/chjw147/post/9d2965b4-1f99-46c8-b434-67e97ffa3a95/image.png)

>-위 그림은 인터프리터에 의해 전역코드가 읽혀지며 실행이 진행되고 있는 상태에서, 함수 호출 코드를 만나 콜 스택(실행 컨텍스트 스택)에 함수 실행 컨텍스트가 생기고 이에 대한 렉시컬 환경을 만들기 위해 **평가**가 진행된 결과를 보여준다.<br>
-전역코드에 대해서 진행한 것처럼 함수 내부에 대해서도 평가가 끝났으니 **실행**이 일어나게 된다.

![](https://velog.velcdn.com/images/chjw147/post/f71cd29a-70fc-4e3a-8733-584f25ba98c7/image.png)


+ 함수 환경 레코드 (Function Environment Record) : 함수 내부에서 선언된 변수나 함수 등이 생기게 된다. 전역 렉시컬 환경의 window 를 참조하고 있음.

+ 외부 렉시컬 환경 참조 (Outer Lexical Environment Reference) : 이 참조 영역에 있는 스코프로 스코프체인이 일어날 수 있게 된다.


> **주의** : 함수 렉시컬 환경은 위 그림에서 빨간 박스 부분만 해당하는게 아니다. 참조하는 스코프 (여기서는 글로벌 렉시컬 스코프)까지 포함해서 함수 렉시컬 환경이다.
그림은 없지만 예시코드를 보면 bar 함수는 foo 함수 렉시컬 스코프와 글로벌 렉시컬 
스코프를 참조하니까 이 모두를 포함한 환경이 bar 함수 렉시컬 환경이 된다.

>**렉시컬 스코프 vs 렉시컬 환경**<br>
-렉시컬 스코프 : 함수가 정의된 위치에 따라 변수의 범위를 결정하는 규칙이다.<br>
-렉시컬 환경 : 특정 시점에서의 실행 컨텍스트 내에서 변수와 함수 선언을 관리하는 데이터 구조이다.<br>
-렉시컬 스코프는 코드 작성 시의 변수 유효 범위를 정의하고, 렉시컬 환경은 실행 시의 변수와 함수의 실제 저장소와 관련된 개념이다.
**(그냥 같은 말이라고 생각해도 큰 무리가 없다.)**




참고 : https://iridescent-zeal.tistory.com/269
