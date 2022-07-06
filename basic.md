# 표기법

dash-case, snake_case : html, css에서 주로 사용  
camelCase, PascalCase : js

---

# 사용방법

html의 head부분에서 script를 호출하면, body 부분을 읽기 전 script가 동작하므로,  
오류가 발생하기 때문에, body 아래에 script를 사용하거나,  
head 영역에서 사용하려는 경우 defer이라는 속성을 추가한다.

---

# 보간법

```js
let myName = "CHAN";

// ${}안은 변수, 데이터를 넣을 수 있다
let hello = `Hello ${myName}`;
console.log(hello); // Hello CHAN

let hello = `Hello ${"name"}`;
let hello = `Hello ${123}`;
let hello = `Hello ${false}`;
```

---

# 인자(parameter), 인수(argument) 차이

> 인자 : 함수를 정의할 때 외부로부터 내부로 전달하는 변수의 값을 의미. 즉, 함수를 정의할 때 사용

> 인수 : 함수를 호출할 때 사용되는 데이터 값을 의미

```js
function justFunc(a, b) {} // a, b는 파라미터
justFunc(1, 2); // 1, 2는 인수
```
