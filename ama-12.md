
## 1. What is the use of `useContext`?

`useContext` is a React Hook used to access data from a Context without passing props manually through every component (avoids prop drilling).

**Example:** Theme, logged-in user, language.

---

## 2. What is the use of React?

React is a JavaScript library used to build fast, reusable, and interactive user interfaces using components.

**Benefits:**
- Reusable components
- Virtual DOM for faster rendering
- Easy state management
- One-way data flow

---

## 3. What is React Fiber?

React Fiber is React's new rendering engine introduced in React 16.

**Purpose:**
- Makes rendering faster.
- Splits rendering work into small units.
- Allows React to pause, resume, or prioritize rendering.
- Improves UI responsiveness.

---

## 4. Why do we make components?

Components help us divide the UI into reusable, independent pieces.

**Advantages:**
- Reusability
- Easy maintenance
- Better code organization
- Easier testing

---

## 5. Difference between `<a>` and `<Link>`

| `<a>` | `<Link>` |
|--------|----------|
| HTML tag | React Router component |
| Reloads the entire page | Navigates without page reload |
| Sends a new HTTP request | Uses client-side routing |
| Slower | Faster |
| Used for external links | Used for internal navigation |

**Example**

```jsx
<a href="/about">About</a>

<Link to="/about">About</Link>
```

---

## 6. Difference between `*args` and `**kwargs` (Python)

| `*args` | `**kwargs` |
|----------|------------|
| Stores positional arguments | Stores keyword arguments |
| Data type: Tuple | Data type: Dictionary |

**Example**

```python
def fun(*args):
    print(args)

fun(10, 20, 30)
# (10, 20, 30)
```

```python
def fun(**kwargs):
    print(kwargs)

fun(name="Vasu", age=21)
# {'name': 'Vasu', 'age': 21}
```

---

## 7. What is React Fragment?

A React Fragment lets you group multiple elements without adding an extra HTML element to the DOM.

**Without Fragment**

```jsx
<div>
  <h1>Hello</h1>
  <p>World</p>
</div>
```

**With Fragment**

```jsx
<>
  <h1>Hello</h1>
  <p>World</p>
</>
```

**Why use it?**
- Avoids unnecessary `<div>` elements.
- Keeps the DOM clean.
- Improves readability.

---
