## 1. What is a System Prompt?

**Answer:**

A **System Prompt** is a set of instructions given to an AI model before the conversation starts. It defines the AI's behavior, role, rules, limitations, tone, and objectives.

**Example:**

> "You are a helpful React mentor. Explain concepts in simple language with examples."

The AI follows the system prompt throughout the conversation unless overridden by higher-priority instructions.

---

## 2. Difference Between Extended Thinking and Adaptive Thinking

| Extended Thinking                                  | Adaptive Thinking                                                                 |
| -------------------------------------------------- | --------------------------------------------------------------------------------- |
| AI spends more time reasoning before answering.    | AI adjusts the depth of reasoning based on task complexity.                       |
| Used for complex problems requiring deep analysis. | Used for balancing speed and accuracy.                                            |
| Produces detailed reasoning and better solutions.  | Produces quick answers for simple tasks and detailed answers for difficult tasks. |
| Focuses on deeper problem-solving.                 | Focuses on dynamically choosing the right amount of reasoning.                    |

**Example:**

* **Extended Thinking:** Solving a complex system design problem.
* **Adaptive Thinking:** Giving a quick answer for "What is React?" but using deeper reasoning for "Design a scalable React application."

---

## 3. What is the use of useRef in React?

**Answer:**

`useRef` is a React Hook that creates a mutable reference that persists across re-renders without causing re-renders when its value changes.

### Common Uses:

1. Accessing DOM elements directly.
2. Storing previous values.
3. Holding timer or interval IDs.
4. Persisting values between renders without triggering re-renders.

### Syntax:

```jsx
const myRef = useRef(initialValue);
```

### Example:

```jsx
import { useRef } from "react";

function App() {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus</button>
    </>
  );
}
```

---

## 4. What is an MCP Client?

**Answer:**

An **MCP (Model Context Protocol) Client** is an application that connects to MCP servers and requests tools, resources, or data for an AI model.

### Responsibilities:

* Connects to MCP servers.
* Sends requests.
* Receives tool definitions and resources.
* Makes tools available to the AI assistant.

### Examples:

* Claude Desktop
* Cursor
* VS Code with MCP support

**Simple Flow:**

```
AI Application → MCP Client → MCP Server
```

---

## 5. MCP Server vs MCP Client

| MCP Client                    | MCP Server                     |
| ----------------------------- | ------------------------------ |
| Requests tools and resources. | Provides tools and resources.  |
| Initiates communication.      | Responds to requests.          |
| Runs inside AI applications.  | Hosts capabilities for the AI. |
| Consumes services.            | Exposes services.              |

### Example:

* **MCP Client:** Claude Desktop
* **MCP Server:** GitHub MCP Server

### Flow:

```
Claude Desktop (Client)
        ↓
GitHub MCP Server (Server)
        ↓
GitHub Data & Actions
```

---

## 6. What is MCP Inspector?

**Answer:**

**MCP Inspector** is a debugging and testing tool used to inspect, test, and validate MCP servers.

### Uses:

* Test MCP server functionality.
* View available tools and resources.
* Debug requests and responses.
* Verify server configuration.
* Troubleshoot MCP integrations.

### Benefits:

* Easier MCP server development.
* Faster debugging.
* Helps ensure MCP servers work correctly before production use.

### Example:

A developer can use MCP Inspector to:

1. Connect to an MCP server.
2. View all available tools.
3. Execute tool calls.
4. Inspect request/response data.
5. Debug errors.

---
