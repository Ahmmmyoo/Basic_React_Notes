# Basic_React_Notes


**Beginner Notes for React** 

<br>

References: 
- Video: [**React Full Course 2024**](https://www.youtube.com/watch?v=CgkZ7MvWUAA&t=5389s)
- Channel: [**Bro Code**](https://www.youtube.com/@BroCodez)
   
<br>
      
## Chapter 1 - React Tutorial for Beginners

[React Reference Page](https://react.dev/reference/react)

### 1.1 Setup and Installation

**Install Prerequisites**:

- Install [nodejs](https://nodejs.org/en) - JavaScript runtime environment required to run and manage React applications.
- Install [VS Code](https://code.visualstudio.com/) - A popular code editor with extensive support for JavaScript and React.

**Initialize a New React Project using Vite**: Vite is a build tool that provides a faster and leaner development experience for modern web projects.

`npm create vite@latest`

Follow the prompts: 
- **Project name**: `my-react-app`
- **Select Framework**: `React`
- **Select Variant**: `JavaScript`

This will create a new directory called my-react-app with the basic setup for a React project.

### 1.2 Running the React Application

To run the application, navigate to your project directory and install dependencies:

1. `cd my-react-app` - Changes directory to your project folder.
1. `npm install` -  Installs all the dependencies listed in package.json.
1. `npm run dev` - Starts the development server and opens the application in the browser.

### 1.3 Understanding React Components

**What is a React Component?**

A React component is a reusable piece of code that defines how a certain part of your application should appear and behave. Components can be as simple as a button or as complex as an entire page.

**Creating a Header Component**

1. Create a new file named `Header.jsx` in the `./src` directory.

    ```jsx
    // Header.jsx
    import React from 'react';

    const Header = () => {
      return (
        <header>
          <h1>Welcome to My React App</h1>
        </header>
      );
    };

    export default Header;
    ```

2. Add the `Header` component to your main `App.jsx` file.

    First, import the Header component:
    ```jsx
    // App.jsx
    import React from 'react';
    import Header from './Header';

    function App() {
      return (
        <div className="App">
          <Header />
          {/* Other components will go here */}
        </div>
      );
    }

    export default App;
    ```

### 1.4 JSX Syntax and Usage

JSX stands for JavaScript XML. It allows us to write HTML inside JavaScript. It makes it easier to write and add HTML in React.

- **Embedding Expressions in JSX**:

  You can embed any JavaScript expression in JSX by wrapping it in curly braces `{}`:

  ```jsx
  const name = 'React Developer';
  const element = <h1>Hello, {name}</h1>;
  ```

- **Adding Attributes**:

  You can add attributes to JSX elements just like you do in HTML:

  ```jsx
  const link = <a href="https://reactjs.org">Learn React</a>;
  ```

### 1.5 React Props and State

**Props**:

Props are short for properties. They are read-only components that must be kept pure. Props allow you to pass data from a parent component to a child component.

```jsx
// Parent Component
import React from 'react';
import Header from './Header';

function App() {
  return (
    <div>
      <Header title="Welcome to React" />
    </div>
  );
}

// Child Component (Header.jsx)
const Header = (props) => {
  return <h1>{props.title}</h1>;
};

export default Header;
```

**State**:

State is a special object in React components that allows them to react to changes and re-render. Unlike props, state is managed within the component and can be changed asynchronously.

```jsx
import React, { useState } from 'react';

function Counter() {
  // Declare a state variable named 'count' with a default value of 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

### 1.6 React Event Handling

React handles events similarly to HTML, but with some syntactical differences:

- Events are named using camelCase, e.g., `onClick` instead of `onclick`.
- You pass a function as the event handler, not a string.

  ```jsx
  function handleClick() {
    alert('Button clicked!');
  }

  return (
    <button onClick={handleClick}>Click me</button>
  );
  ```

### 1.7 Conditional Rendering

React allows you to conditionally render components based on certain conditions.

```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please sign in.</h1>;
  }
}
```

### 1.8 React Lists and Keys

Lists in React are used to display multiple similar components and are created using the .map() method. Each item in a list should have a unique key prop.

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li key={number.toString()}>{number}</li>);

return <ul>{listItems}</ul>;
```

### 1.9 Forms in React

Forms in React handle inputs using controlled components. The state of each input element is controlled by React.

```jsx
import React, { useState } from 'react';

function MyForm() {
  const [name, setName] = useState('');

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('A name was submitted: ' + name);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}

export default MyForm;
```

### 1.10 Component Lifecycle and Hooks

React components have a lifecycle that consists of mounting, updating, and unmounting. React provides several hooks to work with the lifecycle methods of a component.

**useEffect Hook**: The `useEffect` hook lets you perform side effects in function components.

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]); // Only re-run the effect if count changes

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

### 1.11 Conclusion

React is a powerful library for building user interfaces with components that manage their own state. Understanding the basics of components, JSX, props, state, and hooks is essential for developing efficient and scalable React applications.

In the next chapter, we will dive into **Advanced Component Patterns**

<br>

## Chapter 2 - Advanced Component Patterns

In this chapter, we'll explore advanced component patterns in React that will help you write more reusable, flexible, and maintainable code. Understanding these patterns is crucial as you build larger and more complex React applications.

### 2.1 Functional Components vs. Class Components

**Functional Components**:

- Functional components are simpler and are typically used for presentational purposes.
- They are JavaScript functions that accept props as an argument and return JSX.

  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }
  ```

**Class Components**:

- Class components are ES6 classes that extend `React.Component` and must have a `render` method.
- They are more powerful as they can hold state and have lifecycle methods.

  ```jsx
  class Welcome extends React.Component {
    render() {
      return <h1>Hello, {this.props.name}</h1>;
    }
  }
  ```

**Key Differences**:

- **State and Lifecycle**: Class components were traditionally used for components that manage state and have lifecycle methods. However, with the introduction of Hooks, functional components can also manage state and lifecycle, making them more powerful and preferred for new projects.
- **Simplicity and Readability**: Functional components are more straightforward and easier to read, especially with simpler logic.

### 2.2 Higher-Order Components (HOCs)

A Higher-Order Component (HOC) is an advanced technique in React for reusing component logic. An HOC is a function that takes a component and returns a new component.

**Example of a Higher-Order Component**:

```jsx
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log('Rendering', WrappedComponent.name);
    return <WrappedComponent {...props} />;
  };
}
```

**Usage**:

```jsx
const EnhancedComponent = withLogger(OriginalComponent);
```

**When to Use HOCs**:

- When you need to share behavior across multiple components.
- Useful for cross-cutting concerns like logging, authentication, or error handling.

**Best Practices**:

- Avoid nesting too many HOCs as it can make debugging difficult.
- Ensure the HOC passes through all props to the wrapped component.

### 2.3 Render Props

A component with a render prop takes a function that returns a React element, which is then rendered. This pattern makes it easy to share code between components using a prop that is a function.

**Example of Render Props**:

```jsx
class MouseTracker extends React.Component {
  constructor(props) {
    super(props);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove = (event) => {
    this.setState({
      x: event.clientX,
      y: event.clientY,
    });
  };

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}
```

**Usage**:

```jsx
<MouseTracker
  render={({ x, y }) => (
    <h1>
      The mouse position is ({x}, {y})
    </h1>
  )}
/>
```

**Advantages of Render Props**:

- Provides a flexible way to share code between components.
- Avoids issues of props drilling and state management across multiple components.

**Best Practices**:

- Use descriptive names for render prop functions.
- Be mindful of performance implications due to anonymous functions being re-created on every render.

### 2.4 Controlled vs. Uncontrolled Components

**Controlled Components**:

- Form elements whose values are controlled by React state.
- React state is the "single source of truth" for these elements.

  ```jsx
  class ControlledForm extends React.Component {
    constructor(props) {
      super(props);
      this.state = { input: '' };
    }

    handleChange = (event) => {
      this.setState({ input: event.target.value });
    };

    render() {
      return (
        <input
          type="text"
          value={this.state.input}
          onChange={this.handleChange}
        />
      );
    }
  }
  ```

**Uncontrolled Components**:

- Form elements that maintain their own internal state.
- You access the current value through React refs.

  ```jsx
  class UncontrolledForm extends React.Component {
    constructor(props) {
      super(props);
      this.inputRef = React.createRef();
    }

    handleSubmit = (event) => {
      alert('A name was submitted: ' + this.inputRef.current.value);
      event.preventDefault();
    };

    render() {
      return (
        <form onSubmit={this.handleSubmit}>
          <input type="text" ref={this.inputRef} />
          <button type="submit">Submit</button>
        </form>
      );
    }
  }
  ```

**When to Use Controlled vs. Uncontrolled Components**:

- **Controlled Components**: Preferred when you need to handle or manipulate form data in some way (e.g., validation, conditional logic).
- **Uncontrolled Components**: Useful for simple scenarios where you need less overhead and don't need to manage form data extensively.

### 2.5 Composition vs. Inheritance

**Composition**:

- Composition is a more natural pattern in React than inheritance. Instead of creating a new component by extending another, you build components by combining other components.
- This approach makes your code more modular and reusable.

**Example of Composition**:

```jsx
function FancyBorder(props) {
  return <div className={'FancyBorder FancyBorder-' + props.color}>{props.children}</div>;
}

function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">Welcome</h1>
      <p className="Dialog-message">Thank you for visiting our spacecraft!</p>
    </FancyBorder>
  );
}
```

**Inheritance**:

- While inheritance is used in object-oriented programming to create a new class from an existing class, React recommends composition over inheritance because components are meant to be reusable and composable units.
- Inheritance can lead to tightly coupled components, making your codebase more difficult to maintain and extend.

**Best Practices**:

- Prefer composition over inheritance to create components that are flexible and easier to maintain.
- Use props to pass data and functions down to child components.

### 2.6 Conclusion

Understanding these advanced component patterns is crucial for building scalable and maintainable React applications. By mastering these patterns, you can write more reusable and flexible code, making your React applications more robust and easier to extend.

In the next chapter, we will dive into **State Management in React**, exploring different techniques and libraries to manage state effectively in your applications.

