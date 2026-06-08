
## 1. What is reduce() function?

`reduce()` is used to reduce an array into a single value.

```js
const arr = [1, 2, 3, 4];

const sum = arr.reduce((acc, cur) => acc + cur, 0);

console.log(sum);
```

Output:

```js
10
```

---

## 2. What happens if we replace <!DOCTYPE html> with any other name?

The browser may enter **quirks mode**, causing inconsistent page rendering.

```html
<!DOCTYPE html>
```

This is the correct declaration for HTML5.

---

## 3. What is the use of .prototype in JavaScript?

`.prototype` is used to add properties and methods that are shared by all objects created from a constructor.

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log("Hello");
};

const p1 = new Person("Vasu");
p1.greet();
```

Output:

```js
Hello
```

---

## 4. What are different interactive elements used to interact with users?

Common interactive HTML elements:

- input
- button
- select
- textarea
- form

```html
<input type="text">
<button>Submit</button>
```

---

## 5. Difference between null and undefined?

- `null` → intentionally assigned empty value.
- `undefined` → variable declared but not assigned.

```js
let a = null;
let b;

console.log(a);
console.log(b);
```

Output:

```js
null
undefined
```

---

## 6. What is Optional Chaining?

Optional chaining (`?.`) safely accesses nested properties without throwing an error.

```js
const user = {};

console.log(user.address?.city);
```

Output:

```js
undefined
```

---

## 7. What is DOM?

DOM (Document Object Model) represents an HTML document as objects that JavaScript can access and modify.

```js
document.getElementById("demo").innerHTML = "Hello";
```

---

## 8. Which inbuilt module is used to read files in JS?

In Node.js, the `fs` module is used.

```js
const fs = require("fs");
```

Example:

```js
fs.readFile("data.txt", "utf8", (err, data) => {
  console.log(data);
});
```

---

## 9. What is Hoisting?

Hoisting moves variable and function declarations to the top of their scope before execution.

```js
console.log(a);

var a = 10;
```

Output:

```js
undefined
```

---

## 10. Different types of events in JavaScript?

Common events:

- click
- dblclick
- keydown
- keyup
- submit
- change
- load

```js
button.addEventListener("click", () => {
  console.log("Clicked");
});
```

---

## 11. Which method is used to get key-value pairs from an object?

`Object.entries()`

```js
const obj = {
  name: "Vasu",
  age: 21
};

console.log(Object.entries(obj));
```

Output:

```js
[
  ["name", "Vasu"],
  ["age", 21]
]
```

---

## 12. Keywords used to handle exceptions in JavaScript?

- try
- catch
- finally
- throw

```js
try {
  throw "Error";
} catch (err) {
  console.log(err);
}
```

Output:

```js
Error
```

---

## 13. What is this keyword in JavaScript?

`this` refers to the object that is calling the method.

```js
const person = {
  name: "Vasu",
  greet() {
    console.log(this.name);
  }
};

person.greet();
```

Output:

```js
Vasu
```

---

## 14. What is Event Delegation?

Event delegation is a technique where a parent element handles events for its child elements.

```js
document.getElementById("parent")
  .addEventListener("click", (e) => {
    console.log(e.target);
  });
```

Benefit: fewer event listeners and better performance.

---

## 15. Out of undefined and null, which is user provided and which is provided by JavaScript?

- `null` → User/Programmer provided.
- `undefined` → JavaScript provided.

```js
let a = null;

let b;

console.log(a);
console.log(b);
```

Output:

```js
null
undefined
```
