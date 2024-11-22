---
title: "Top React common use cases with code"
date: '2024/12/01'
lastmod: '2022/3/10'
tags: [React, Front-end]
draft: false
summary: "Design patterns are typical solutions to commonly occurring problems in software design.
They are like pre-made blueprints that you can customize to solve a recurring design problem in your code."
images: [/static/images/react.png]
layout: PostLayout
---

- `Props` pass data from parent to child components
```javascript
// ParentComponent.js
import ChildComponent from './ChildComponent';

function ParentComponent() {
    const data = 'Hello from Parent';
    return <ChildComponent message={data} />;
}

// ChildComponent.js
function ChildComponent(props) {
    return <p>{props.message}</p>;
}
```
- `Passing value or function from child to parent component`
```javascript
// ParentComponent.js
import React from 'react';
import ChildComponent from './ChildComponent';

function ParentComponent() {
    const handleChildData = (data) => {
        console.log('Data received from child:', data);
    };

    return (
        <div>
            <ChildComponent sendDataToParent={handleChildData} />
        </div>
    );
}

export default ParentComponent;

// ChildComponent.js
import React from 'react';

function ChildComponent({ sendDataToParent }) {
    const handleClick = () => {
        sendDataToParent('Hello from child');
    };

    return (
        <div>
            <button onClick={handleClick}>Send Data to Parent</button>
        </div>
    );
}

export default ChildComponent;

```
- `State` manage component-specific data
```javascript
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```
- `Data Binding` update UI based on user input
```javascript
import React, { useState } from 'react';

function TwoWayBinding() {
    const [inputValue, setInputValue] = useState('');

    const handleChange = (e) => {
        setInputValue(e.target.value); // Update the state with the new input value
    };

    return (
        <div>
            <input type="text" value={inputValue} onChange={handleChange} />
            <p>Input Value: {inputValue}</p> {/* Display the current value of the input */}
        </div>
    );
}

export default TwoWayBinding;
```
- `Forms`
handle form submissions and user input
```javascript
function FormExample() {
    const handleSubmit = (e) => {
        e.preventDefault();
        console.log('Form submitted');
    };

    return (
        <form onSubmit={handleSubmit}>
            <input type="text" />
            <button type="submit">Submit</button>
        </form>
    );
}
```
- `Ref`
access and manipulate the DOM directly
```javascript
import React, { useRef } from 'react';

function FocusInput() {
    const inputRef = useRef(null);

    const handleClick = () => {
        inputRef.current.focus();
    };

    return (
        <div>
            <input ref={inputRef} type="text" />
            <button onClick={handleClick}>Focus Input</button>
        </div>
    );
}
```
- `UseEffect`  
is used to perform side effects in functional components. There are two part of the effect function:
    - `Effect function`  
      The side effects you want to perform, such as fetching data, subscribing to events, or updating the DOM. By default, this code runs after every render of the component, including the initial render. But with `[]`, it runs only once after mounting. with nothing, effect run after every render. with `[aa, bb]`, it runs after every render of the component, but will only re-run when the value of `aa` or `bb` changes. If `aa` and `bb` remains the same between renders, the effect function will not re-run.
    - `Cleanup function`  
      The return statement in the effect function allows you to specify a cleanup function. This cleanup function is invoked when the component unmounts or before the effect runs again (if dependencies are specified). Its purpose is to clean up any resources or subscriptions created by the effect.  
```javascript
import React, { useState, useEffect } from 'react';

function Timer() {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        const intervalId = setInterval(() => {
            setSeconds(seconds + 1);
        }, 1000);

        return () => clearInterval(intervalId);
    }, [seconds]);

    return <p>Seconds: {seconds}</p>;
}
```
```javascript
useEffect(() => {
    console.log('Component mounted');
    return () => {
        console.log('Component unmounted');
    };
}, []);
```
- `Context`
share data across multiple components without prop drilling
```javascript
import React, { useContext } from 'react';

const ThemeContext = React.createContext('light');

function ThemedButton() {
    const theme = useContext(ThemeContext);
    return <button style={{ background: theme }}>Click me</button>;
}

// In a parent component
<ThemeContext.Provider value="dark">
    <ThemedButton />
</ThemeContext.Provider>
```
- `Conditional Rendering`
```javascript
function Greeting({ isLoggedIn }) {
    return isLoggedIn ? <UserGreeting /> : <GuestGreeting />;
}
```
- `List Rendering`
render lists of data dynamically
```javascript
function TodoList({ todos }) {
    return (
        <ul>
            {todos.map(todo => <li key={todo.id}>{todo.text}</li>)}
        </ul>
    );
}
```
- `Event Handling`
handler user interactions
```javascript
function Button() {
    const handleClick = () => {
        console.log('Button clicked');
    };

    return <button onClick={handleClick}>Click me</button>;
}
```
- `Higher-order Components (HOC)`  
Reuse component logic by wrapping components with higher-order components.
```javascript
function withLogger(WrappedComponent) {
    return function WithLogger(props) {
        console.log('Props:', props);
        return <WrappedComponent {...props} />;
    };
}

const EnhancedComponent = withLogger(MyComponent);
```
- `Lazy-loading`  
Load components dynamically only when needed
```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function MyComponent() {
    return (
        <Suspense fallback={<div>Loading...</div>}>
            <LazyComponent />
        </Suspense>
    );
}
```
