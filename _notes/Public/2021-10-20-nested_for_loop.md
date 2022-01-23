---
title: "이중 for문"
notetype : feed
date : 20-10-2021
---

### 두 숫자가 한꺼번에 돌아갈 때 사용하는 이중for문

<br />

#### 👉 이중for문(i,j)과 변수설정(변수,i)의 차이는? 

i,j 있을 때 이중for문은 : 
<br />
i가 0일때, j는 1~9까지 다 돌고 나면 -> i가 1이 되는 구조 (i안에서 j만 끝까지 돌아가고 나서야 i++ 실행) 
<br />

But, 두 숫자가 동시에 동일하게 돌아가야 한다면,
<br />
current변수에 idx[0]를 할당하고, idx[i]를 for문 돌려서 current와 idx[i]를 비교하는 방법을 쓴다 ! (이중 for문 사용 X)
<br />
(current= boxes[i] 처럼 current값은 갱신하여 재할당해주면 된다.)

<br />
<br />

#### 👉 이중 for문 사용 예시

어떤 함수에 '123' 을 인자로 넣었을 때, 11,12,13,21,22,23,31,32,33' 으로 리턴되게 하는 방법은 !?

```javascript

function makePermutations(str) {
  let result= ''
                                                         // <실행순서>
  for (let left = 0; left < str.length; left++) {        //1                          8
    for (let right = 0; right < str.length; right++) {   //2  4  6                    9  11 
      result = result + `${str[left]}${str[right]},`;    //3  5  7(str.length까지 돌면) 10 12 
    }
  }

  return result.slice(0, result.length - 1);
}

```
