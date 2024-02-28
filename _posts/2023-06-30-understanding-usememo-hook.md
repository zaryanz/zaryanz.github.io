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
import { useState } from "react";

export default function App() {
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

So at first glance, there seems to be a lot going on, but let me break it down for you.

We start with two simple React states, one _count_ state, that can be updated with a button click, and a _text_ state that is bound to the input field. _slowFunction_ is a function that is emulated to be slow and _valueFromSlowFunction_ is the variable that we would store this expensive function's computed value in.

Now using this code, I want you to try to change the value of the input field by typing in something. You would realize right off the bat that the typing feels very laggy. This is because every time you are changing the _text_ state, a re-render is caused in the App component, which causes the expensive function to run and compute _valueFromSlowFunction_ every single time you type in a character.

You would also notice that you get a `new count calculated` log statement in the console a bunch of times, which confirms that the _slowFunction_ is being run every time the _text_ state changes.

The way that we are going to solve this problem is by wrapping the computed value _valueFromSlowFunction_ with the _useMemo_ hook,

```jsx
import { useState, useMemo } from "react";
...
const valueFromSlowFunction = useMemo(() => slowFunction(count), [count]);
...
```

How this works is, by passing in the count state in the dependency array of the _useMemo_ hook, React memoizes the value of _valueFromSlowFunction_ and doesn't re-compute it across re-renders unless the _count_ state in the dependency array changes.

Now, only when you update the count by pressing the "Update Count" button, the value will be computed again.
