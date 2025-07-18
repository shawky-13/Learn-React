## Learn React

Some Notes From React Course
This is Link of the Youtube Course : https://www.youtube.com/watch?v=x4rFhThSX04

---------||------------------||------------||--------------------||------------------------||

Q. where does React put all of the elements I create in JSX when i call root.reneder() ?

=> The Elements that i create in JSX are put inside div that has a root id and
converted into a virtural DOM & React compares the real DOM then updates it.

---------||------------------||------------||--------------------||------------------------||

Q. What Would Show up in my console if I were to run this line of code `console.log(<h1>Welcome</h1>)` ?

=> The Output is React Element Object

```
{
    type: "h1",
    props: {children: "welcome"},
    ....
}
```

---------||------------------||------------||--------------------||------------------------||

Q. what's wrong in this code ?

```
root.render(

<h1>wlecome</h1>
<p>hey baby</p>
)
```

=> The problem is that you are trying to render two JSX elements
side by side without wrapping them in a single parent element. JSX expressions must have one parent.

Incorrect:

```
root.render(
<h1>wlecome</h1>
<p>hey baby</p>
)
```

Correct:

```
root.render(
<>
<h1>wlecome</h1>
<p>hey baby</p>
</>
)
```

---------||------------------||------------||--------------------||------------------------||

Q. what does it mean for something to be "declerative" instead of "imperative"?

=> In programming:
Declarative means you describe what you want to happen, not how to do it.

Example: `<h1>Hello</h1>`
(You declare that you want a heading.)

Imperative means you describe how to do something, step by step.

Example:

```
const h1 = document.createElement('h1');
h1.textContent = 'Hello';
document.body.appendChild(h1);
```

(You give instructions for each step.)

Summary:
Declarative: Focus on the result.
Imperative: Focus on the process.

---------||------------------||------------||--------------------||------------------------||

Q. what does it mean for something to be "composable"?

=> In programming, composable means you can build complex things by combining smaller,
reusable pieces together.

For example, in React, you can create small components and then combine (compose) them to make larger UIs.
This makes your code more modular, reusable, and easier to manage.

Summary:
Composable means you can assemble bigger solutions from smaller, independent parts.

---------||------------------||------------||--------------------||------------------------||

Q. What is a React Component ?

=> A React component is a reusable, self-contained piece of code that defines part of a user interface in a React application. Components can be written as JavaScript functions or classes, and they return JSX to describe what should appear on the screen. Components can also accept inputs called props and manage their own state.

Example (function component):

```
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

---------||------------------||------------||--------------------||------------------------||

Q. What is wrong of this code ?

```
function myComponent() {
  return (<small>I'm tiny text</small>);
}
```

=> Component Name Capitalization:
React component names must start with an uppercase letter.
Change mycomponent to MyComponent.

Corrected code:

```
function MyComponent() {
  return (<small>I'm tiny text</small>);
}
```

---------||------------------||------------||--------------------||------------------------||

Q. What is wrong of this code ?

```
function Header() {
  return (<h1>Welcome</h1>);
}

root.render(
Header()
)
```

=>The issue is that you are calling the Header function (Header()) instead of passing it as a component to root.render.

Correct:

```
root.render(
  <Header />
)
```

---------||------------------||------------||--------------------||------------------------||

A Fragment component in React is a special component that lets you group multiple elements without adding an extra node to the DOM.

Why use it?
Sometimes you want to return multiple elements from a component, but React components must return a single parent element. A Fragment solves this without adding an extra `<div>` or other wrapper.

Syntax:

```
import React from 'react';

function Example() {
  return (
    <React.Fragment>
      <h1>Hello</h1>
      <p>This is a fragment.</p>
    </React.Fragment>
  );
}

```

Or, using the shorthand:

```
function Example() {
  return (
    <>
      <h1>Hello</h1>
      <p>This is a fragment.</p>
    </>
  );
}

```

---------||------------------||------------||--------------------||------------------------||

==> Some Notes :

In your React Project, the best practise to create a
components folder insider the src directory. Place all
your reusable component files there.

```
my-project/
└── src/
      ├── App.jsx
      ├── components/
      │     ├── Header.jsx
      │     ├── Main.jsx
      │     └── Footer.jsx
      └── ...
```

---------||------------------||------------||--------------------||------------------------||

Q. what do props help us accomplish ?

=> Props in React help us pass data and configuration from a parent component to a child component.
They allow components to be reusable and customizable by providing different values for each instance.

---------||------------------||------------||--------------------||------------------------||

Q. How do you pass a prop into a component?

=> You pass a prop into a component by adding it as an attribute when you use the component, like this:

```
<MyComponent name="Alice" age={25} />
```

Inside MyComponent, you can access the props with props.name and props.age.

---------||------------------||------------||--------------------||------------------------||

Q. What data type is "props" when the component recieve it ?

=>When a component receives props, the data type of props is a JavaScript object.

---------||------------------||------------||--------------------||------------------------||

Q. What does the .map() array method do ?

=>The .map() array method creates a new array by applying a function to each element of the original array.
It does not change the original array.

Example:

```
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2); // [2, 4, 6]

```

In React, .map() is often used to turn an array of data into an array of components for rendering.

---------||------------------||------------||--------------------||------------------------||

Q.What do we usually use .map() for in React ?

=>We usually use .map() in React to transform an array of data into an array of React elements or components for rendering.
For example, if you have an array of items, you can use .map() to create a list of <li> elements or custom components for each item.

Example:

```
const items = ['a', 'b', 'c'];
return (
  <ul>
    {items.map(item => <li key={item}>{item}</li>)}
  </ul>
);

```

Summary:
.map() is commonly used in React to render lists dynamically from data.

---------||------------------||------------||--------------------||------------------------||

Q.Why is using .map() better than just creating the components manually by typing them out ?

=>Using .map() is better than manually typing out components because it makes your code dynamic, scalable, and maintainable.
With .map(), you can render any number of components based on your data, so if your data changes (more items, fewer items), your UI updates automatically.
Manually typing each component is repetitive and error-prone, especially for large or changing lists.

Summary:
.map() lets you efficiently generate components from data, making your code DRY (Don’t Repeat Yourself) and easier to manage.

---------||------------------||------------||--------------------||------------------------||

Q.You have 2 options for what you can pass in to a state setter function (e.g setCount) . What are they ?

=> You can pass either of these two options to a state setter function like setCount in React:

A value:
Directly set the new state.
`setCount(5);`

A function:
Pass a function that receives the previous state and returns the new state.
`setCount(prevCount => prevCount + 1);`

Summary:
You can pass a new value or a function that calculates the new value based on the previous state.

---------||------------------||------------||--------------------||------------------------||

Q. when would you want to pass the first option ( from answer above ) to the state setter function ?

=>You would want to pass the first option (a direct value) to the state setter function when you already know the exact new value you want to set, and it does not depend on the previous state.

Example:
Resetting a counter to zero:
`setCount(0);`

Setting a value from user input:
`setName(event.target.value);`

Summary:
Use the direct value option when the new state does not rely on the current state.

---------||------------------||------------||--------------------||------------------------||

Q. when would you want to pass the second option ( from answer above ) to the state setter function ?

=>You would want to pass the second option (a function) to the state setter when the new state depends on the previous state.

Example situations:
Incrementing or decrementing a counter:
`setCount(prevCount => prevCount + 1);`

Toggling a boolean value:
`setIsOpen(prev => !prev);`

Updating an array or object based on its previous value:
`setItems(prevItems => [...prevItems, newItem]);`

Summary:
Use the function form when your update relies on the current state value, especially if state updates may be batched or asynchronous.

---------||------------------||------------||--------------------||------------------------||
