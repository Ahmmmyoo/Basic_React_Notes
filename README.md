# Basic_React_Notes


**Beginner Notes for React** 
\
\
References: 
- Video: [**React Full Course 2024**](https://www.youtube.com/watch?v=CgkZ7MvWUAA&t=5389s)
- Channel: [**Bro Code**](https://www.youtube.com/@BroCodez)


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