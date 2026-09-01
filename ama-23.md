# React & Redux Interview Questions — Answers

## 1. Adhikya Edammala — What is batching in React?

**Batching** in React means React groups multiple state updates together and performs **one re-render** instead of re-rendering after every individual state update.

### Example

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
  };

  return <button onClick={handleClick}>{count}</button>;
}
```

You might expect the count to increase by `3`, but it usually increases by only `1`.

Why?

All three updates use the same value of `count` from the current render:

```js
setCount(0 + 1);
setCount(0 + 1);
setCount(0 + 1);
```

React batches these updates and processes them together.

### Functional updates

If you want each update to use the **latest state**, use a functional update:

```jsx
setCount(prev => prev + 1);
setCount(prev => prev + 1);
setCount(prev => prev + 1);
```

Now the count increases by `3`.

The updates are effectively processed like:

```text
0 → 1 → 2 → 3
```

### Why batching is useful

Batching:

- Reduces unnecessary re-renders
- Improves performance
- Groups related state updates into one render

### Interview answer

> **Batching in React is the process of grouping multiple state updates together so React can process them in a single render, improving performance and avoiding unnecessary re-renders.**

---

## 2. Boorle Sowmya Sri Lakshmi — What is lifting state up?

**Lifting state up** means moving state from a child component to their **closest common parent** so that multiple child components can share and synchronize that state.

### Problem

Suppose two sibling components need the same data:

```text
Parent
 ├── Input
 └── Display
```

If `Input` owns the state, `Display` cannot directly access it.

Instead, move the state to the parent:

```text
Parent
 ├── Input
 └── Display
```

The parent owns the state and passes data/functions to both children.

### Example

```jsx
function Parent() {
  const [name, setName] = useState("");

  return (
    <>
      <Input name={name} setName={setName} />
      <Display name={name} />
    </>
  );
}

function Input({ name, setName }) {
  return (
    <input
      value={name}
      onChange={e => setName(e.target.value)}
    />
  );
}

function Display({ name }) {
  return <h2>Hello {name}</h2>;
}
```

Here:

```text
Parent
  ↓ state
Input      Display
  ↓          ↑
updates     receives
```

The parent is the **single source of truth**.

### Why do we lift state up?

We lift state when:

- Multiple components need the same state
- Sibling components need to communicate
- We want one source of truth
- We want to keep related state synchronized

### Interview answer

> **Lifting state up means moving shared state to the closest common parent of the components that need it, then passing the state and update functions down through props.**

---

## 3. Md Musharaf — What is the use of `useDispatch()`?

`useDispatch()` is a React-Redux hook used to get the **dispatch function** from the Redux store.

We use `dispatch()` to send an **action** to Redux.

### Example

```jsx
import { useDispatch } from "react-redux";
import { addTodo } from "./todoSlice";

function Todo() {
  const dispatch = useDispatch();

  const handleAdd = () => {
    dispatch(addTodo("Learn Redux"));
  };

  return <button onClick={handleAdd}>Add Todo</button>;
}
```

The flow is:

```text
Component
   ↓
dispatch(action)
   ↓
Redux Store
   ↓
Reducer
   ↓
State changes
   ↓
Components receive updated state
```

For example:

```js
dispatch(addTodo("Learn Redux"));
```

`addTodo("Learn Redux")` creates an action.

Conceptually:

```js
{
  type: "todo/addTodo",
  payload: "Learn Redux"
}
```

Redux sends that action to the appropriate reducer.

### `useDispatch()` vs `useSelector()`

| Hook | Purpose |
|---|---|
| `useDispatch()` | Send actions / update Redux state |
| `useSelector()` | Read data from Redux state |

Example:

```jsx
const dispatch = useDispatch();

const todos = useSelector(state => state.todo.todos);

dispatch(addTodo("Learn Redux"));
```

Here:

- `useSelector()` **reads**
- `dispatch()` **sends an action**

### Interview answer

> **`useDispatch()` is a React-Redux hook that gives us access to the Redux store's dispatch function. We use it to dispatch actions that can cause Redux state to change through reducers.**

---

## 4. Nayunipatruni Harsha Vardhan — What is a reducer in Redux?

A **reducer** is a function that determines how the Redux state should change when an action is dispatched.

The basic idea is:

```text
Previous State + Action
        ↓
     Reducer
        ↓
    New State
```

### Example

```js
const initialState = {
  count: 0
};

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case "counter/increment":
      return {
        ...state,
        count: state.count + 1
      };

    default:
      return state;
  }
}
```

If we dispatch:

```js
dispatch({
  type: "counter/increment"
});
```

Redux sends the action to the reducer.

The reducer sees:

```js
action.type === "counter/increment"
```

and returns the updated state:

```js
{
  count: 1
}
```

### Reducer using Redux Toolkit

With Redux Toolkit, reducers are usually written inside a slice:

```js
const counterSlice = createSlice({
  name: "counter",

  initialState: {
    count: 0
  },

  reducers: {
    increment: state => {
      state.count += 1;
    }
  }
});
```

You may wonder:

> "Isn't modifying state directly?"

Redux Toolkit uses **Immer** internally, so this syntax is converted into an immutable state update.

### Important rule

A reducer should be:

- Predictable
- Synchronous
- Based on the previous state and action
- Free from side effects

A reducer should **not** perform things such as:

```js
fetch(...)
localStorage.setItem(...)
setTimeout(...)
```

Those operations belong elsewhere, such as middleware/thunks or other application logic.

### Interview answer

> **A reducer in Redux is a function that receives the current state and an action and determines what the next state should be. It contains the state-update logic for the actions dispatched to Redux.**

---

## 5. Vikas Mehta — What is stale closure in React?

A **stale closure** happens when a function created during an earlier render keeps referring to **old values from that render**, even though the component's state has changed.

This happens because JavaScript closures remember the variables from the scope in which the function was created.

### Example

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setTimeout(() => {
      console.log(count);
    }, 3000);
  };

  return (
    <>
      <p>{count}</p>

      <button onClick={handleClick}>
        Log Count
      </button>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
}
```

Suppose:

```text
count = 0
```

You click **Log Count**.

Then before 3 seconds pass, you click **Increment** several times:

```text
0 → 1 → 2 → 3
```

After 3 seconds, the timeout may print:

```text
0
```

Why?

The callback created when `count` was `0` captured that value.

It doesn't automatically change to the latest value just because the component rendered again.

That's a **stale closure**.

---

### Common stale-closure problem with `useEffect`

Consider:

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const id = setInterval(() => {
      console.log(count);
    }, 1000);

    return () => clearInterval(id);
  }, []);

  return <button onClick={() => setCount(count + 1)}>
    {count}
  </button>;
}
```

Because the dependency array is:

```js
[]
```

the effect runs only once.

The interval callback therefore keeps the `count` value from that initial render.

### Fix 1: Add the dependency

```jsx
useEffect(() => {
  const id = setInterval(() => {
    console.log(count);
  }, 1000);

  return () => clearInterval(id);
}, [count]);
```

Now the effect is recreated when `count` changes.

### Fix 2: Functional state updates

When the problem is updating state based on previous state, use:

```js
setCount(prev => prev + 1);
```

instead of:

```js
setCount(count + 1);
```

This is especially useful for asynchronous callbacks.

### Fix 3: `useRef` for the latest value

Sometimes you need a long-lived callback to access the latest value without recreating the callback.

A ref can hold the latest value:

```jsx
const countRef = useRef(count);

useEffect(() => {
  countRef.current = count;
}, [count]);
```

Then:

```js
console.log(countRef.current);
```

can access the latest stored value.

### Important distinction

A stale closure is **not** a React bug.

It comes from the interaction between:

1. JavaScript closures
2. React's render model
3. Functions capturing values from a particular render

Each render creates its own snapshot of props and state.

### Interview answer

> **A stale closure occurs when a callback captures state or props from an older render and later uses that outdated value. It commonly appears with timers, intervals, event handlers, and effects. We can often solve it using correct effect dependencies, functional state updates, or refs when appropriate.**

---

# Quick Revision

| Question | Short Answer |
|---|---|
| **Batching** | React groups multiple state updates into fewer renders. |
| **Lifting state up** | Move shared state to the closest common parent and pass it through props. |
| **`useDispatch()`** | Gives access to Redux's `dispatch()` function for sending actions. |
| **Reducer** | Determines the next Redux state based on the current state and dispatched action. |
| **Stale closure** | A callback uses old state/props captured from an earlier render. |

# One-Line Interview Revision

### Batching
> React groups multiple state updates together to reduce unnecessary re-renders.

### Lifting State Up
> Move shared state to the closest common parent so multiple children can use the same source of truth.

### `useDispatch()`
> `useDispatch()` gives a component the Redux `dispatch` function to send actions to the store.

### Reducer
> A reducer determines how Redux state changes in response to dispatched actions.

### Stale Closure
> A stale closure occurs when a callback retains and uses state or props from an older render.
