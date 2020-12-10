# Ultimate React Cheatsheet

## Resources

### Starting Point:

- React documentation: [Getting Started – React](https://reactjs.org/docs/)
- Structuring a React app: [File Structure – React](https://reactjs.org/docs/faq-structure.html)
- React API: [React Top-Level API – React](https://reactjs.org/docs/react-api.html)
- Thinking In React: [Thinking in React – React](https://reactjs.org/docs/thinking-in-react.html)
- Tutorial: [Hello World – React](https://reactjs.org/docs/hello-world.html)

### Free Courses:

- Learn modern React through 58 interactive screencasts: [React Tutorial: Learn React JS - Free 4-Hour Course](https://scrimba.com/learn/learnreact)
- Learn React (Codecademy): [ReactJS Tutorial Part I: Learn ReactJS For Free \| Codecademy](https://www.codecademy.com/learn/react-101)
- React: Getting Started (Pluralsight): [React Course: Getting Started \| Pluralsight](https://www.pluralsight.com/courses/react-js-getting-started)
- Front-end Web Development With React (Coursera): [Front-End Web Development with React \| Coursera](https://www.coursera.org/learn/front-end-react)

### Paid Courses:

- Epic React - Kent C. Dodds: [Get Really Good at React \| Epic React by Kent C. Dodds](https://epicreact.dev/)
- Learn React Using Hooks to Build Real-World Applications - Brain Holt (Frontend Masters): [Learn React Using Hooks to Build Real-World Applications with Brian Holt](https://frontendmasters.com/courses/complete-react-v5/)
- Modern React + Redux by Stephen Grider (Stephen has been updating this course since 2016, highly recommended to pick up. Udemy often has massive monthly sales so you can usually pick this course up for $14): [Modern React with Redux Training Course \| Udemy](https://www.udemy.com/course/react-redux/)

### Books:

- Learning React, 2nd Edition (2020) - O'Reilly [paperback]: [Learning React, 2nd Edition [Book]](https://www.oreilly.com/library/view/learning-react-2nd/9781492051718/)
- Pure React, 4th Edition (2020) - Dave Ceddia [PDF, ePub, and MOBI]: [Pure React](https://daveceddia.com/pure-react/)
- Road to React - Robin Wieruch [PDF, MOBI & EPUB]: [Road to React](https://www.roadtoreact.com/)

### Articles And Blogs:

- The Missing Introduction To React: [The Missing Introduction to React \| by Eric Elliott | JavaScript Scene | Medium](https://medium.com/javascript-scene/the-missing-introduction-to-react-62837cb2fd76)
- 7 Architectural Attributes of a Reliable React Component: [7 Architectural Attributes of a Reliable React Component](https://dmitripavlutin.com/7-architectural-attributes-of-a-reliable-react-component/#1-single-responsibility)
- Best Practices With React Hooks: [Best Practices with React Hooks. Ordering hooks, using the right linter… \| by Nathan Sebhastian | Oct, 2020 | Bits and Pieces](https://blog.bitsrc.io/best-practices-with-react-hooks-69d7e4af69a7)
- Methods Of Improving And Optimizing Performance In React Apps: [Methods Of Improving And Optimizing Performance In React Apps — Smashing Magazine](https://www.smashingmagazine.com/2020/07/methods-performance-react-apps/)

### Other Resources:

- Exhaustive list of React resources: [React Resources](https://reactresources.com/)
- Devhints React Cheatsheet: [React.js cheatsheet](https://devhints.io/react)
- Awesome React - The final list of curated React resources you'll ever need: [GitHub - enaqx/awesome-react: A collection of awesome things regarding React ecosystem](https://github.com/enaqx/awesome-react)

## Getting Started

### React Packages
```js
npm install --save react // The main library APIs
npm install --save react-dom // The bindings between React and the browser DOM
```

### Create React App (CRA)

[Create React App](https://github.com/facebook/create-react-app) is an opinionated templating tool for creating comfortable environments for learning React. It's the easiest way to begin a new single-page application in React. Requires Node >= 8.10 and npm >= 5.6 installed on your machine.

From the [React docs](https://github.com/facebook/create-react-app):
> It sets up your development environment so that you can use the latest JavaScript features, provides a nice developer experience, and optimizes your app for production.

```js
// bootstrap a new project with create-react-app
npx create-react-app your-project-name

// navigate into the project and start running on localhost:3000
cd your-project-name
npm start
```
_(Unfamiliar with npx? Read more about it [here](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b))_

If you prefer to work with TypeScript, you can visit [this page](https://create-react-app.dev/docs/adding-typescript/) to read about adding TS during installation or to a pre-existing application.

## Components

Historically, React was divided between two different types of components: function components & class components. This was because functional components were intended to be pure UI functions—given a set of inputs, it should always return the same output. Class components provided lifecycle methods, state, and other side effects through the [Component API](https://reactjs.org/docs/react-component.html). Since the release of [React Hooks in React v16.8.0](https://reactjs.org/docs/hooks-intro.html), it's now possible to include lifecycles/state into functional components, rendering class components practically obsolete.


### Creating A Function Component

```jsx
import React from 'react'; // not needed in React v17+

function FirstComponent() {
  return (
    <p>My First Component</p>
  );
}

export default FirstComponent;
```
#### Snippet Notes:

- Line 3: Can use either `function FirstComponent() {}` or `const FirstComponent = () => {}`. Learn more about the differences between regular functions and arrow functions [here](https://flaviocopes.com/javascript-functions-vs-arrow-functions/).
- Line 4: Every component must return a valid React element (or null).
- Line 9: The default export for this file. Want to learn more about the module system? [Introduction to ES6 Modules](https://medium.com/backticks-tildes/introduction-to-es6-modules-49956f580da).

### Creating A Class Component
```jsx
import React from 'react';

class SecondComponent extends React.Component {
  render() {
    return (
      <p>My Second Component</p>
    );
  }
}

export default SecondComponent;
```
#### Snippet Notes:
- Line 3: Here we use the [ES6 class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) syntax which should function similarly to classes in other OOP languages. You must extend from [React.Component](https://reactjs.org/docs/react-component.html) to create an instance of a React class.
- Line 4: Render is the only function you must define in a React.Component subclass. This contains the rendering logic of the component (which, similarly to the previous example, must return a React element or null).

##### Additional reading:

- [Components and Props – React](https://reactjs.org/docs/components-and-props.html)
- [React.Component – React](https://reactjs.org/docs/react-component.html)
- [Understanding Functional Components vs. Class Components in React - Twilio](https://www.twilio.com/blog/react-choose-functional-components)

## JSX

If you're familiar with front-end web development, you may recognize the syntax used to build components and may (understandably) think it's using HTML. In fact, it's actually using an HTML-like syntactical extension to JavaScript known as JSX (JavaScript XML). It's a syntactical sugar that works well for representing the tree-shaped hierarchy of components in an application. It's entirely possible to write components in pure JavaScript without this extension, but it's not recommended.

Under the hood, JSX is an abstraction over `React.createElement()` calls:

```jsx
React.createElement(
  type,
  [props],
  [...children]
)
```
The first argument is the type—this will be the corresponding HTML or React element that eventually gets created (`div`, `p`, `img`, etc). The second argument is any properties to pass to the component (more on props later). The final argument is any children belonging to this component. This will be anything nested within the element. The following example shows the JavaScript version of a component with its JSX counterpart:

```jsx
React.createElement('div', { id: 'main' },
  React.createElement('h1', null, 'Hello World!'),
  React.createElement('p', null, 'My paragraph element')
);

<div id="main">
  <h1>Hello World!</h1>
  <p>My paragraph element</p>
</div>
);
```
You can see how JSX is a huge improvement to the developer experience.

Because JSX is a syntactical extension of JavaScript, browsers can't natively interpret it. Therefore it needs to be transpiled into something browsers can understand. You'll need a transpiler like [Babel](https://babeljs.io/docs/en/) to handle converting your code into backward-compatible JavaScript. If you're using create-react-app, this is all already handled for you under the hood.

Note: It's important to be aware of the [JSX Gotchas](https://reactjs.org/docs/jsx-in-depth.html).


##### Additional Reading:

- [Getting Started With JSX](https://flaviocopes.com/jsx/)
- [Introducing JSX – React](https://reactjs.org/docs/introducing-jsx.html)
- [JSX In Depth – React](https://reactjs.org/docs/jsx-in-depth.html)
- [React.createElement()](https://reactjs.org/docs/react-api.html#createelement)

## Props

In React, data flows unidirectionally. This pattern comes from the [Flux Architecture](https://facebook.github.io/flux/) designed by Facebook for building their client-side web applications (which complements the composable nature of React's view components). This can be a much different experience for developers who are used to working with frameworks that offer two-way data binding. This means data has only one way to be transferred to other parts of the application: from a parent to its children.

```jsx
function ComponentOne() {
  return (
    <ComponentTwo text="Hello World!" />
  );
}

function ComponentTwo(props) {
  console.log(props.text); // Hello World!

  return (
    <p>{props.text}</p>
  );
}
```

Props are read-only—a component may never modify its own props. This is to avoid any ambiguity in the flow of data; if a child component were to mutate its props, it would break the rule of unidirectional data flow (a child modifying data belonging to its parent). 

##### Additional Reading:

- [Unidirectional Data Flow in React](https://flaviocopes.com/react-unidirectional-data-flow/)
- [Flux Docs \| Flux](https://facebook.github.io/flux/)
- [Components and Props – React](https://reactjs.org/docs/components-and-props.html)
- [Composition vs Inheritance – React](https://reactjs.org/docs/composition-vs-inheritance.html)

## PropTypes

PropTypes is a runtime typechecking library (although static analysis can be achieved through additional tooling with [eslint](https://www.npmjs.com/package/eslint)). This allows you to develop type-safe component APIs, reducing the surface area for errors in your application. PropTypes was once part of the core React library but was eventually moved into a separate package.

```jsx
npm install --save prop-types
```

To add typechecking to a component, you can attach an object of types (matching the expected props) to the component's prototype:

```jsx
import PropTypes from 'prop-types';

function Greeting({ name }) {
  return (
    <div>Hello, {name}</div>
  );
}

Greeting.propTypes = {
  name: PropTypes.string
}

export default Greeting;
```
Note: passing the wrong type will only log an error to the console and won't interrupt the application from running, therefore it's important to be diligent in making sure your prop types are valid. If you prefer stricter compile-time typechecking, you can look into a solution like [TypeScript](https://www.typescriptlang.org/).

For a more exhaustive list of available types, click [here](https://reactjs.org/docs/typechecking-with-proptypes.html#proptypes).

##### Additional Reading:

- [Typechecking With PropTypes – React](https://reactjs.org/docs/typechecking-with-proptypes.html)
- [PropTypes GitHub page](https://github.com/facebook/prop-types)

## State

So far we've been rendering static components, but modern applications are far more sophisticated and require interaction and dynamic updates. We should be able to react to when data changes and update the components that need to know. We can achieve this through state. State is owned by a single component—this is to encapsulate the implementation details of a component while providing props to control its behavior.

In functional components, we can add state by using the `useState` hook:

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  function incrementCount() {
    setCount(count + 1);
  }

  return (
    <React.Fragment>
      <button onClick={incrementCount}>Increment</button>
      <p>{count}</p>
    </React.Fragment>
  );
}
```
#### Snippet Notes:
- Line 4: This is "destructuring" two properties from our call to `useState()`. Destructuing is a powerful feature of JavaScript ES6 that allows you to pull properties from an object or array and assign them to variables. Here useState is returning an array of two properties: [value, setter]. `const [count, setCount]` is assigning the matching indices from the array - value to `count`, and setter to `setCount`. Read more about destructuring [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment). Note: whatever you pass as an argument into `useState()` will be used as the initial value (in this case, 0 for `count`).
- Line 7: Since state is immutable, the only way we can update count's value' is by using the `setCount` function returned from `useState`. The value of `count` will persist through each render, so `count + 1` will always be referring to the most recent value.
- Line 11: We're using `<React.Fragment>`
- Line 12: We’re attaching our `incrementCount` function to the `onClick` button handler. This is a declarative way of attaching an event listener in React.
- Line 13: Inside of JSX we can execute JavaScript expressions by using curly braces `{ }`. In this case, we're accessing the current value of `count`. On the first run of this component, this will return `<p>0</p>`.

If any children require knowledge of the current count value, it can be passed down as props. If two components need to share this state, then the state should be moved up to a common ancestor, and then pass it down into every component that needs the value. Note: there are popular state management libraries that introduce a concept of a centralized state store into React for any data that needs to be accessed in separate branches of the React tree.

```js
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  function incrementCount() {
    setCount(count + 1);
  }

  return (
    <React.Fragment>
      <button onClick={incrementCount}>Increment</button>
      <PrintCount count={count} />
      <PrintCountPlusOne count={count} />
    </React.Fragment>
  );
}

function PrintCount({ count }}) {
  return <p>{count}</p>
}

function PrintCountPlusOne() {
  return <p>{count + 1}</p>
}
```
This is not a useful example, but you can see that since both sub-components have a dependency on the count state, we need to make sure that the component which owns the state is a common ancestor of both.

##### Additional Reading:

- [State and Lifecycle – React](https://reactjs.org/docs/state-and-lifecycle.html)
- [The React State](https://flaviocopes.com/react-state/)
- [Lifting State Up – React](https://reactjs.org/docs/lifting-state-up.html)
- [Using the State Hook – React](https://reactjs.org/docs/hooks-state.html)

