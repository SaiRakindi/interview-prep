# Redux Interview questions

Created: November 13, 2024 1:19 PM

### What is Redux?

**Redux** is a predictable state management library for JavaScript applications, primarily used with React but also adaptable to other libraries. It allows you to manage the state of an application in a single place, making it easier to maintain and debug large applications. Redux follows the **unidirectional data flow** principle, where state changes happen in a clear and predictable way.

### Key Principles of Redux

1. **Single Source of Truth**:
    - The entire state of your application is stored in a single JavaScript object (known as the **store**). This makes it easier to manage and debug, as the application state can be inspected and reproduced.
2. **State is Read-Only**:
    - The only way to change the state is by dispatching an **action**, an object that describes what happened. This ensures that no one can mutate the state directly, leading to predictable state transitions.
3. **Changes are Made with Pure Functions (Reducers)**:
    - To specify how the state tree is transformed by actions, you write **reducers**. Reducers are pure functions that take the previous state and the action, and return the new state. They do not mutate the existing state but return a new state object.

### Data Flow in Redux

1. **Action**:
    - An action is an object that describes a state change. Actions are dispatched to trigger changes in the store. Each action must have a `type` property, and it may include additional data (payload) that the reducer needs to modify the state.
    
    ```jsx
    { type: 'ADD_ITEM', payload: { item: 'Product A' } }
    
    ```
    
2. **Reducer**:
    - A reducer is a function that takes the current state and an action, and returns a new state based on the action. Reducers are pure functions, meaning they don’t have side effects or modify the input.
    
    ```jsx
    const initialState = { cart: [] };
    
    function cartReducer(state = initialState, action) {
      switch (action.type) {
        case 'ADD_ITEM':
          return { ...state, cart: [...state.cart, action.payload.item] };
        default:
          return state;
      }
    }
    
    ```
    
3. **Store**:
    - The store holds the application’s state. It is created using the `createStore` function, passing in the root reducer. The store allows state access via `getState()`, dispatching actions via `dispatch(action)`, and subscribing to changes via `subscribe(listener)`.
4. **Dispatch**:
    - To modify the state, actions are dispatched using `dispatch(action)`. This sends the action to the store’s reducer to calculate the new state.
5. **Selector**:
    - Selectors are functions used to extract specific parts of the state from the store. You can use `useSelector` in React to access the necessary state inside a component.

### Sharing Data Between Components

### 1. Sharing Data from **Parent to Child** (Props)

- You can pass data from a parent component to a child component using **props**.

```jsx
// Parent Component
<ChildComponent data={parentData} />

// Child Component
const ChildComponent = ({ data }) => {
  return <div>{data}</div>;
};

```

### 2. Sharing Data from **Child to Parent** (Callback Functions)

- You can share data from a child component to a parent component by passing a **callback function** from the parent to the child and invoking it in the child component with the necessary data.

```jsx
// Parent Component
const ParentComponent = () => {
  const handleDataFromChild = (data) => {
    console.log('Data from child:', data);
  };

  return <ChildComponent sendData={handleDataFromChild} />;
};

// Child Component
const ChildComponent = ({ sendData }) => {
  const data = 'Hello from Child';
  return <button onClick={() => sendData(data)}>Send Data</button>;
};

```

### Key Principles and Data Flow in Redux

- **Unidirectional Data Flow**: In Redux, data flows in a single direction:
    1. The **view** dispatches an **action**.
    2. The **reducer** handles the action and updates the state.
    3. The **view** re-renders based on the updated state.

This ensures that state transitions are predictable and makes the application easier to maintain and debug.

### Redux Components: View, Actions, Reducers

1. **View (React Component)**:
    - The **view** in Redux refers to the React components that display the UI and interact with the user.
    - These components are connected to the Redux store using functions like `useSelector` to read the state and `useDispatch` to trigger actions.
    - When a user interacts with the UI (e.g., clicking a button), the component dispatches an action to request a state change.
    
    Example:
    
    ```jsx
    import React from 'react';
    import { useDispatch, useSelector } from 'react-redux';
    
    const ProductList = () => {
      const products = useSelector((state) => state.products); // Accessing the state from the Redux store
      const dispatch = useDispatch();
    
      const addItemToCart = (product) => {
        dispatch({ type: 'ADD_ITEM', payload: product }); // Dispatching an action
      };
    
      return (
        <div>
          {products.map((product) => (
            <div key={product.id}>
              <h3>{product.name}</h3>
              <button onClick={() => addItemToCart(product)}>Add to Cart</button>
            </div>
          ))}
        </div>
      );
    };
    
    ```
    
2. **Actions**:
    - **Actions** are JavaScript objects that represent an event or intention to modify the state.
    - Every action has a `type` property (a string) that describes what kind of event is happening. Sometimes, actions also carry additional data, known as a **payload**, which provides the necessary information for the state update.
    
    Example of an action:
    
    ```jsx
    const addItemAction = {
      type: 'ADD_ITEM',
      payload: {
        id: 1,
        name: 'Product A'
      }
    };
    
    ```
    
    **Action Creators**:
    These are functions that return actions. Instead of manually creating action objects, action creators make your code cleaner and reusable.
    
    Example:
    
    ```jsx
    const addItem = (product) => {
      return {
        type: 'ADD_ITEM',
        payload: product
      };
    };
    
    ```
    
3. **Reducers**:
    - A **reducer** is a pure function that takes the current state and an action as arguments, and returns the new state based on the action. It **does not mutate the original state**, but returns a new state object.
    
    Reducers are responsible for handling specific parts of the state (e.g., `products`, `cart`). Multiple reducers can be combined into a **root reducer** using `combineReducers`.
    
    Example of a Reducer:
    
    ```jsx
    const initialState = {
      cart: []
    };
    
    const cartReducer = (state = initialState, action) => {
      switch (action.type) {
        case 'ADD_ITEM':
          return {
            ...state,
            cart: [...state.cart, action.payload] // Returning a new state with the added item
          };
        default:
          return state; // If the action is not handled, return the current state
      }
    };
    
    ```
    
4. **Store**:
    - The **store** is the central object in Redux that holds the entire application state.
    - It provides methods like `getState()` to access the current state, `dispatch()` to send actions, and `subscribe()` to listen for changes in the state.
    
    Example of creating a store:
    
    ```jsx
    import { createStore } from 'redux';
    import cartReducer from './reducers/cartReducer';
    
    const store = createStore(cartReducer); // Create the store with the reducer
    
    ```
    

### Making API Calls in Redux

To handle asynchronous operations like API calls in Redux, you typically use **middleware** such as **Redux Thunk** or **Redux Saga**. These tools help manage side effects (like API calls) and allow for more complex action handling.

### Redux Thunk (for API calls)

**Redux Thunk** allows you to write action creators that return a function instead of an action object. This function can perform asynchronous tasks like making API requests and dispatch other actions when the task is complete.

Steps for making API calls with Redux:

1. **Install Redux Thunk**:
    
    ```bash
    npm install redux-thunk
    
    ```
    
2. **Configure Redux Thunk as Middleware**:
In your store setup, apply `thunk` middleware:
    
    ```jsx
    import { createStore, applyMiddleware } from 'redux';
    import thunk from 'redux-thunk';
    import rootReducer from './reducers';
    
    const store = createStore(rootReducer, applyMiddleware(thunk));
    
    ```
    
3. **Create an Asynchronous Action Creator**:
In this example, we will fetch products from an API and dispatch an action to update the store with the fetched products.
    
    ```jsx
    // Action Creator with API Call
    const fetchProducts = () => {
      return async (dispatch) => {
        dispatch({ type: 'FETCH_PRODUCTS_REQUEST' }); // Optional loading state
    
        try {
          const response = await fetch('<https://api.example.com/products>');
          const data = await response.json();
    
          // Dispatch a success action with the fetched data
          dispatch({ type: 'FETCH_PRODUCTS_SUCCESS', payload: data });
        } catch (error) {
          // Dispatch an error action if the API call fails
          dispatch({ type: 'FETCH_PRODUCTS_FAILURE', error: error.message });
        }
      };
    };
    
    ```
    
4. **Reducer to Handle API Data**:
In your reducer, handle different states (loading, success, error) to manage the fetched data.
    
    ```jsx
    const initialState = {
      products: [],
      loading: false,
      error: null
    };
    
    const productReducer = (state = initialState, action) => {
      switch (action.type) {
        case 'FETCH_PRODUCTS_REQUEST':
          return { ...state, loading: true, error: null };
        case 'FETCH_PRODUCTS_SUCCESS':
          return { ...state, loading: false, products: action.payload };
        case 'FETCH_PRODUCTS_FAILURE':
          return { ...state, loading: false, error: action.error };
        default:
          return state;
      }
    };
    
    ```
    
5. **Dispatching the API Call in a Component**:
Now, in your component, you can dispatch the `fetchProducts` action when the component loads (using `useEffect`).
    
    ```jsx
    import React, { useEffect } from 'react';
    import { useDispatch, useSelector } from 'react-redux';
    import { fetchProducts } from './actions/productActions';
    
    const ProductList = () => {
      const dispatch = useDispatch();
      const { products, loading, error } = useSelector((state) => state.product);
    
      useEffect(() => {
        dispatch(fetchProducts()); // Dispatch the API call when the component loads
      }, [dispatch]);
    
      if (loading) return <p>Loading...</p>;
      if (error) return <p>Error: {error}</p>;
    
      return (
        <div>
          {products.map((product) => (
            <div key={product.id}>
              <h3>{product.name}</h3>
            </div>
          ))}
        </div>
      );
    };
    
    ```
    

### Summary

- **View**: React components interact with the store by dispatching actions and subscribing to state changes.
- **Actions**: Objects that describe what happened, sent to the store via `dispatch()`.
- **Reducers**: Pure functions that take the current state and an action, then return a new state.
- **API Calls**: Use middleware like Redux Thunk to handle asynchronous actions such as API requests. This allows you to dispatch actions before, during, and after the API call to manage state accordingly.

By using Redux with Thunk, you can manage both synchronous and asynchronous actions in a predictable, centralized state management system.