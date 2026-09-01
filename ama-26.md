

## 1. Adhikya Edammala - What is FastAPI?

**FastAPI** is a modern, high-performance Python web framework used for building RESTful APIs. It is built on top of Starlette (for web routing) and Pydantic (for data validation).

### Key Highlights:
* **High Performance**: As fast as NodeJS and Go, thanks to asynchronous support (`async`/`await`).
* **Automatic Documentation**: Automatically generates interactive API docs (Swagger UI and ReDoc) out of the box based on Python type hints.
* **Data Validation**: Validates incoming request payloads and query parameters automatically.
* **Developer Friendly**: Reduces code duplication, decreases bugs, and offers great editor auto-completion.

---

## 2. Boorle Sowmya Sri Lakshmi - What is the use of Redis?

**Redis** (Remote Dictionary Server) is an open-source, in-memory data store used primarily as a **caching layer**, **in-memory database**, and **message broker**.

### Common Use Cases:
* **Caching**: Stores frequently accessed database query results in RAM for lightning-fast sub-millisecond response times.
* **Session Management**: Manages user session state in web applications (e.g., login tokens, shopping carts).
* **Rate Limiting**: Tracks API request counters to block excessive user traffic.
* **Pub/Sub Messaging**: Facilitates real-time messaging and event notifications between microservices.
* **Leaderboards & Analytics**: Uses atomic counter operations for real-time counting and rankings.

---

## 3. Md Musharaf - Why do we need to pass a `key` prop in React components when using `map`?

In React, the `key` prop is a special string attribute that gives elements inside an array a stable, unique identity across renders.

### Why It Is Needed:
* **Efficient DOM Diffing (Reconciliation)**: React uses keys to quickly compare the old element tree with the new one. It identifies exactly which items were added, updated, reordered, or removed.
* **Preserving Component State**: Without unique keys, React might re-use DOM nodes or component instances incorrectly, causing UI bugs, input state mismatches, or unexpected resets.
* **Performance Optimization**: Minimizes unnecessary re-rendering and DOM manipulations when dynamic lists change.

---

## 4. Nayunipatruni Harsha Vardhan - What is the use of `useMemo`?

`useMemo` is a React Hook used to **memoize (cache)** the result of a costly calculation between re-renders.

### Key Details:
* **Prevents Re-computation**: It only recalculates the value when one of its specified dependencies changes.
* **Referential Equality**: Helps preserve referential equality for non-primitive values (objects, arrays) passed as props to child components, preventing unnecessary child re-renders.

### Example Scenario:
Filtering or sorting a large dataset of thousands of items:
```javascript
const filteredList = useMemo(() => {
  return items.filter(item => item.name.includes(searchTerm));
}, [items, searchTerm]);
```

---

## 5. Vikas Mehta - What does `scalar_one_or_none()` do?

In SQLAlchemy (Python ORM), `scalar_one_or_none()` executes a database query expecting **at most one** result row and returns the scalar value (or entity object) of that row.

### How It Behaves:
* **Returns 1 Object/Value**: If exactly 1 matching record is found in the database.
* **Returns `None`**: If 0 matching records are found.
* **Raises Exception (`MultipleResultsFound`)**: If 2 or more matching records are found.

### When to Use It:
Use it when querying by unique identifiers (e.g., fetching a user by `id` or `email`) where getting 0 or 1 result is valid, but getting multiple results indicates a data integrity violation.
```python
user = session.query(User).filter(User.email == "user@example.com").scalar_one_or_none()
```
