---
title: Javascript - 호이스팅
categories:
- Javascript
feature_image: "https://picsum.photos/2560/600?image=872"
---

### <호이스팅>
>코드를 실행시킬 때 코드에서 변수나 함수를 선언하는 부분이 <span style="color:red"> **스코프 영역 내의 최상단** </span>으로 올라가서 실행되는 것.
&rarr; var 나 function(){} 같은 경우 선언보다 호출 코드가 먼저 와도 오류가 나지 않는 이유이다.

>**함수레벨스코프** : `var, 함수선언식` 은 호이스팅 시 함수스코프 최상단으로 호이스팅이 일어난다.

>**블록레벨스코프** : `let, const, 함수표현식, 화살표함수` 는 호이스팅 시 블록스코프 최상단으로 호이스팅이 일어난다.

---

### &lt;변수 호이스팅&gt;

>**var** : 선언과 초기화(undefined 값으로)가 함수스코프 내 최상위에서 실행 된다. 할당은 코드의 원래 자리에서 이루어진다.

```javascript
console.log(a); // undefined
var a = 1;

console.log(a); // 1

var a = 2; // a=2, 재선언 가능
a= 3; // a=3, 재할당 가능
```
---
+ var 변수를 글로벌 스코프에서 (즉 함수 외부에서) 선언하면 글로벌 객체의 속성이 된다.
let 과 const 는 제외.

---

>**let** : 선언 부분은 블록스코프 내 최상위에서 실행 된다. 하지만 초기화와 할당이 코드의 원래 자리에서 이루어진다.

```javascript
console.log(a); // error. 선언만 되고 초기화되지 않은 식별자에 접근. TDZ(Temporal Dead Zone)
let a = 1;

console.log(a); // 1

let a = 2; // error. 재선언 불가능
a = 3; // a=3, 재할당은 가능
```

>**const** : 선언 부분은 블록스코프 내 최상위에서 실행 된다. 하지만 초기화와 할당이 코드의 원래 자리에서 이루어진다. (재할당 불가능)

```javascript
console.log(a); // error. 선언만 되고 초기화되지 않은 식별자에 접근. TDZ(Temporal Dead Zone)
const a = 1;

console.log(a); // 1

const a = 2; // error. 재선언 불가능
a = 3; // error. 재할당 불가능
```

---
+ const 선언 시 제일 처음 주어진 메모리 값을 수정할 수 없다는 것이지 그 값이 참조하고 있는 값을 수정할 수는 있다.
ex) 식별자 a가 가르키고 있는 참조주소값이 아닌 그 주소에 해당하는 값을 수정할 수 있다.
```javascript
const a = { first : 1, second : 2 };
a.first = 2; // 객체 a 의 first 값은 2로 바뀐다.
```


---

### &lt;함수 호이스팅&gt;

>**선언식** : var 와 유사하다. 식별자 와 몸통({ }) 부분이 함께 함수레벨스코프의 최상단으로 올라가서 실행된다. (호이스팅 시 초기화 값으로 함수 내부 코드들이 그냥 텍스트 같이 함수객체라는 값으로 주어 지고, 실제 내부 코드들의 메모리 할당은 함수 호출(실행) 시에 실행컨텍스트와 스코프가 생기면서 이때 일어난다. 

```javascript
aa(); // 선언 전 호출 가능. aa함수는 호이스팅 되어 가지고 있던 코드를 실행시키면서 내부코드들에 대한 메모리를 잡는다.

function aa(){
  var a = 1; 
  let b = 2;
  const c = 3; // 내부 코드에 해당하는 변수나 함수들은 aa함수가 호출될 때, aa함수스코프가 생기며 이 스코프영역의 메모리에 등록된다.
}

aa(); // 선언 후 호출 가능.
```

>**표현식** : 함수부분을 단순히 값(리터럴) 취급을 하므로 변수(식별자)는 선언 키워드에 따라 해당하는 호이스팅이 일어나고, 함수는 값으로써 원래 자리에서 변수에 할당될 뿐 따로 호이스팅이 일어나지 않는다. 함수 내부 코드들은 선언식처럼 함수가 호출될 시 메모리가 잡힌다.

```javascript
aa(); // error. 선언 전 호출 불가능.

const aa = function(){  // var 였으면 aa는 var처럼 호이스팅 된다. undefined로 초기화된 채.
  var a = 1;
  let b = 2;
  const c = 3;
};

aa(); //  정상적으로 함수가 실행되면서 스코프를 만들고 내부 코드들의 메모리를 잡는다.
```

>**화살표** : 표현식의 한 종류이므로 표현식과 같이 동작한다.

```javascript
aa(); // error. 선언 전 호출 불가능.

const aa = ()=>{
  var a = 1;
  let b = 2;
  const c = 3;
};

aa(); // 선언 후 호출 가능.
```

---


### &lt;함수 내부 호이스팅&gt;

> 선언식, 표현식, 화살표 함수 모두 함수가 호출되어 실행될 때, aa라는 함수 스코프를 만들면서 내부 코드에 대한 메모리를 잡는다. 이때도 변수와 함수에 대해서 호이스팅이 일어난다.

```javascript
function aa() {
  var a = 1;
  let b = 2;
  const c = 3;
  function bb() {
    console.log('qqq');
  }
}
```


---

### &lt;블록 내부 호이스팅&gt;

> **for문, if문, while문...**
블록 내부에서도 호이스팅이 일어난다. var 와 함수선언식은 함수레벨스코프에 따라 움직이므로 블록스코프를 뛰쳐 나간다.

```javascript
function aa(){
  var a = 1; // aa함수스코프에 a,b,c,d,bb 가 등록된다.
  let b = 2;
  const c = 3;
  for ( a; a<5; a+=1){ // for 스코프에 e가 등록된다.
    console.log(a);
    var d = 4;
    let e = 5;
    function bb(){
      console.log(b);
    }
  };
}
```
