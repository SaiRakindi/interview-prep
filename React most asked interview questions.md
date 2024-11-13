# React most asked interview questions

Created: November 13, 2024 10:25 AM

### 1. **What is React?**

React is a popular JavaScript library for building user interfaces, particularly for single-page applications (SPAs). It allows you to create reusable UI components, making development more efficient. React follows a declarative paradigm, meaning you describe what you want to render, and React takes care of the rendering process behind the scenes.

- **Why use React?**
    - Component-based architecture
    - Virtual DOM for faster rendering
    - Unidirectional data flow
    - Rich ecosystem with hooks, context, and state management solutions (Redux)

### 2. **What is `useMemo`?**

`useMemo` is a React Hook that allows you to memoize expensive calculations or values that don’t need to be recalculated on every render. This improves performance by avoiding unnecessary recalculations.

```jsx
const MyComponent = ({ items }) => {
  const sortedItems = useMemo(() => {
    return items.sort((a, b) => a - b);
  }, [items]);

  return <ul>{sortedItems.map(item => <li key={item}>{item}</li>)}</ul>;
};

```

- **Key Point**: Use `useMemo` for performance optimization when calculations are heavy and you want to avoid recalculating unless dependencies change.

### 3. **What are the features of React?**

- **JSX**: Syntax extension for JavaScript, allowing you to write HTML-like code inside JavaScript.
- **Components**: React allows the building of encapsulated, reusable components.
- **Virtual DOM**: React updates only the changed elements in the DOM, improving performance.
- **Hooks**: Functions like `useState`, `useEffect` allow functional components to have state and lifecycle methods.
- **One-way data binding**: Ensures that data flows from parent to child, making the code predictable.

### 4. **What is JSX?**

JSX stands for JavaScript XML. It allows you to write HTML elements in JavaScript code, and React compiles it into JavaScript. JSX improves readability and keeps logic and UI intertwined.

```jsx
const element = <h1>Hello, world!</h1>;

```

### 5. **What is DOM?**

The DOM (Document Object Model) is a programming interface for web documents. It represents the structure of HTML and XML documents in a tree-like structure, where each element is a node.

### 6. **What is Virtual DOM?**

The Virtual DOM is a lightweight, in-memory representation of the real DOM. React uses the Virtual DOM to figure out what changes need to be applied to the real DOM, optimizing updates and rendering.

### 7. **What is the component lifecycle of React class components?**

Class components have several lifecycle methods:

- **Mounting**: `constructor()`, `componentDidMount()`
- **Updating**: `shouldComponentUpdate()`, `componentDidUpdate()`
- **Unmounting**: `componentWillUnmount()`

```jsx
class MyComponent extends React.Component {
  componentDidMount() {
    // Code to run after the component is rendered
  }
  componentWillUnmount() {
    // Cleanup code before component is removed
  }
  render() {
    return <div>Hello, World</div>;
  }
}

```

### 8. **What are fragments in React?**

Fragments let you group multiple elements without adding extra nodes to the DOM.

```jsx
return (
  <>
    <h1>Title</h1>
    <p>Paragraph</p>
  </>
);

```

### 9. **What are props in React?**

Props (short for "properties") are the read-only inputs passed from parent to child components.

```jsx
const Greeting = (props) => <h1>Hello, {props.name}</h1>;

```

### 10. **What are synthetic events in React?**

Synthetic events are cross-browser wrappers around the native browser events in React, ensuring consistency across different browsers.

```jsx
function handleClick(event) {
  console.log(event.target);
}

<button onClick={handleClick}>Click me</button>;

```

### 11. **What is the difference between `package.json` and `package-lock.json`?**

- **package.json**: Lists dependencies for your project. It specifies what libraries your project requires.
- **package-lock.json**: Records the exact versions of dependencies that are installed. This ensures consistency across different environments.

### 12. **What are the differences between client-side and server-side rendering?**

- **Client-side rendering (CSR)**: The browser downloads a minimal HTML file, then renders the full content using JavaScript. This results in faster interactions after the initial load.
- **Server-side rendering (SSR)**: The HTML is generated on the server with full content and sent to the client, which results in faster initial load but slower subsequent interactions.

### 13. **What is state in React?**

State in React is an object that holds the component's dynamic data. When the state changes, the component re-renders.

```jsx
const [count, setCount] = useState(0);

```

### 14. **What are props?**

Props, or properties, are used to pass data from a parent component to a child component.

### 15. **Differences between State and Props in React?**

- **State**: Managed within the component; mutable.
- **Props**: Passed from parent to child; immutable.

### 16. **What is props drilling?**

Props drilling is the process of passing props through multiple layers of components. This can become cumbersome in large applications.

### 17. **Disadvantages of props drilling and how to avoid it?**

Props drilling can lead to unnecessary complexity and hard-to-maintain code. Use Context API or Redux to manage state globally and avoid drilling.

```jsx
const UserContext = React.createContext();

```

### 18. **What are Pure components in React?**

Pure components only re-render if their props or state change. This prevents unnecessary re-rendering, improving performance.

```jsx
class PureComp extends React.PureComponent {}

```

### 19. **What are Refs in React?**

Refs are used to access DOM elements or React elements directly.

```jsx
const inputRef = useRef();

```

### 20. **What is meant by forward ref?**

`forwardRef` is used to pass refs from a parent to a child component.

```jsx
const MyComponent = React.forwardRef((props, ref) => <input ref={ref} />);

```

Let me know how you'd like to proceed with the remaining questions!

Let's continue with detailed answers and examples for the remaining questions:

### 21. **What are Error Boundaries in React?**

Error Boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the whole app. They catch errors during rendering, in lifecycle methods, and constructors of the whole tree below them.

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.log(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}

```

### 22. **What are Higher Order Components (HOCs) in React?**

HOCs are functions that take a component and return a new component with additional props or behavior. They allow code reuse across components.

```jsx
function withLogger(WrappedComponent) {
  return class extends React.Component {
    componentDidMount() {
      console.log('Component mounted');
    }
    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
}

```

### 23. **Differences between Controlled and Uncontrolled Components?**

- **Controlled Component**: React controls the form element's state.
    
    ```jsx
    const [inputValue, setInputValue] = useState('');
    return <input value={inputValue} onChange={(e) => setInputValue(e.target.value)} />;
    
    ```
    
- **Uncontrolled Component**: The DOM itself handles form element state, and React accesses it using refs.
    
    ```jsx
    const inputRef = useRef();
    return <input ref={inputRef} />;
    
    ```
    

### 24. **What is `useCallback`?**

`useCallback` memoizes a function and only recreates it if the dependencies change. It’s useful for passing stable functions as props to child components.

```jsx
const handleClick = useCallback(() => {
  console.log('Button clicked');
}, []);

```

### 25. **Differences between `useMemo` and `useCallback`?**

- `useMemo`: Memoizes a **value** (result of a function).
- `useCallback`: Memoizes a **function** to prevent it from being re-created unless dependencies change.

### 26. **What are keys in React?**

Keys help React identify which items have changed, been added, or removed when rendering lists. They should be unique and stable.

```jsx
const listItems = items.map(item => <li key={item.id}>{item.name}</li>);

```

### 27. **What is Lazy Loading in React?**

Lazy loading is a technique where components or resources are loaded only when they are needed, improving initial load time. React provides the `React.lazy()` function for this.

```jsx
const LazyComponent = React.lazy(() => import('./MyComponent'));

```

### 28. **What is Suspense in React?**

`Suspense` is a component that lets you display a fallback UI (like a loading spinner) while waiting for a lazy-loaded component to load.

```jsx
<Suspense fallback={<div>Loading...</div>}>
  <LazyComponent />
</Suspense>

```

### 29. **What are Custom Hooks?**

Custom hooks are user-defined hooks that allow logic reuse across multiple components. They’re a way to extract common logic from components.

```jsx
function useFetchData(url) {
  const [data, setData] = useState(null);
  useEffect(() => {
    fetch(url).then(response => response.json()).then(setData);
  }, [url]);
  return data;
}

```

### 30. **What is `useReducer` hook?**

`useReducer` is used to handle complex state logic in React components, similar to Redux’s reducer pattern.

```jsx
const [state, dispatch] = useReducer(reducer, initialState);

```

### 31. **What are Portals in React?**

Portals allow you to render components outside the root DOM node of your app, while still preserving the React tree.

```jsx
ReactDOM.createPortal(<Child />, document.getElementById('modal-root'));

```

### 32. **What is Context in React?**

The Context API provides a way to pass data through the component tree without having to pass props down manually at every level.

```jsx
const ThemeContext = React.createContext('light');

```

### 33. **Practical Question: Example of Context API Usage?**

```jsx
const ThemeContext = React.createContext();

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return <ThemedButton />;
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button className={theme}>I am styled by theme!</button>;
}

```

### 34. **Purpose of Callback Function as an Argument of `setState()`?**

The callback in `setState()` ensures that code is executed after the state has been updated. This is useful when you need to perform an action right after state changes.

```jsx
this.setState({ count: this.state.count + 1 }, () => {
  console.log('State has been updated');
});

```

### 35. **Practical Question: Create a Custom Hook for Increment/Decrement Counter?**

```jsx
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);
  return { count, increment, decrement };
}

function CounterComponent() {
  const { count, increment, decrement } = useCounter(0);
  return (
    <div>
      <button onClick={decrement}>-</button>
      <span>{count}</span>
      <button onClick={increment}>+</button>
    </div>
  );
}

```

### 36. **Which Lifecycle Hooks in Class Components are Replaced by `useEffect`?**

- `componentDidMount`: replaced by `useEffect(() => {}, [])`.
- `componentDidUpdate`: replaced by `useEffect(() => {}, [dependencies])`.
- `componentWillUnmount`: replaced by returning a cleanup function in `useEffect`.

### 37. **What is Strict Mode in React?**

`StrictMode` is a tool for highlighting potential problems in your application. It activates additional checks and warnings for its descendants.

```jsx
<React.StrictMode>
  <App />
</React.StrictMode>

```

### 38. **Different Ways to Pass Data from Child to Parent Component in React?**

- **Callback functions**: Passing a function from parent to child and calling it in the child component.
- **Using Refs**: Passing `useRef` to child components.

### 39. **Practical Question: Send Data from Child to Parent Using Callback Functions**

```jsx
function Parent() {
  const handleDataFromChild = (data) => {
    console.log(data);
  };

  return <Child sendData={handleDataFromChild} />;
}

function Child({ sendData }) {
  return <button onClick={() => sendData("Child Data")}>Send Data</button>;
}

```

### 40. **Practical Question: Send Data from Child Component to Parent Using `useRef`**

```jsx
function Parent() {
  const childRef = useRef();
  const handleClick = () => {
    console.log(childRef.current.value);
  };

  return (
    <div>
      <Child ref={childRef} />
      <button onClick={handleClick}>Get Data</button>
    </div>
  );
}

const Child = React.forwardRef((props, ref) => (
  <input ref={ref} type="text" />
));

```

### 41. **How Do You Optimize Your React Application?**

- **Memoization** (`useMemo`, `React.memo`) to avoid unnecessary re-renders.
- **Lazy loading** components.
- **Use production build** to reduce bundle size.
- **Code-splitting** to load only the necessary parts.
- **Avoid inline functions** in render methods.

### 42. **How Would You Consume a RESTful JSON API in React?**

```jsx
useEffect(() => {
  fetch('<https://jsonplaceholder.typicode.com/posts>')
    .then(response => response.json())
    .then(data => setData(data));
}, []);

```

Let me know if you'd like further breakdowns of the remaining concepts!

Let’s continue with detailed explanations and examples for the remaining questions:

### 43. **Different Design Patterns Used in React?**

- **Component pattern**: React is inherently component-based, where UIs are split into reusable, independent pieces.
- **Higher-Order Component (HOC)**: A function that takes a component and returns a new enhanced component.
- **Render Props pattern**: A function is passed as a prop to render dynamic content inside a component.
- **Container-Presenter pattern**: The separation of business logic (container) from UI rendering (presenter).
- **Custom Hooks**: For sharing logic between components using React hooks.

### 44. **Context API vs Redux?**

- **Context API**: Best for lightweight state sharing without complex logic. It’s part of React, with no extra dependencies.
    - Pros: Simple, minimal setup, no middleware.
    - Cons: Not ideal for large-scale apps or frequent updates.
- **Redux**: A more scalable state management solution that offers a single store for the entire app, ideal for complex state logic.
    - Pros: Middleware support, tools like DevTools, more control over state.
    - Cons: More boilerplate, learning curve, extra dependencies.

### 45. **Prop Types in React (How to Apply Validation on Props in React)?**

PropTypes help you validate the type of props passed to a component during development. It’s useful for catching bugs early.

```jsx
import PropTypes from 'prop-types';

function MyComponent({ name, age }) {
  return (
    <div>
      Name: {name}, Age: {age}
    </div>
  );
}

MyComponent.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
};

```

### 46. **What are React Mixins?**

Mixins were a way to share reusable code between components in older versions of React (before ES6 classes). However, Mixins have been deprecated in favor of HOCs and hooks as they introduced complexity and potential name collisions.

### 47. **What are the Different Hooks You Have Used?**

- **useState**: Manage state in functional components.
- **useEffect**: Handle side effects like data fetching, subscriptions, etc.
- **useRef**: Create persistent references to DOM elements or variables.
- **useContext**: Access context values.
- **useReducer**: Complex state management.
- **useMemo**: Memoize expensive calculations.
- **useCallback**: Memoize functions.
- **useLayoutEffect**: Similar to `useEffect`, but fires synchronously after all DOM mutations.
- **useImperativeHandle**: Customize ref exposure.

### 48. **What are Render Props in React?**

Render props are a pattern in which a function is passed as a prop to a component to control what it renders.

```jsx
function DataFetcher({ render }) {
  const [data, setData] = useState([]);
  useEffect(() => {
    fetch('<https://api.example.com/data>')
      .then(response => response.json())
      .then(setData);
  }, []);
  return render(data);
}

function App() {
  return (
    <DataFetcher render={(data) => (
      <div>{data.map(item => <p key={item.id}>{item.name}</p>)}</div>
    )} />
  );
}

```

### 49. **Different Types of Exports and Imports?**

- **Named exports**: Export multiple components or functions from a file.
    
    ```jsx
    export const myFunction = () => {};
    import { myFunction } from './myFile';
    
    ```
    
- **Default exports**: Only one default export per file.
    
    ```jsx
    export default MyComponent;
    import MyComponent from './MyComponent';
    
    ```
    

### 50. **Differences Between `createElement` vs `cloneElement` in React?**

- **`React.createElement()`**: Used to create new React elements. It’s the underlying function used by JSX.
    
    ```jsx
    const element = React.createElement('div', { className: 'example' }, 'Hello');
    
    ```
    
- **`React.cloneElement()`**: Clones an existing element, allowing you to modify its props or children.
    
    ```jsx
    const newElement = React.cloneElement(existingElement, { className: 'newClass' });
    
    ```
    

### 51. **When to Use `useState` and `useReducer`?**

- **`useState`**: Ideal for simple state that is independent of other state variables.
- **`useReducer`**: Useful for complex state logic involving multiple values or where the next state depends on the previous state.
    
    ```jsx
    const reducer = (state, action) => {
      switch(action.type) {
        case 'increment':
          return { count: state.count + 1 };
        case 'decrement':
          return { count: state.count - 1 };
        default:
          return state;
      }
    };
    
    const [state, dispatch] = useReducer(reducer, { count: 0 });
    
    ```
    

### 52. **What is `flushSync` in React?**

`flushSync` forces React to flush updates synchronously. Normally, React batches state updates and flushes them asynchronously, but `flushSync` allows you to control the timing for specific cases, such as when you need to immediately update the DOM.

```jsx
import { flushSync } from 'react-dom';

flushSync(() => {
  setState(newState);
});

```

These are some comprehensive answers for your interview preparation. Would you like to dive deeper into any specific topic or practical examples?

### 53. **What are Protected Routes in React?**

Protected routes in React are routes that restrict access to certain parts of the application based on specific conditions, such as user authentication. For example, an e-commerce app may have pages like "Profile" or "Checkout" that should only be accessible to logged-in users. Protected routes ensure that only authenticated users can access these pages, while unauthenticated users are redirected to a login page or another relevant page.

### Real-World Scenario

Imagine a banking app where only logged-in users can view their account balance. If an unauthenticated user tries to access the account page, the app redirects them to a login page instead.

### Implementation of Protected Routes

Using `React Router`, we can create protected routes by checking if a user is authenticated before rendering the target component. Here’s an example of implementing a protected route component:

```jsx
import React from 'react';
import { Route, Redirect } from 'react-router-dom';

// Mock authentication function
const isAuthenticated = () => {
  // Normally you would check the user's auth status from context or auth provider
  return !!localStorage.getItem('token');
};

// ProtectedRoute component
const ProtectedRoute = ({ component: Component, ...rest }) => {
  return (
    <Route
      {...rest}
      render={(props) =>
        isAuthenticated() ? (
          <Component {...props} />
        ) : (
          <Redirect to="/login" />
        )
      }
    />
  );
};

export default ProtectedRoute;

```

In this example:

- `ProtectedRoute` checks if the user is authenticated using the `isAuthenticated` function.
- If authenticated, it renders the specified component.
- If not, it redirects the user to the `/login` route.

### Using ProtectedRoute

Now, let’s use `ProtectedRoute` in our app to secure the "Dashboard" route.

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import ProtectedRoute from './ProtectedRoute';
import Dashboard from './Dashboard';
import Login from './Login';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/login" component={Login} />
        <ProtectedRoute path="/dashboard" component={Dashboard} />
      </Switch>
    </Router>
  );
}

export default App;

```

Now, if a user tries to access `/dashboard` without being authenticated, they’ll be redirected to `/login`.

---

### 54. **What is React Router?**

React Router is a standard library for routing in React applications. It enables you to create single-page applications (SPAs) where navigation between pages doesn’t require a full page reload. React Router manages the component rendering based on the current URL, allowing your app to provide a seamless, multi-page experience.

### Key Features of React Router

- **Declarative routing**: Define routes declaratively in your component tree.
- **Nested routing**: Support for defining routes within routes for complex layouts.
- **Dynamic routing**: Allows URLs with dynamic parameters (e.g., `/users/:id`).
- **Navigation methods**: React Router provides components like `<Link>` and `<NavLink>` to navigate between routes without reloading the page.

### Real-World Scenario

Consider an online store where users can view a list of products, see details for each product, and navigate back to the homepage. Using React Router, you can define routes for each page (`/products`, `/products/:id`, `/cart`, etc.) and display the appropriate component for each route.

### Implementation Example

To use React Router, install it via npm:

```bash
npm install react-router-dom

```

Then, create routes in your application:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

function Home() {
  return <h2>Home Page</h2>;
}

function About() {
  return <h2>About Page</h2>;
}

function ProductDetail({ match }) {
  return <h2>Product ID: {match.params.id}</h2>;
}

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link> | <Link to="/products/1">Product 1</Link>
      </nav>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/products/:id" component={ProductDetail} />
      </Switch>
    </Router>
  );
}

export default App;

```

In this example:

- **Home** and **About** are regular routes, accessible via `/` and `/about`.
- **ProductDetail** is a dynamic route, with `:id` representing a route parameter. It can handle URLs like `/products/1`, `/products/2`, etc.
- **`<Link>`** is used to navigate between routes without reloading the page.

### Explanation of Key Components

- **`<Router>`**: Wraps the application to enable routing.
- **`<Switch>`**: Renders the first matched route inside it, preventing multiple matches.
- **`<Route>`**: Defines individual routes and what component to render for each path.
- **`<Link>`**: Used to create navigational links.

### Combining Protected Routes with React Router

You can integrate protected routes within a React Router setup to manage restricted access:

```jsx
function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link> | <Link to="/dashboard">Dashboard</Link>
      </nav>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <ProtectedRoute path="/dashboard" component={Dashboard} />
      </Switch>
    </Router>
  );
}

```

Here, `/dashboard` is a protected route. Only authenticated users will be able to access it; others will be redirected to `/login`.

---

### Summary

- **Protected Routes**: Used to control access to routes based on authentication or other conditions, redirecting unauthorized users.
- **React Router**: A library to handle routing in React applications, enabling single-page application behavior with nested and dynamic routes.

Both concepts are crucial in building secure and scalable React applications that provide smooth navigation and user access management.