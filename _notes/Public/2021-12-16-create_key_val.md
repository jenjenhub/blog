---
layout: single
title:  "배열/객체 안에 key,value쌍 생성하기"
---

### 배열(arr) 안에 key,value쌍 생성하기

```javascript
let something= []
something['name'] = 'Kim'
something['phone']= 'Galaxy'
something;

▶️ [name: 'Kim', phone: 'Galaxy'] 생성 !
```



### 객체(obj) 안에 key,value쌍 생성하기

```javascript
let something = {}
something['name'] = 'Kim'
something['phone']= 'Galaxy'
something;

▶️ {name: 'Kim', phone: 'Galaxy'} 생성 !
```



### 배열과 객체(arr & obj) 안에 key,value쌍 생성하기

```javascript
let something = [{'age':25}]
something['name'] = 'Kim'
something['phone']= 'Galaxy'

▶️ [{…}, name: 'Kim', phone: 'Galaxy']  생성 !
	  0: {age: 25}
	  name: "Kim"
	  phone: "Galaxy"
	  length: 1
```

