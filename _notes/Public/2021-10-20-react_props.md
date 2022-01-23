---
title: "React : 부모 컴포넌트 → 자식 컴포넌트 props 전달하기"
notetype : feed
date : 20-10-2021
---

<br />

## Case 1


<img width="1078" alt="111" src="https://user-images.githubusercontent.com/85834764/150670211-05638d3e-05cf-403d-9941-14ed8214100c.png">


❗️onClick이라는 변수로 설정한 것. 

​	근데 객체니까 생긴 게 {onClick : handleRollClick}    ← 전체가 props.

​    형태로 따지자면, {prop : state} 전체를 props라 묶어 칭하는데, 그렇다면 지금 props= { onClick : handleRollClick }

​	props.onClick하면 handleRollClick이 되는거고,

​	그래서 props라 하면, onClick={handleRollClick} 을 의미하는 것. 
​    구조는 onClick에 handleRollClick함수가 할당되어 있다고 말할 수 있다.


<img width="578" alt="222" src="https://user-images.githubusercontent.com/85834764/150670222-46f28890-1250-48a7-8b30-8fe11f6f2f86.png">



function Button ({onClick}) {

const **onClick** = () => {         <- 이 onClick은 다른 함수이름으로 바뀌어도 무방.

onClick()

}}

...생략...

return <button onClick={onClick}></button>    
여기 첫번째 onClick은 또 다른 컴포넌트에  **onClick**함수를 props로 전달하기 위한 prop부분이다.



﹦



function Button (props) {

const onClick = props.onClick

}  

와 동일함.

<br />
<br />

## Case 2





Web:

<img width="530" alt="333" src="https://user-images.githubusercontent.com/85834764/150670229-5f6d67c7-7a31-434e-b4f3-f9445b5f5399.png">


👉 이 화면에서 '값 변경' button을 누르면 '값은 보여줄게 완전히 달라진 값 입니다' 라고 뜨도록 바꾸고 싶다 !

​       부모 컴포넌트에서 상태변경함수를 만들어 자식 컴포넌트에 전달 후 사용하는 방식을 쓰자.


<br />

#### 📌 Original

```javascript
import React, { useState } from "react";

export default function ParentComponent() {
  const [value, setValue] = useState("날 바꿔줘!");

  const handleChangeValue = () => {
    setValue("보여줄게 완전히 달라진 값");
  };

  return (
    <div>
      <div>값은 {value} 입니다</div>
      <ChildComponent />
    </div>
  );
}
-----------------

function ChildComponent() {
  const handleClick = () => {
    // 💡 이 버튼을 눌러서 부모의 상태를 바꿀 순 없을까????
  };

  return <button onClick={handleClick}> 값 변경 </button>
}
```

<br />

### 부모 컴포넌트 → 자식 컴포넌트 props 전달방법 ❗️



부모 컴포넌트에 있는 상태변경함수인 handleChangeValue를 자식 컴포넌트에서도 쓸 수 있도록 전달하고 싶을 때, 
props를 사용한다. 

props 이름을 handleButtonClick이라 지어주자. 

부모 컴포넌트 return부분에 <code><ChildComponent handleButtonClick={handleChangeValue} /> </code> 라고 써주면 props로 자식컴포넌트에 전달된다.

이제 자식컴포넌트 페이지에 와서는 맨 위에, <code>function ChildComponent({handleButtonClick}) { </code>  인자로 props이름을 넣어준다. (그러면 이제 이 props는 ChildComponent내에서 자유롭게 사용 가능하다)




구조 : 

<code><ChildComponent handleButtonClick={handleChangeValue}/> </code>에서 

handleButtonClick이 prop이고 handleChangeValue가 state 

props는 handleButtonClick={handleChangeValue}



function ChildComponent (props) { 

const handleButtonClick = props.handleButtonClick 

가 축약된 게 Result 1 version !! 

왜? props = {prop : state} 

props= {handleButtonClick : handleChangeValue}



<br />

#### 📌 Result 1

```js
import React, { useState } from "react";

export default function ParentComponent() {
  const [value, setValue] = useState("날 바꿔줘!");

  const handleChangeValue = () => {
    setValue("보여줄게 완전히 달라진 값");
  };

  return (
    <div>
      <div> 값은 {value} 입니다 </div>
      <ChildComponent handleButtonClick={handleChangeValue}/>
    </div>
  );
}
-----------

function ChildComponent({handleButtonClick}) {
  const handleClick = () => {
    handleButtonClick()
  };

  return <button onClick={handleClick}> 값 변경 </button>
}
```



Web :


<img width="531" alt="444" src="https://user-images.githubusercontent.com/85834764/150670237-5d4546f7-fea8-414a-b14c-c2db50a56d42.png">





<br />

#### 📌 Result 2

설정할 값(newValue)을 콜백 함수의 인자로 넘기면, 

newValue에 새로운 text '넘겨줄게 자식이 원하는 값'을 넣어서 부모와 자식이 다른 text를 화면에 보여주게끔 만들 수 있다. ( 자식 컴포넌트에서 useState를 새로 쓰면서, 부모 condition과 다르게 condition을 변화시킬 수 있음 )

handleChangeValue = handleButtonClick 

handleChangeValue함수를 부모에서 자식으로 props로 넘겨주면서 이름만 handleButtonClick으로 변경

```js
function ParentComponent() {
  const [value, setValue] = useState("날 바꿔줘!");

  const handleChangeValue = (newValue) => {
    setValue(newValue);
  };

const handleChangeValue = () => {
    setValue("보여줄게 완전히 달라진 값");
  };

  return (
    <div>
      <div>값은 {value} 입니다</div>
      <ChildComponent handleButtonClick={handleChangeValue}/>
    </div>
  );
}
-----------
function ChildComponent({ handleButtonClick }) {
  const handleClick = () => {
    handleButtonClick('넘겨줄게 자식이 원하는 값')
  }

  return (
    <button onClick={handleClick}> 값 변경 </button>
  )
}
```



Web :

<img width="538" alt="555" src="https://user-images.githubusercontent.com/85834764/150670244-ffa6abdb-5c33-4484-952b-7a2dbb37966e.png">



