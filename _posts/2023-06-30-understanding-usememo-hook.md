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

  const valueFromSlowFunction = useMemo(() => slowFunction(count1), [count1]);

  return (
    <div className="App">
      <button onClick={() => setCount(count + 1)}>Update Count</button>
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <p>{valueFromSlowFunction}</p>
    </div>
  );
}
```

We start with two simple React states, one _count_ state, that can be updated with a button click, and a _text_ state that is bound to the input field.

How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .mx-auto.d-block :}

Here's a code chunk:

```
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code with syntax highlighting:

```javascript
var foo = function (x) {
  return x + 5;
};
foo(3);
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes

You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
