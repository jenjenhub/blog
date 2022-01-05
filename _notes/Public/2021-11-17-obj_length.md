---
layout: single
title: "obj의 length 구하기"
---

⚠️ 객체는 .length로 길이를 구할 수 없다.

✅ 그래서 사용하는 게 Object.keys(객체).length



```js
const obj = {a:1, b:2, c:3}
obj.length   // undefined
Object.keys(obj).length   // 3
```

