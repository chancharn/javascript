# 데이터 종류

string, number, boolean, undefined, null, object, array

## string

```js
let name = "DOG";
let hello = `hello ${name}!`; // 보간법

console.log("name"); // name
console.log(name); // DOG
```

## num

```js
let num = 1.23;
let notNum = "1.23";
```

## boolean

```js
let getTrue = true;
console.log(getTrue); // true
```

## undefined

값이 할당되지 않은 상태

```js
let undef;
let obj = { abc: 123 };

console.log(undef); // undefined
console.log(obj.abc); // 123
console.log(obj.xyz); // undefined
```

## null

undefined와 비슷하게 값이 빈 상태지만, '의도적'으로 비운 경우

```js
let empty = null;
console.log(empty); // null
```

## object

객체 데이터 key:value 형태

```js
let user = {
  name: "abc",
  age: 100,
  isValid: true,
};

console.log(user.name); // abc
console.log(user.age); // 100
console.log(user.isValid); // true
```

## array

배열 데이터

```js
let fruits = ["apple", "banana", "melon"];

console.log(fruits[0]);
```

---

## const

const 불변 변수를 수정할 땐,  
push, shift, pop와 같은 내장함수를 사용하지 않고,  
concat, slice와 같은 함수로 수정한다.

> 배열 데이터 형태

```js
// push

const arr = [];
const arr2 = arr.concat(1, 2, 3, 4, 5);
const arr3 = arr2.concat(0);
console.log(arr, arr2, arr3);
// [], [1,2,3,4,5], [1,2,3,4,5,0]

const arr4 = [1, 2, 3, 4, 5];
console.log(arr4.slice(0, 2), arr2);
// [1, 2] 마지막 항목은 포함하지 않으므로 1, 2번째만 반환
// [1, 2] [1, 2, 3, 4, 5]
```

```js
// shift

// shift와 같은 가장 앞의 인자를 자르려는 경우
// length는 1부터 카운팅
const len = arr4.length;
console.log(arr4.slice(1, len));
// 또는
console.log(arr4.slice(1));
// slice인자로 두번째를 입력하지 않으면 자동으로 끝까지 포함
```

```js
// pop

// pop와 같은 가장 끝 인자를 자르려는 경우
console.log(arr4.slice(0, len - 1));
```

```js
// splice

// splice와 같이 가운데에 값을 추가하거나, 삭제할 때
const arr5 = [1, 2, 3, 4, 5];
arr5.splice(2, 2, 0.1, 0.7, 0.9);
// 첫번째 위치의 인자는 삽입할 위치, 두번째 인자는 삽입할 위치를 기준으로 삭제할 값 갯수, 세번째부터는 삽입하려는 값
console.log(arr5);
// [1, 2, 0.1, 0.7, 0.9, 5]
const arr6 = [...arr5.slice(0, 2), 0.1, 0.7, 0.9, ...arr5.slice(5)];
console.log(arr6);
```

> 객체 데이터

```js
// 객체 데이터의 값을 변경할 경우 X
const obj = {
  a: 1,
  b: 2,
};
obj.a = 5;
console.log(obj);

// 위 방식이 아닌 아래의 방식으로 변경한다
const obj2 = {
  ...obj,
  a: 1,
};
console.log(obj2);
```
