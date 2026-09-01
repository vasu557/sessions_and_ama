## 1. Adhikya Edammala — What is useCallback?

`useCallback` is a React Hook used to **memoize a function**.

It returns the same function reference between renders until one of its dependencies changes.

### Syntax

```jsx
const memoizedFunction = useCallback(() => {
  // function logic
}, [dependencies]);
```

### Why do we need useCallback?

Normally, when a component re-renders, functions declared inside the component are created again.

```jsx
function Parent() {
  const handleClick = () => {
    console.log("Clicked");
  };

  return <Child onClick={handleClick} />;
}
```

Every time `Parent` renders, a new `handleClick` function is created.

```text
Render 1 → function A
Render 2 → function B
Render 3 → function C
```

Even though the function does the same thing, each one is a different function reference.

This becomes important when passing functions to a child component that uses `React.memo`.

### Example

```jsx
import { useCallback, useState } from "react";

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        {count}
      </button>

      <Child onClick={handleClick} />
    </>
  );
}
```

Because of `useCallback`, `handleClick` keeps the same reference between renders as long as its dependencies do not change.

### useCallback with dependencies

```jsx
const handleClick = useCallback(() => {
  console.log(count);
}, [count]);
```

Here, whenever `count` changes, React creates a new function because the dependency changed.

### useCallback does NOT prevent re-rendering by itself

This is an important interview point.

`useCallback` does not directly stop a component from rendering.

It mainly keeps a **function reference stable**.

It becomes especially useful together with `React.memo`.

```jsx
const Child = React.memo(function Child({ onClick }) {
  console.log("Child rendered");

  return <button onClick={onClick}>Click</button>;
});
```

If `handleClick` is stable because of `useCallback`, `React.memo` can see that the `onClick` prop has not changed.

### useCallback vs useMemo

| Hook | Memoizes |
|---|---|
| `useCallback` | A function |
| `useMemo` | A calculated value |

Example:

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);

const value = useMemo(() => {
  return expensiveCalculation();
}, []);
```

### When should you use useCallback?

Use it when:

- Passing a callback to a memoized child
- Function reference stability matters
- A function is used as a dependency of another Hook
- Profiling shows unnecessary renders caused by changing function references

Do not use it everywhere automatically. Memoization itself has a cost, so it should provide a real benefit.

### Interview answer

> `useCallback` is a React Hook that memoizes a function and returns the same function reference between renders until its dependencies change. It is mainly useful when function identity matters, especially when passing callbacks to memoized components.

---

# 2. Boorle Sowmya Sri Lakshmi — What is the difference between React and Redux?

React and Redux are **different tools with different responsibilities**.

## React

React is a JavaScript library primarily used for **building user interfaces**.

React deals with things such as:

- Components
- JSX
- Props
- Local state
- Rendering
- Event handling

Example:

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}
```

Here React manages the component and its local state.

---

## Redux

Redux is a **state management library**.

It is mainly useful for managing shared application state.

Examples of shared state:

- Logged-in user
- Shopping cart
- Products
- Notifications
- Application settings
- Authentication state

Redux provides a centralized store:

```text
             Redux Store
                  |
        ---------------------
        |         |         |
       User      Cart     Products
```

Components can read data from the store and dispatch actions to request state changes.

---

## React vs Redux

| React | Redux |
|---|---|
| UI library | State management library |
| Builds components and UI | Manages shared application state |
| Supports local component state | Provides centralized state |
| Uses props to pass data | Uses store/selectors to access shared state |
| Uses hooks such as `useState` | Uses concepts such as actions, reducers, and store |
| Mainly concerned with UI | Mainly concerned with state management |

---

## How React and Redux work together

A typical flow is:

```text
React Component
      |
      | dispatch(action)
      ↓
Redux Store
      |
      ↓
Reducer
      |
      ↓
Updated State
      |
      ↓
React Component
      |
      ↓
UI updates
```

For example:

```jsx
dispatch(addTodo("Learn Redux"));
```

The action is dispatched to Redux.

The reducer processes the action and updates the Redux state.

The React component receives the updated state and the UI updates.

---

## Do we always need Redux with React?

**No.**

Redux is not required to use React.

For simpler applications, React's built-in tools may be enough:

```jsx
useState
useReducer
Context
```

Redux becomes useful when application state becomes more complex or needs to be shared across many parts of the application.

### Interview answer

> React is primarily a library for building user interfaces, while Redux is a state management library used to manage shared application state. They are often used together, but Redux is not required to use React.

---

# 3. Md Musharaf — What is conditional rendering?

**Conditional rendering** means rendering different UI based on a condition.

In simple terms:

> If a condition is true, show one UI; otherwise, show another UI.

---

## Using if

```jsx
function User({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome!</h1>;
  }

  return <h1>Please login</h1>;
}
```

If:

```js
isLoggedIn = true;
```

React renders:

```text
Welcome!
```

If:

```js
isLoggedIn = false;
```

React renders:

```text
Please login
```

---

## Using the ternary operator

The ternary operator is commonly used directly inside JSX.

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

It means:

```text
condition ? true result : false result
```

Example:

```jsx
function App() {
  const isLoggedIn = true;

  return (
    <div>
      {isLoggedIn ? (
        <h1>Dashboard</h1>
      ) : (
        <h1>Login</h1>
      )}
    </div>
  );
}
```

---

## Using `&&`

If you only want to render something when a condition is true:

```jsx
{isLoggedIn && <LogoutButton />}
```

This means:

```text
isLoggedIn = true
    ↓
LogoutButton is rendered

isLoggedIn = false
    ↓
Nothing is rendered
```

---

## Multiple conditions

For multiple conditions, `if` statements or `switch` can make the code easier to understand.

```jsx
function Status({ status }) {
  if (status === "loading") {
    return <p>Loading...</p>;
  }

  if (status === "success") {
    return <p>Data loaded!</p>;
  }

  if (status === "error") {
    return <p>Something went wrong.</p>;
  }

  return null;
}
```

---

## Common conditional-rendering techniques

### `if`

```jsx
if (condition) {
  return <Component />;
}
```

### Ternary

```jsx
condition ? <ComponentA /> : <ComponentB />
```

### Logical AND

```jsx
condition && <Component />
```

### `switch`

```jsx
switch (status) {
  case "loading":
    return <Loading />;

  case "success":
    return <Success />;

  default:
    return null;
}
```

### Interview answer

> Conditional rendering in React means rendering different components or UI elements based on a condition. It can be implemented using `if`, ternary operators, `&&`, or `switch` statements.

---

# 4. Nayunipatruni Harsha Vardhan — What is the difference between DRF and FastAPI?

**DRF** stands for **Django REST Framework**.

DRF and FastAPI are both Python technologies used to build APIs, but they have different architectures and ecosystems.

---

## Django REST Framework

DRF is built on top of Django.

```text
Django
   ↓
Django REST Framework
   ↓
REST API
```

Django provides many built-in features, including:

- ORM
- Authentication
- Admin panel
- Middleware
- Routing
- Security features
- Database integration

DRF adds API-specific functionality such as:

- Serializers
- API Views
- ViewSets
- Routers
- Authentication
- Permissions
- Browsable API

Example:

```python
from rest_framework.views import APIView
from rest_framework.response import Response

class UserView(APIView):
    def get(self, request):
        return Response({"message": "Hello"})
```

---

## FastAPI

FastAPI is a modern Python framework focused on building APIs.

It is built around:

- Python type hints
- Pydantic validation
- Starlette/ASGI
- Automatic API documentation
- Strong async support

Example:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users")
def get_users():
    return {"message": "Hello"}
```

FastAPI automatically provides API documentation such as:

```text
Swagger UI
ReDoc
```

---

## Main differences

| DRF | FastAPI |
|---|---|
| Built on Django | Standalone API framework |
| Uses Django's ecosystem | Has a more focused API ecosystem |
| Django ORM is commonly used | Does not force a specific ORM |
| Uses serializers for validation/transformation | Uses Pydantic models for validation/schema |
| Django architecture | Lightweight API-focused architecture |
| Django Admin available | No built-in Django-style admin |
| Supports async, but Django/DRF has a strong synchronous heritage | Designed with ASGI and async support in mind |
| Excellent for Django applications | Excellent for API-focused applications |

---

## Typical DRF architecture

```text
Client
  ↓
Django URL
  ↓
View / ViewSet
  ↓
Serializer
  ↓
Django ORM
  ↓
Database
```

## Typical FastAPI architecture

```text
Client
  ↓
FastAPI Route
  ↓
Pydantic Validation
  ↓
Service / Business Logic
  ↓
ORM / Database Layer
  ↓
Database
```

---

## When would you choose DRF?

DRF is a strong choice when:

- You already use Django
- You need Django's ORM
- You need Django Admin
- You want Django's batteries-included ecosystem
- Your application is primarily a Django application

---

## When would you choose FastAPI?

FastAPI is a strong choice when:

- You want a focused API framework
- You want strong type hints
- You want automatic API documentation
- You need modern async capabilities
- You want flexibility in choosing your database/ORM architecture

### Important interview point

Do not simply say:

> "FastAPI is better than DRF."

They solve similar API-building problems but belong to different ecosystems and have different design goals.

### Interview answer

> DRF, or Django REST Framework, is an API framework built on top of Django and provides Django's ecosystem, ORM, authentication, admin, and REST-specific features. FastAPI is a modern, API-focused Python framework built around type hints, Pydantic validation, and ASGI, with strong async support and automatic API documentation.

---

# 5. Vikas Mehta — How do you prevent child re-rendering when a parent re-renders?

Normally, when a parent component re-renders, its child components can also render again.

If a child does not need to update, we can use:

```jsx
React.memo()
```

to avoid unnecessary child renders when its props have not changed.

---

## Example without React.memo

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        {count}
      </button>

      <Child />
    </>
  );
}

function Child() {
  console.log("Child rendered");

  return <h1>Child</h1>;
}
```

When `count` changes:

```text
Parent renders
     ↓
Child renders
```

Even though `Child` does not depend on `count`.

---

## Using React.memo

```jsx
const Child = React.memo(function Child() {
  console.log("Child rendered");

  return <h1>Child</h1>;
});
```

Now React can skip rendering the child when its props have not changed.

The flow becomes:

```text
Parent renders
     ↓
Child props unchanged
     ↓
Child render can be skipped
```

---

## Important problem: functions as props

Consider this:

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    console.log("Clicked");
  };

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        {count}
      </button>

      <Child onClick={handleClick} />
    </>
  );
}

const Child = React.memo(function Child({ onClick }) {
  console.log("Child rendered");

  return <button onClick={onClick}>Child</button>;
});
```

Although `Child` uses `React.memo`, the child can still re-render.

Why?

Because every time the parent renders, this function is recreated:

```js
const handleClick = () => {
  console.log("Clicked");
};
```

So React sees:

```text
Previous onClick → function A
New onClick      → function B
```

The references are different.

Therefore:

```text
Props changed
     ↓
Child renders again
```

---

## Solution: React.memo + useCallback

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        {count}
      </button>

      <Child onClick={handleClick} />
    </>
  );
}

const Child = React.memo(function Child({ onClick }) {
  console.log("Child rendered");

  return <button onClick={onClick}>Child</button>;
});
```

Now:

```text
Parent re-renders
       ↓
useCallback returns same function reference
       ↓
Child props unchanged
       ↓
React.memo can skip child render
```

---

## What about objects and arrays?

The same issue can happen with objects and arrays.

Example:

```jsx
<Child user={{ name: "Vasu" }} />
```

A new object is created on every parent render:

```text
Render 1 → object A
Render 2 → object B
Render 3 → object C
```

Even though the contents are the same, the references are different.

If maintaining the reference is actually useful, `useMemo` can be used:

```jsx
const user = useMemo(() => {
  return {
    name: "Vasu"
  };
}, []);

<Child user={user} />
```

---

# Three important tools

## 1. React.memo

Used to skip unnecessary child renders when its props have not changed.

```jsx
const Child = React.memo(ChildComponent);
```

## 2. useCallback

Used to keep a function reference stable.

```jsx
const handleClick = useCallback(() => {
  // logic
}, []);
```

## 3. useMemo

Used to memoize a calculated value or object.

```jsx
const user = useMemo(() => {
  return {
    name: "Vasu"
  };
}, []);
```

---

## Important interview clarification

Do not say:

> "`React.memo` completely prevents the child from rendering."

That is not always true.

`React.memo` is a **performance optimization**.

A memoized component can still render when:

- Its props change
- Its own state changes
- A context it uses changes
- Its parent passes a new object, array, or function reference

### Interview answer

> To prevent unnecessary child re-renders when a parent re-renders, I can wrap the child with `React.memo`. If the child receives functions as props, I can use `useCallback` to keep those function references stable. For objects or calculated values, `useMemo` can sometimes be used to maintain stable references. These are performance optimizations and should be used when they provide a real benefit.

---

