---
title: "split, slice, splice"
notetype : feed
date : 06-01-2022
---
# str.split (separator)   

### ☑️ str을 쪼갤 때 | str을 arr로    <br />

<br/>

#### 1.  띄어쓰기마다 쪼개기

	let string = ‘Hello my name is Jenny’

	string.split(’ ‘)[2] 하면  → ‘name’ 출력

Why ? 👉   space 있는 곳마다 string을 쪼개고, 쪼개진 유닛(단어)의 0,1,2번째인 name이 출력.

<br />



	let string = ‘Hello,my,name,is,Jenny’ 라면

	string.split(’,’)[2] 을 해야

	→ ‘name’ 이 나온다.  

<br />

#### 2.  알파벳 하나씩 쪼개기  

	let str= 'codestates'

	str.split('')

	→ ['c', 'o', 'd', 'e', 's', 't', 'a', 't', 'e', 's'] (배열로 리턴)
<br />


	str.split('').reverse() //.reverse()메서드는 배열의 순서 바꾼다

	→ ['s', 'e', 't', 'a', 't', 's', 'e', 'd', 'o', 'c']
<br />


	str.split('').reverse().join() //.join()은 배열 합쳐서 문자열로 리턴하는 메서드

	→ 's,e,t,a,t,s,e,d,o,c'
<br />


	str.split('').reverse().join('')

	→ 'setatsedoc'
<br />


	str.split('').reverse().join('-')

	→ 's-e-t-a-t-s-e-d-o-c'
<br />


	str.split(’’)[0] //하나씩 쪼갠 결과물의 0번째 유닛(알파벳 이외에 띄어쓰기도 카운트 셈)

	→ ‘c’  
<br />


      

#### 3.  복사해서 array로 리턴하기

	let str = ‘codestates’

	str.split()

	→ [’codestates’]  

<br />

# arr.slice 

### ☑️ arr → arr
<br />

❌  slice는 기존 배열을 바꾸지 않는다.
<br />

	str.slice(3);

	문자열 3번째에서 끝까지 긁는다

	(=앞에서 3개를 제거한다)

<br />

<aside> 💡 `str.slice(0,str.length)` 하면 str의 처음부터 끝까지 모든 요소를 보여줌 (콤마나 띄어쓰기도 한자리씩 차지함)

</aside>

```javascript
const str= ('12 33,7  0')
str.slice(0,3)  -> '12 '
str.slice(0,6)  -> '12 33,'

const animals = ['ant', 'bison', 'camel', 'duck', 'elephant']
✅ 앞에서부터 인덱스 세는 법 : 0, 1, 2, 3...
✅ 뒤에서부터 인덱스 세는 법 : -0, -1, -2, -3...

console.log(animals.slice(2));        ▶️ 앞에서 2개만 빼고 추출 (인덱스 2부터 출력)
// expected output: Array ["camel", "duck", "elephant"]
console.log(animals.slice(2, 4));     ▶️ 인덱스 2부터 3까지 추출
// expected output: Array ["camel", "duck"]
console.log(animals.slice(-2));       ▶️ 뒤에서 2개만 추출
// expected output: Array ["duck", "elephant"]  
console.log(animals.slice(2, -1));    ▶️ 인덱스 2부터 뒤에서 인덱스 -1 추출
// expected output: Array ["camel", "duck"]

```

<br />

# arr.splice()

<br />
⭕️ splice는 기존 배열을 변화시킨다.


	arr=[1,2,3,4,5]

	arr.splice(2,1) 하면 index2에서 1개만 쏙 빼고 남은 배열 리턴

	→ [1,2,4,5]



✅  splice는 기존 배열을 변화시키는 메소드이기 때문에 복사해서 새 변수에 할당해야 함 (mutable, 얕은복사)

	const newTags= [...tags]

	newTags.splice(indexToRemove,1)
