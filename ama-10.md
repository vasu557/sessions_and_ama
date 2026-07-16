# JavaScript, Redis, Celery, Kubernetes & SQL Interview Answers

## 1. Why are we able to use Redis as a message broker?
**Answer:**
Redis supports fast in-memory data structures like **Lists, Streams, and Pub/Sub**, which allow producers to send messages and consumers to receive them. Since all operations happen in memory, Redis is extremely fast and works well as a message broker for tools like Celery.

---

## 2. Difference between `undefined` and `null`

| undefined | null |
|-----------|------|
| Default value assigned by JavaScript | Value assigned intentionally by the programmer |
| Means a variable has not been initialized | Means the variable is intentionally empty |
| Type is `undefined` | Type is `object` (historical JavaScript bug) |

**Example**
```javascript
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null
```

---

## 3. What is Hoisting in JavaScript?

**Answer:**
Hoisting is JavaScript's behavior of moving **variable and function declarations** to the top of their scope before execution.

**Example**
```javascript
console.log(a); // undefined
var a = 10;
```

Internally:
```javascript
var a;
console.log(a);
a = 10;
```

**Note**
- `var` is hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but remain in the **Temporal Dead Zone (TDZ)** until initialized.

---

## 4. Difference between `Promise.any()` and `Promise.all()`

### Promise.all()
- Waits for **all promises** to succeed.
- Rejects immediately if **any one promise fails**.

```javascript
Promise.all([p1, p2, p3]);
```

### Promise.any()
- Returns the **first fulfilled promise**.
- Ignores rejected promises.
- Rejects only if **all promises fail**.

```javascript
Promise.any([p1, p2, p3]);
```

---

## 5. What is Callback Hell?

**Answer:**
Callback Hell is a situation where callbacks are nested inside multiple callbacks, making the code difficult to read, maintain, and debug.

Example:

```javascript
login(function() {
    getUser(function() {
        getOrders(function() {
            makePayment(function() {
                console.log("Done");
            });
        });
    });
});
```

**Solution**
- Promises
- Async/Await

---

## 6. What is `Promise.race()`?

**Answer:**
`Promise.race()` returns the result of the **first promise that settles**, whether it is fulfilled or rejected.

```javascript
Promise.race([p1, p2, p3]);
```

If the fastest promise succeeds → fulfilled.

If the fastest promise fails → rejected.

---

## 7. What is Closure in JavaScript?

**Answer:**
A closure is a function that remembers and can access variables from its outer scope even after the outer function has finished executing.

Example:

```javascript
function outer() {
    let count = 0;

    return function() {
        count++;
        console.log(count);
    };
}

const counter = outer();

counter(); // 1
counter(); // 2
```

Uses:
- Data privacy
- Function factories
- Memoization

---

## 8. Tell some Celery Signals

Some commonly used Celery signals:

- `task_prerun` – Before a task starts.
- `task_postrun` – After a task finishes.
- `task_success` – When a task succeeds.
- `task_failure` – When a task fails.
- `worker_ready` – Worker is ready.
- `worker_shutdown` – Worker is shutting down.
- `beat_init` – Triggered when Celery Beat starts.

---

## 9. What is Event Delegation?

**Answer:**
Event Delegation is a technique where you attach a single event listener to a parent element instead of adding listeners to multiple child elements. It works because of **event bubbling**.

Example:

```javascript
document.getElementById("list").addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
        console.log(e.target.textContent);
    }
});
```

**Benefits**
- Better performance
- Less memory usage
- Works for dynamically added elements

---

## 10. What happens if a Pod crashes in Kubernetes?

**Answer:**
If a Pod crashes:

1. Kubernetes detects the failure.
2. The Pod is marked as failed.
3. The controller (Deployment/ReplicaSet) creates a new Pod automatically.
4. Traffic is redirected to healthy Pods.
5. The application continues running if replicas are available.

This provides **self-healing**.

---

## 11. What are LIMIT and OFFSET in SQL?

### LIMIT
Restricts the number of rows returned.

```sql
SELECT * FROM employees
LIMIT 5;
```

### OFFSET
Skips a specified number of rows before returning results.

```sql
SELECT * FROM employees
LIMIT 5 OFFSET 10;
```

Used for **pagination**.

---

## 12. What is Async JavaScript?

**Answer:**
Async JavaScript allows time-consuming tasks (API calls, file operations, timers) to run **without blocking** the main thread.

Instead of waiting, JavaScript continues executing other code and handles the result later.

Example:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Task Completed");
}, 2000);

console.log("End");
```

Output:

```
Start
End
Task Completed
```

Common async mechanisms:
- Callbacks
- Promises
- Async/Await
- `setTimeout()`
- `fetch()`
