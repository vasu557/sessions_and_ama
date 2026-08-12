## 1. Adhikya Edammala — What is Compaction?

**Compaction** is the process of reducing the size of stored context by removing unnecessary or less important information while keeping the important information.

**Example:** Instead of keeping a long conversation history, older messages can be summarized into a shorter summary.

**Purpose:** To save context space and allow the AI to focus on important information.

---

## 2. Allanki VV Manikanta Sai — Tell Me the Tips for Saving Context Space

Some useful tips are:

- Remove unnecessary information.
- Use short and clear prompts.
- Avoid repeating the same information.
- Summarize older conversations when detailed history is not needed.
- Send only the relevant part of large files or code.
- Keep instructions concise and specific.

**Main idea:** Send only the information that is actually needed.

---

## 3. Boorle Sowmya Sri Lakshmi — When Will You Use `useEffect()` Hook?

We use **`useEffect()`** when we need to perform a **side effect** in a React component.

Common examples:

- Fetching data from an API.
- Setting up event listeners.
- Using timers such as `setInterval()`.
- Updating something outside React.
- Running code when a component mounts or when specific state/props change.

**Example:**

```jsx
useEffect(() => {
  console.log("Component loaded");
}, []);
```

The empty dependency array means the effect runs once after the component mounts.

---

## 4. Md Musharaf — What Happens If Context Window Is Going to Full?

When the context window becomes full, the AI cannot keep adding unlimited new information.

Depending on the system, older or less important information may be:

- Removed or truncated.
- Summarized through compaction.
- No longer available to the model.

This can cause the AI to **lose access to earlier conversation details**.

**Main idea:** A full context window limits how much information the AI can process at once.

---

## 5. Nayunipatruni Harsha Vardhan — What Is the Use of `useNavigate()`?

`useNavigate()` is a React Router hook used to **navigate from one route to another using JavaScript**.

**Example:**

```jsx
const navigate = useNavigate();

function handleLogin() {
  navigate("/dashboard");
}
```

After login, the user is programmatically moved to `/dashboard`.

It is useful for navigation after actions such as:

- Form submission
- Login
- Logout
- Delete operation
- Button click

---

## 6. Vikas Mehta — Why Should We Not Use Array Indexes as `key`?

In React, `key` helps React identify which list items have changed.

Using an array index as a key can cause problems when the list is:

- Reordered
- Inserted into
- Deleted from

**Example:**

```jsx
items.map((item, index) => (
  <li key={index}>{item}</li>
))
```

If the list changes, React may think that an item is the same when it is actually a different item. This can cause incorrect UI behavior or state being associated with the wrong item.

**Better:**

```jsx
items.map((item) => (
  <li key={item.id}>{item.name}</li>
))
```

Use a **stable and unique ID** whenever possible.
