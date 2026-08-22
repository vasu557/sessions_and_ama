## 1. What Happens When We Update the State Directly?

In React, state should never be updated directly. Instead, use the state setter function (`setState` or `setCount`).

### Wrong
```js
count = count + 1;
```

### Correct
```js
setCount(count + 1);
```

### Why?
- React does not detect direct state changes.
- The component may not re-render.
- UI and state can become out of sync.

### One-Line Answer
**If we update state directly, React may not detect the change and the component may not re-render.**

---

## 2. What is Suspense in React?

**Suspense** is a React component used to show a fallback UI (such as a loading spinner) while waiting for a component or data to load.

### Example
```js
<Suspense fallback={<h2>Loading...</h2>}>
  <LazyComponent />
</Suspense>
```

### Benefits
- Improves user experience.
- Handles lazy-loaded components.
- Displays loading states easily.

### One-Line Answer
**Suspense allows React to display a fallback UI while waiting for components or data to load.**

---

## 3. What is Reconciliation in React?

**Reconciliation** is the process React uses to compare the old Virtual DOM with the new Virtual DOM and update only the changed parts in the real DOM.

### Steps
1. State or props change.
2. React creates a new Virtual DOM.
3. React compares it with the previous Virtual DOM.
4. Only the changed elements are updated in the real DOM.

### One-Line Answer
**Reconciliation is React's process of comparing Virtual DOMs and updating only the changed parts of the real DOM.**

---

## 4. What is the Difference Between State and Props?

| State | Props |
|---------|---------|
| Managed inside the component | Passed from parent to child |
| Can be changed | Read-only |
| Used for dynamic data | Used for passing data |
| Updated using setter functions | Cannot be modified by child |

### Example

#### Props
```js
<Child name="Vasu" />
```

#### State
```js
const [count, setCount] = useState(0);
```

### One-Line Answer
**State is managed and updated within a component, while props are read-only data passed from parent to child components.**

---

## 5. What is a Controlled Component?

A **Controlled Component** is a form element whose value is controlled by React state.

### Example
```js
const [name, setName] = useState("");

<input
  value={name}
  onChange={(e) => setName(e.target.value)}
/>
```

### Benefits
- React controls form data.
- Easier validation.
- Predictable behavior.

### One-Line Answer
**A controlled component is a form element whose value is managed by React state.**

---

## 6. What Will We Use to Change Routes in Every Component?

In React Router, we use **useNavigate()** to change routes programmatically from any component.

### Example
```js
import { useNavigate } from "react-router-dom";

function Home() {
  const navigate = useNavigate();

  return (
    <button onClick={() => navigate("/about")}>
      Go to About
    </button>
  );
}
```

### One-Line Answer
**We use the `useNavigate()` hook from React Router to change routes programmatically from a component.**
