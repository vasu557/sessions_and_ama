
## 1. Adhikya Edammala — What is the use of `combineReducers`?

`combineReducers` is used in **Redux** to combine multiple reducers into **one root reducer**.

### Why do we use it?

In a large application, we usually have different reducers for different parts of the state.

For example:

```text
UserReducer     → User data
CartReducer     → Cart data
ProductReducer  → Product data
```

Instead of passing these reducers separately to the Redux store, we combine them:

```javascript
const rootReducer = combineReducers({
  user: userReducer,
  cart: cartReducer,
  product: productReducer
});
```

Then:

```javascript
const store = configureStore({
  reducer: rootReducer
});
```

### Simple Definition

> **`combineReducers` combines multiple reducers into a single root reducer so Redux can manage different parts of the application state in an organized way.**

### Example State

After combining:

```javascript
state = {
  user: {...},
  cart: [...],
  product: [...]
}
```

So:

```text
Store
  │
  └── Root Reducer
       ├── userReducer
       ├── cartReducer
       └── productReducer
```

---

## 2. Boorle Sowmya Sri Lakshmi — What is the use of Fanout Exchange?

A **Fanout Exchange** is an exchange in **RabbitMQ** that sends a message to **all queues** that are bound to it.

It does **not** care about the routing key.

### Example

Suppose we have:

```text
              Fanout Exchange
              /      |       \
             ↓       ↓        ↓
          Queue 1  Queue 2  Queue 3
```

If a producer sends:

```text
"New user registered"
```

All three queues receive the message.

```text
Producer
   ↓
Fanout Exchange
   ↓
 ┌───────┬───────┬───────┐
 ↓       ↓       ↓
Q1      Q2      Q3
```

### Real-Life Example

Imagine a company announces:

> "New employee joined."

The message needs to reach:

* HR
* Payroll
* Email notification service

A Fanout Exchange can broadcast the message to all of them.

### Simple Definition

> **A Fanout Exchange broadcasts a message to every queue bound to the exchange, regardless of the routing key.**

### Important Point

```text
Direct Exchange  → sends based on routing key
Topic Exchange   → sends based on pattern
Fanout Exchange  → sends to everyone
```

---

## 3. Md Musharaf — What is the difference between LocalStorage and Cookies?

Both **LocalStorage** and **Cookies** can store data in the browser, but they are used differently.

| Feature                      | LocalStorage                                | Cookies                                                 |
| ---------------------------- | ------------------------------------------- | ------------------------------------------------------- |
| Storage size                 | Larger (~5 MB or more depending on browser) | Small (~4 KB)                                           |
| Sent to server automatically | No                                          | Yes                                                     |
| Expiration                   | Stays until manually removed                | Can have an expiration time                             |
| Common use                   | Client-side data                            | Authentication/session data                             |
| Accessible using JavaScript  | Yes                                         | Yes, except `HttpOnly` cookies                          |
| Security                     | Not ideal for sensitive data                | Can be made safer with `HttpOnly`, `Secure`, `SameSite` |

### LocalStorage

Example:

```javascript
localStorage.setItem("username", "Vasu");
```

Retrieve:

```javascript
localStorage.getItem("username");
```

The data remains in the browser until it is removed.

### Cookies

Example:

```text
session_id=abc123
```

Cookies are automatically sent with matching HTTP requests.

```text
Browser
   ↓
HTTP Request + Cookie
   ↓
Server
```

### Important Security Point

For authentication, **HttpOnly cookies** are often preferred for storing sensitive session/refresh-token information because JavaScript cannot directly read an `HttpOnly` cookie.

### Simple Definition

> **LocalStorage is mainly used for storing client-side data, while cookies are commonly used for data that needs to be sent automatically with HTTP requests, such as session information.**

---

## 4. Nayunipatruni Harsha Vardhan — What is `createAsyncThunk`?

`createAsyncThunk` is a **Redux Toolkit** function used to handle **asynchronous operations** such as API calls.

For example:

```text
React Component
      ↓
dispatch()
      ↓
createAsyncThunk
      ↓
API Call
      ↓
Response
      ↓
Reducer
      ↓
Redux Store
```

### Example

```javascript
export const fetchUsers = createAsyncThunk(
  "users/fetchUsers",
  async () => {
    const response = await fetch("/api/users");
    return response.json();
  }
);
```

`createAsyncThunk` automatically creates three action states:

```text
pending
fulfilled
rejected
```

### Meaning

```text
pending   → API request started
fulfilled → API request succeeded
rejected  → API request failed
```

We can handle these in `extraReducers`:

```javascript
extraReducers: (builder) => {
  builder
    .addCase(fetchUsers.pending, (state) => {
      state.loading = true;
    })
    .addCase(fetchUsers.fulfilled, (state, action) => {
      state.loading = false;
      state.users = action.payload;
    })
    .addCase(fetchUsers.rejected, (state) => {
      state.loading = false;
      state.error = true;
    });
}
```

### Simple Definition

> **`createAsyncThunk` is a Redux Toolkit function that simplifies handling asynchronous operations like API calls and automatically provides pending, fulfilled, and rejected states.**

---

## 5. Vikas Mehta — Why do we use `Depends` in FastAPI?

`Depends` is used in **FastAPI Dependency Injection**.

It allows us to reuse common logic instead of writing the same code inside every API endpoint.

### Example

Suppose we have a function:

```python
def get_current_user():
    return "Vasu"
```

We can use it with `Depends`:

```python
from fastapi import Depends

@app.get("/profile")
def profile(user = Depends(get_current_user)):
    return {"user": user}
```

FastAPI automatically calls:

```python
get_current_user()
```

and gives its result to:

```python
user
```

### Simple Flow

```text
Request
   ↓
FastAPI
   ↓
Depends(get_current_user)
   ↓
get_current_user()
   ↓
Result
   ↓
API Endpoint
```

### Why is it useful?

We can use `Depends` for common functionality such as:

* Authentication
* Database connections
* Getting the current user
* Authorization
* Common request validation
* Reusable business logic

### Real-Life Example

Imagine 10 endpoints need to check whether a user is logged in.

Without `Depends`:

```text
Endpoint 1 → authentication code
Endpoint 2 → authentication code
Endpoint 3 → authentication code
...
Endpoint 10 → authentication code
```

With `Depends`:

```text
             ┌── Endpoint 1
             ├── Endpoint 2
Authentication
             ├── Endpoint 3
             └── Endpoint 10
```

All endpoints can reuse the same dependency.

### Simple Definition

> **`Depends` is used in FastAPI for dependency injection, allowing us to create reusable logic such as authentication, database connections, and validation and automatically provide their results to API endpoints.**

---

# Quick Revision

| Question                | One-Line Answer                                                                                      |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| `combineReducers`       | Combines multiple reducers into one root reducer.                                                    |
| Fanout Exchange         | Sends a message to all queues bound to the exchange.                                                 |
| LocalStorage vs Cookies | LocalStorage stores client-side data; cookies are also sent automatically with HTTP requests.        |
| `createAsyncThunk`      | Handles asynchronous operations like API calls in Redux Toolkit.                                     |
| `Depends`               | Provides reusable dependencies such as authentication and database connections to FastAPI endpoints. |
