## 1. Adhikya Edammala — When do we use an Agent and Workflow?

### Agent

An **agent** is used when the system needs to make decisions dynamically and choose its own next steps based on the situation.

**Use an agent when:**

* The task is open-ended or unpredictable.
* Multiple tools may be required.
* The system needs reasoning and decision-making.
* The next action depends on the result of the previous action.

**Example:** An AI customer-support agent can decide whether to search an order, check a refund policy, or escalate an issue.

### Workflow

A **workflow** is used when the steps are predefined and follow a fixed sequence.

**Use a workflow when:**

* The process is predictable.
* Steps are known in advance.
* Consistency and control are important.
* You want easier testing and debugging.

**Example:** A registration process can follow: validate user → create account → send email → show confirmation.

**In short:**

> **Agent = dynamic decision-making**
> **Workflow = predefined sequence of steps**

---

## 2. Boorle Sowmya Sri Lakshmi — Tell me different types of Hooks

Hooks are functions provided by React that allow functional components to use features such as state, lifecycle behavior, context, and references.

### Common React Hooks

1. **`useState`** — Manages state in a functional component.
2. **`useEffect`** — Performs side effects such as API calls, subscriptions, or timers.
3. **`useContext`** — Accesses data from a React Context.
4. **`useRef`** — Stores a mutable value or references a DOM element without causing a re-render.
5. **`useReducer`** — Manages complex state logic using reducer functions.
6. **`useMemo`** — Memoizes an expensive calculation.
7. **`useCallback`** — Memoizes a function.
8. **`useLayoutEffect`** — Runs an effect synchronously after DOM changes but before the browser paints.
9. **`useImperativeHandle`** — Customizes the value exposed through a ref.
10. **`useId`** — Generates unique IDs that are useful for accessibility and server/client rendering.
11. **`useTransition`** — Marks state updates as non-urgent transitions.
12. **`useDeferredValue`** — Allows a value to be deferred so urgent updates can happen first.
13. **`useSyncExternalStore`** — Subscribes to an external store safely.
14. **`useDebugValue`** — Displays custom hook information in React DevTools.

You can also create **custom hooks** to reuse stateful logic across components.

---

## 3. Md Musharaf — What happens if we update state manually without `setState`?

In React, state should be updated using the appropriate state setter, such as `setState` in class components or the setter returned by `useState` in functional components.

For example:

```jsx
const [count, setCount] = useState(0);

// Correct
setCount(count + 1);

// Incorrect
count = count + 1;
```

If we manually modify state:

* React may **not detect the change**.
* The component may **not re-render**.
* The UI can become **out of sync** with the actual data.
* React's state update mechanisms and optimizations may not work correctly.

For objects and arrays, directly mutating the existing state is also problematic:

```jsx
// Incorrect
user.name = "John";

// Correct
setUser({ ...user, name: "John" });
```

**In short:** Always use the state setter to update React state so React can properly schedule a re-render.

---

## 4. Nayunipatruni Harsha Vardhan — What is Adaptive Thinking?

**Adaptive thinking** is the ability to adjust your approach when circumstances, requirements, or problems change.

Instead of following one fixed solution, an adaptive thinker:

* Understands the changing situation.
* Evaluates different possible solutions.
* Learns from feedback and mistakes.
* Changes strategies when the current approach is not working.
* Makes decisions based on new information.

**Example:**
If a software feature does not work as expected after testing, an adaptive developer analyzes the feedback, identifies the problem, and changes the implementation instead of continuing with the same approach.

**In short:**

> Adaptive thinking means **being flexible, learning continuously, and changing your approach when the situation requires it.**

---

## 5. Vikas Mehta — Advantages of Using React

React is a JavaScript library used for building user interfaces, particularly interactive web applications.

### Advantages of React

1. **Component-Based Architecture**
   React applications can be divided into reusable components, making code easier to maintain.

2. **Reusability**
   Components can be reused in different parts of an application, reducing duplicate code.

3. **Efficient UI Updates**
   React uses a reconciliation process to efficiently update the UI when data changes.

4. **Easy to Learn**
   Developers familiar with JavaScript and HTML can learn React relatively easily.

5. **Strong Ecosystem**
   React has a large ecosystem of libraries, tools, and community resources.

6. **Developer Tools**
   React Developer Tools help developers inspect components and debug applications.

7. **Good for Large Applications**
   Its component-based structure makes it suitable for building and maintaining large applications.

8. **One-Way Data Flow**
   Data generally flows from parent components to child components, making application behavior easier to understand and debug.

9. **Supports Modern Development**
   React supports modern features such as Hooks, concurrent rendering capabilities, and server-side rendering through frameworks such as Next.js.

### Conclusion

React helps developers build **reusable, maintainable, and interactive user interfaces** using a component-based approach.
