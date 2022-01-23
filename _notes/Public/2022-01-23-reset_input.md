---
title: "버튼 누르면 화면상 input 리셋되게 하는 방법"
notetype : feed
date : 23-01-2022
---

<br />

submit 버튼을 누르면 화면상 입력했던 모든 input사라지게 하려면 (근데 데이터 저장은 됨)
<br />
-> `value={}` 사용한다.
<br />
<br />

기존 `<input type="text’" onChange={titleChangeHandler} />` 은 사용자가 input내용을 대로 화면에 보이게끔 만들어준다. 

근데 반대로, we can also pass a new value into the input. (`submitHandler`안에다가 `setEnteredTitle("")` 삽입하면 된다.)

```js
const [enteredTitle, setEnteredTitle]= useState(’’)

const submitHandler= (event) ⇒ {
event.preventDefault();      // submit버튼 누를때마다 page reload 되지 않게끔.
setEnteredTitle(’’);
}

return (
	<form onSubmit={submitHandler}>
    <div className='whatever'>
     <input type=’text’ 
            value={enteredTitle} 
            onChange={titleChangeHandler} />
     {/* ... 또 다른 input 여러개 (여기에도 value element 넣어주고 똑같이 처리하면 input clear가능) */}
    </form>   
)

```

<br />
**결론** : `<input type="text" value={enteredTitle} onChange={titleChangeHandler} />`

<br/>
(input 여러개 있으니까 같은form영역이다~ 라는 뜻에서 form태그로 감싸주는 것이다.)
