---
title: "React 기초 - useEffect"
notetype : feed
date : 23-01-2022
---

<br />

## What does React do?

React renders UI and reacts to user input.
- Render JSX
- Manage State & Props
- React to user event & input
- Re-evaluate components upon State & Prop changes

<br />

## What is a Side Effect?

All actions that are not related to bringing something onto the screen directly.
- Sending HTTP requests (to backend servers)
- Storing data in browser storage
- SetTimeout

### Why differentiate?

- These tasks must happen outside of the normal component evaluation and render cycle - especially since they might block / delay rendering (HTTP requests)

<br />

```js
// import "./App.css";
import React, { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);

  // [] -> 한번만 실행하고 싶다면 = componentDidMount
  useEffect(() => {
    console.log(`컴포넌트가 마운트되었습니다.`);
  }, []);

  // 두번쨰 인자가 없다면 매 리렌더마다 실행
  useEffect(() => {
    console.log(`컴포넌트가 리렌더되었습니다.`);
  });

  // [input] -> input이 변경됐을때에만 실행 = componentDidUpdate
  useEffect(() => {
    console.log(`count가 ${count}로 업데이트 되었습니다.`);
  }, [count]);

  return (
    <div className="App">
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
    </div>
  );
}

export default App;
```
