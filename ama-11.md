# JavaScript / React / SQL Interview Answers

## 1. Adhikya Edammala: What are some JavaScript frameworks?

Popular JavaScript frameworks/libraries are:

- React
- Angular
- Vue.js
- Svelte
- Next.js (React framework)
- Nuxt.js (Vue framework)
- Express.js (Backend framework for Node.js)

---

## 2. Allanki VV Manikanta Sai: Why is React fast?

React is fast because:

- It uses the **Virtual DOM** instead of updating the real DOM directly.
- It compares the old Virtual DOM with the new one (**Diffing**).
- It updates only the changed elements (**Reconciliation**).
- It supports efficient rendering with features like memoization and lazy loading.

---

## 3. Arpit Yadav: What is Hot Reloading?

Hot Reloading updates the application in the browser **without refreshing the page**, while preserving the application's current state.

**Benefits:**
- Faster development
- Instant UI updates
- No need to restart the application

---

## 4. Md Musharaf: What is Prop Drilling?

Prop drilling is the process of passing data from a parent component to a deeply nested child component through intermediate components that do not use the data.

**Problem:**
- Makes code harder to maintain.

**Solution:**
- React Context API
- Redux
- Zustand
- Recoil

---

## 5. Parlapalli Sulochana: What is the use of the `yield` keyword in generators?

The `yield` keyword pauses the execution of a generator function and returns a value. The next call resumes execution from where it stopped.

```javascript
function* numbers() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = numbers();

console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
```

**Use cases:**
- Lazy evaluation
- Iterators
- Processing large datasets
- Infinite sequences

---

## 6. Rovinpal Udupi: What is a Window Function in SQL?

A Window Function performs calculations across a set of rows related to the current row **without grouping the result into a single row**.

**Common window functions:**
- `ROW_NUMBER()`
- `RANK()`
- `DENSE_RANK()`
- `LEAD()`
- `LAG()`
- `SUM() OVER()`
- `AVG() OVER()`

**Example:**

```sql
SELECT
    name,
    salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank
FROM employees;
```

---

## 7. Vikas Mehta: What is `useEffect()`?

`useEffect()` is a React Hook used to perform **side effects** in functional components.

Examples of side effects:
- API calls
- Fetching data
- Timers
- Event listeners
- Updating the document title

**Syntax:**

```javascript
useEffect(() => {
  // Side effect

  return () => {
    // Cleanup (optional)
  };
}, [dependencies]);
```

**Dependency array behavior:**

```javascript
// Runs after every render
useEffect(() => {});

// Runs only once after initial render
useEffect(() => {}, []);

// Runs when count changes
useEffect(() => {}, [count]);
```
