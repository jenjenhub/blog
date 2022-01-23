---
title: "Mutable, Immutable (& reference)"
notetype : feed
date : 21-10-2021
---

<br />
## immutability  (불변성)  vs.  mutability

immutable한 상태냐,  mutable한 상태냐를 구분해야 하는 경우가 있다.

<br />


### 📌 Object 

Immutability는 객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴

JavaScript의 원시 타입(primitive data type)은 immutable value

+ Boolean
+ null
+ undefined
+ Number
+ String
+ Symbol


<br />

#### immutable

```javascript
let user = { name : 'Jenny'}

let myName = user.name  // 변수 myName은 string
user.name = 'Caleb';
myName;            // 'Jenny'
user;              // { name: 'Caleb'}


👩🏻‍💻 user 객체는 (+user.name까지) 변경됐지만, myName은 그대로 ?!
   
      👉 변수 myName에 user.name을 할당했을 때, immutable값인 'Jenny'가 메모리에 새로 생성되고 myName은 이 immutable값 'Jenny'를 참조하기 때문이다. (user.name의 참조를 할당하는 것이 아님)
         그래서 user.name이 변경되어도 myName이 참조하는 'Jenny'는 변함이 없다.
```





#### mutable

```javascript
let user1 = { name : 'Jenny'}

let user2 = user1   // 변수 newUser는 object
user2;          // { name: 'Jenny' }
user2.name = 'Caleb';     // user2를 변경해줌
user2;          // { name: 'Caleb' }
user1;          // { name: 'Caleb' }  👩🏻‍💻 user1 변경하지도 않았는데 왜 바뀜???
user1.name;            // 'Caleb'
user2.name;            // 'Caleb'

👉 user1과 user2가 같은 address를 참조하고 있기 때문에, 변경하지도 않은 객체 user1도 동시에 변경된다.
```

<br />


#### 🔮 참조(reference) 와 연관이 있달까.

숫자 = 원시 데이터형(기본 데이터형, Primitive Data Types)

JavaScript에서는 원시 데이터형을 제외한 모든 데이터 타입은 객체이다.

객체를 다른 말로는 참조 데이터 형(참조 자료형)이라고도 부른다. 기본 데이터형은 ''복제''되지만 참조 데이터형은 ''참조''만 된다. 모든 객체는 참조 데이터형이다.

복제는 파일을 복사하는 것이고 참조는 심볼릭 링크(symbolic link) 혹은 바로가기(윈도우)를 만드는 것과 비슷하다. 

<br />

   
<br />

### 📌 Array



immutable은 원래 객체 다룰 때 쓰는데 배열은 참고만 하기.



 [1,2,3,4] 를  [1,2,3,4,5] 로 만들고 싶을 때 :

#### mutable

```javascript
const arr= [1,2,3,4]; 
arr.push(5);
arr;
```

👉  push() 메소드는 직접 arr을 변경하기 때문에 mutable



