---
layout: post
title: Understanding React's useMemo hook
subtitle:
tags: [react, hooks, usememo]
comments: true
---

React's useMemo hook is often misunderstood. This is my attempt to explain it's usage with a simple example.

Here is the code that we are going to start off with,

```jsx
import { useState, useMemo } from "react";

export default function ParentComponent() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  const slowFunction = (count) => {
    for (let i = 0; i < 10000; i++) {
      count += 1;
      for (let i = 0; i < 10000; i++) {
        count += 1;
      }
      for (let i = 0; i < 10000; i++) {
        count += 1;
      }
    }
    console.log(`new count calculated: ${count}`);
    return count;
  };

  const valueFromSlowFunction = slowFunction(count);

  return (
    <div className="App">
      <button onClick={() => setCount(count + 1)}>Update Count</button>
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <p>{valueFromSlowFunction}</p>
    </div>
  );
}
```

So at first glace, there seems to be a lot going on, but let me break it down for you.

We start with two simple React states, one _count_ state, that can be updated with a button click, and a _text_ state that is bound to the input field.

_slowFunction_ is a function that is emulated to be slow. There is a log statement inside the function that prints "new count calculated" which will help us better understand what's going on.
