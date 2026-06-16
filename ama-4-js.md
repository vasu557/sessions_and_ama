### 1. Why do we use stopPropagation()?
`stopPropagation()` stops an event from moving to parent elements.

```js
button.addEventListener("click", (e) => {
    e.stopPropagation();
});
```

Without it, clicking the button may also trigger the parent's click event.

---

### 2. Difference between .map() and .forEach()

| .map() | .forEach() |
|---------|-----------|
| Returns a new array | Returns undefined |
| Used when transforming data | Used for iteration |
| Does not modify original array | Usually used for side effects |

```js
let arr = [1,2,3];

arr.map(x => x * 2);      // [2,4,6]
arr.forEach(x => console.log(x)); // prints values
```

---

### 3. What is Null Coalescing Operator (??)?

Returns the right value only if the left value is `null` or `undefined`.

```js
let name = null;
console.log(name ?? "Guest");
```

Output:
```js
Guest
```

---

### 4. Why do we use debugger keyword in JS?

It pauses code execution and opens debugging mode in browser DevTools.

```js
let a = 10;
debugger;
let b = 20;
```

Execution stops at `debugger`.

---

### 5. What do Microtask Queue and Callback Queue store?

**Microtask Queue**
- Promise callbacks
- MutationObserver

```js
Promise.resolve().then(() => console.log("Microtask"));
```

**Callback Queue**
- setTimeout
- setInterval
- DOM events

```js
setTimeout(() => console.log("Callback"), 0);
```

Microtasks execute before callback queue tasks.

---

### 6. What is a Closure?

A closure is a function that remembers variables from its outer scope even after the outer function has finished executing.

```js
function outer() {
    let count = 0;

    return function inner() {
        count++;
        console.log(count);
    };
}

const fn = outer();
fn(); // 1
fn(); // 2
```

---

### 7. How to convert JS String to JS Object?

Use `JSON.parse()`.

```js
let str = '{"name":"Vasu","age":21}';

let obj = JSON.parse(str);

console.log(obj.name);
```

Output:
```js
Vasu
```

---

### 8. Difference between Event Bubbling and Event Capturing

**Event Bubbling**
- Event moves from child → parent.

```text
Button → Div → Body
```

**Event Capturing**
- Event moves from parent → child.

```text
Body → Div → Button
```

Bubbling is the default behavior.

---

### 9. What is Event Delegation?

Attaching a single event listener to a parent element to handle events for its children.

```js
ul.addEventListener("click", (e) => {
    console.log(e.target.innerText);
});
```

Benefits:
- Better performance
- Less memory usage
- Works for dynamically added elements

---

### 10. Why do we use Promises?

Promises handle asynchronous operations and avoid callback hell.

```js
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

Promise States:
- Pending
- Fulfilled
- Rejected

---

### 11. What HTTP Method is used to Archive instead of Delete?

There is no special HTTP method called "Archive".

Common practice:
- Use `PATCH` or `PUT`
- Update status to `"archived"`

```http
PATCH /tasks/1

{
  "status": "archived"
}
```

---

### 12. What is Set in JavaScript?

`Set` is a collection of unique values.

```js
let nums = new Set([1,2,2,3,3]);

console.log(nums);
```

Output:
```js
Set(3) {1,2,3}
```

Useful for removing duplicates.

```js
let arr = [1,2,2,3];
let unique = [...new Set(arr)];
```

---

### 13. Why Arrow Functions are not Hoisted?

Arrow functions are stored in variables.

```js
sayHi();

const sayHi = () => {
    console.log("Hi");
};
```

Output:
```js
ReferenceError
```

The variable exists in the Temporal Dead Zone until initialization.

Normal functions are fully hoisted:

```js
sayHi();

function sayHi() {
    console.log("Hi");
}
```

Output:
```js
Hi
```

---

### 14. Why is DOM Used?

DOM (Document Object Model) represents the HTML page as JavaScript objects.

It allows JavaScript to:
- Access HTML elements
- Change content
- Change styles
- Add/remove elements
- Handle events

```js
document.getElementById("title").innerText = "Hello";
```

Without DOM, JavaScript cannot interact with HTML pages.
