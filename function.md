# 함수

## 기명(이름이 있는) 함수 / 함수 선언

```js
function hello() {
  console.log("hello");
}
```

## 익명(이름이 없는) 함수 / 함수 표현

함수 명이 없기 때문에, 변수에 함수를 담아서 표현

```js
const world = function () {
  console.log("world");
};

hello(); // hello
world(); // world
```

## method

getName처럼 같이 값으로 함수가 들어가 있는 경우에는 속성이 아닌, method라 한다

```js
const heropy = {
  name: "heropy",
  age: 85,
  getName: function () {
    return this.name;
  },
};
```

---

# DOM API

js에서 html를 제어하는 명령어  
(addEventListener, classList, forEach, textContent)

## addEventListener

첫번째 인자에는 이벤트(click, scroll, keydown 등...), 두번째 인자에는 핸들러(실행할 함수)

## classList

class 속성에 대한 제어(add, remove, contains(class 속성 값 존재 여부 확인, boolean 형태 반환))

```js
// index.html
<div class="box">BOX!</div>
```

```js
//main.js
let boxEl = document.queryselector(".box");
console.log(boxEl); // <div class="box">BOX!</div>

boxEl.addEventListener("click", function () {
  console.log("누르지마라!");
  boxEl.classList.add("activate");
});

let isContains = boxEl.classList.contains("activate");
console.log(isContains); // true
```

```js
const boxEl = document.queryselector(".box");
boxEl.classList.add("activate");
let isContains = boxEl.classList.contains("activate");
console.log(isContains); // true

boxEl.classList.remove("activate");
isContains = boxEl.classList.contains("activate");
console.log(isContains); // false
```

## forEach

첫번째 매개변수 : 반복 중인 요소  
두번째 매개변수 : 반복 중인 번호, 순서

```js
// html
<div class="box">1</div>
<div class="box">2</div>
<div class="box">3</div>
<div class="box">4</div>
```

```js
const boxEls = document.querySelectAll(".box");

boxEls.forEach(function (boxEls, index) {
  boxEls.classList.add(`order-${index + 1}`);
  console(index, boxEl);
});

// 0 <div class="box order-1">1</div>
// 1 <div class="box order-2">2</div>
// 2 <div class="box order-3">3</div>
// 3 <div class="box order-4">4</div>
```

## textContent

```js
// index.html
<div class="box">BOX!!</div>;

// main.js
const boxEl = document.querySelector(".box");

// getter (값을 얻는 용도)
console.log(boxEl.textContent); // BOX!!

// setter (값을 지정하는 용도)
boxEl.textContent = "SAY ANYTHING!!";

console.log(boxEl.textContent); // SAY ANYTHING!!
```

## 메소드 체이닝

여러 메소드를 점 표기법으로 작성하는 것

```js
const a = "HELLO~";
// split : 문자를 인수 기준으로 쪼개서 배열로 반환하는 메소드
// reverse: 배열을 뒤집는 메소드
// join : 배열을 인수 기준으로 문자로 병합해 번환하는 메소드

const b = a.split("").reverse().join(""); // 메소드 체이닝

console.log(a); // HELLO~
console.log(b); // ~OLLEH
```

---

# 생성자 함수

객체를 생성할때 사용하는 함수 (객체: 객체 데이터를 저장하는 그릇)

```js
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
  this.sayHello = function () {
    alert(this.name + ' said "hello"');
  }; // 메소드
}
let chan = new Person("chan", "male");
let mina = new Person("mina", "female");
// new로 새로운 객체를 생성, Person이라는 함수 또한 대문자 P로 시작하므로 생성자 함수인 것을 암시
chan.sayHello();
mina.sayHello();
```

---

# 프로토타입(원형)

부모의 유전자라는 의미

```js
function Person2(name, gender) {
  this.name = name;
  this.gender = gender;
}
Person2.prototype.sayHello = function () {
  alert(this.name + "반갑다");
};
// function Person2 내부의 객체 데이터가 아닌 prototype를 사용함으로서, Person2라는 함수에 sayHello를 추가
let chan1 = new Person2("chan1", "male");
let mina1 = new Person2("mina1", "female");
chan1.sayHello();
mina1.sayHello();

// 생성자 함수일 경우 첫글자가 대문자여야 한다. ex)Person
// 아래에서 new Person으로 생성자 함수를 불러올 수 있다.
// constructor은 생성자 함수 그 자체를 가리킴
// prototype는 생성자 함수에 정의한 모든 객체가 공유할 원형(유전자)
// Person2.prototype.000 = 000 이건 부모만 가짐, 자식은 x but, 부모한테 가져와서 불러올 수 있음
```
