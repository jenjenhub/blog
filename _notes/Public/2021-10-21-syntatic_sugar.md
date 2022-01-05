---
title: "구조분해할당"
notetype : feed
date : 21-10-2021
---

### Syntatic Sugar



Chrome console에서 다음과 같이 쳐보면서 구조분해할당을 이해해보자.

```js
const word = 'hello';           // undefined 출력

const number = 123;             // undefined 출력

const obj = { word, number };   // undefined 출력

obj 
  -> { word: 'hello', number: 123 } 출력

```



value를 const로 선언하고

obj 를 생성해 객체구조로 안에 key만 넣어주면

obj 는 { key : value,  key : value,  key : value ... } 형태로 만들어진다 !
