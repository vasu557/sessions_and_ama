## 1. What is the difference between Fetch and Axios?

| Fetch | Axios |
|--------|--------|
| Built-in browser API | Third-party library |
| No installation required | Requires installation (`npm install axios`) |
| Requires manual JSON conversion using `response.json()` | Automatically converts JSON responses |
| Does not throw errors for HTTP 4xx/5xx responses | Automatically throws errors for HTTP 4xx/5xx responses |
| More verbose syntax | Cleaner and shorter syntax |

### Fetch Example
```js
fetch("/users")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

### Axios Example
```js
axios.get("/users")
  .then((response) => console.log(response.data));
```

### One-Line Answer
**Fetch is a built-in browser API for making HTTP requests, whereas Axios is a third-party library that provides additional features like automatic JSON transformation and better error handling.**

---

## 2. What is the difference between Props and State?

| Props | State |
|--------|--------|
| Passed from parent to child component | Managed within the component |
| Read-only (immutable) | Can be updated using setter functions |
| Used to pass data between components | Used to manage component-specific data |
| Controlled by parent component | Controlled by the component itself |

### Props Example
```js
function Child({ name }) {
  return <h1>{name}</h1>;
}
```

### State Example
```js
const [count, setCount] = useState(0);
```

### One-Line Answer
**Props are used to pass data from parent to child components, while state is used to manage and update data within a component.**

---

## 3. What is Store in Redux?

A **Store** is the central container that holds the entire state of a Redux application.

### Responsibilities of Store
- Stores the application's state.
- Allows access to the state.
- Updates the state through dispatched actions and reducers.
- Notifies subscribed components when the state changes.

### Redux Flow
```text
Component → Dispatch Action → Reducer → Store Updated → UI Re-renders
```

### Store Example
```js
import { configureStore } from "@reduxjs/toolkit";
import userReducer from "./userSlice";

const store = configureStore({
  reducer: {
    user: userReducer,
  },
});
```

### One-Line Answer
**A Redux Store is a centralized place where the application's global state is stored and managed.**

---

## 4. What is the difference between React and Redux?

| React | Redux |
|--------|--------|
| JavaScript library for building user interfaces | State management library |
| Manages UI components | Manages application state |
| Uses props and state | Uses store, actions, and reducers |
| Focuses on rendering UI | Focuses on sharing and updating data |
| Can work without Redux | Usually used with React for large applications |

### Example
```text
React → Creates Login Form UI

Redux → Stores Logged-In User Information
```

### One-Line Answer
**React is used for building user interfaces, while Redux is used for managing and sharing application state across components.**
