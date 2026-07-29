## 1. Adhikya Edammala: What is the Single Responsibility Principle (SRP)?

The **Single Responsibility Principle (SRP)** is one of the five **SOLID** principles of object-oriented programming. It states that:

> **A class should have only one responsibility or one reason to change.**

This means a class should perform only one specific task.

### Example
Instead of having one `Employee` class that:
- Stores employee details
- Calculates salary
- Generates reports

Split it into:
- `Employee` – Manages employee information
- `SalaryCalculator` – Calculates salary
- `ReportGenerator` – Generates reports

### Benefits
- Easier to maintain
- Better code readability
- Easier testing
- Reduced code dependency

---

## 2. Allanki VV Manikanta Sai: What's the Use of Kubernetes?

**Kubernetes (K8s)** is an open-source container orchestration platform used to deploy, manage, and scale containerized applications automatically.

### Uses
- Automates deployment of applications
- Auto-scales applications based on traffic
- Load balances incoming requests
- Restarts failed containers (Self-healing)
- Supports rolling updates and rollbacks
- Efficient resource management

### Example
If an application runs in multiple Docker containers and one container crashes, Kubernetes automatically starts a new one to maintain availability.

---

## 3. Arpit Yadav: Describe ACID Properties in Database

**ACID** properties ensure that database transactions are reliable and maintain data integrity.

### A - Atomicity
A transaction is executed completely or not at all.

**Example:**
During a bank transfer:
- Debit ₹100 from Account A
- Credit ₹100 to Account B

If the second operation fails, the first operation is rolled back.

---

### C - Consistency
A transaction moves the database from one valid state to another while maintaining all rules and constraints.

**Example:**
A balance should never become negative if a database constraint prevents it.

---

### I - Isolation
Multiple transactions can execute simultaneously without interfering with each other.

**Example:**
Two users updating different records should not affect each other's transactions.

---

### D - Durability
Once a transaction is committed, the changes are permanently stored even if the system crashes.

### Summary

| Property | Meaning |
|----------|---------|
| Atomicity | All or nothing |
| Consistency | Maintains valid data |
| Isolation | Transactions don't interfere |
| Durability | Changes are permanent |

---

## 4. Boorle Sowmya Sri Lakshmi: What are Different Exchanges in RabbitMQ?

RabbitMQ uses **Exchanges** to route messages to queues.

### Types of Exchanges

### 1. Direct Exchange
Routes messages based on an exact routing key.

**Use Case:** Order processing

---

### 2. Fanout Exchange
Sends messages to all connected queues.

**Use Case:** Notifications and broadcasting

---

### 3. Topic Exchange
Routes messages using wildcard routing patterns.

Wildcards:
- `*` → One word
- `#` → Zero or more words

**Use Case:** Logging and event systems

---

### 4. Headers Exchange
Routes messages based on message headers instead of routing keys.

**Use Case:** Complex filtering based on metadata

---

## 5. Md Musharaf: What is a Lambda Function in Python?

A **lambda function** is a small anonymous function defined using the `lambda` keyword.

### Syntax

```python
lambda arguments: expression
```

### Example

```python
square = lambda x: x * x
print(square(5))
```

### Output

```
25
```

### Uses
- Short functions
- `map()`
- `filter()`
- `sorted()`
- `reduce()`

---

## 6. Nayunipatruni Harsha Vardhan: What are Props in React?

**Props (Properties)** are used to pass data from a parent component to a child component.

Props are:
- Read-only
- Immutable
- Used for component communication

### Example

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

<Welcome name="John" />
```

### Output

```
Hello, John
```

### Advantages
- Makes components reusable
- Enables parent-child communication
- Keeps components dynamic

---

## 7. Parlapalli Sulochana: What is the `super` Keyword?

The **`super` keyword** is used to access the parent class's methods, variables, or constructors from a child class.

### Example (Java)

```java
class Animal {
    Animal() {
        System.out.println("Animal Constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super();
        System.out.println("Dog Constructor");
    }
}
```

### Output

```
Animal Constructor
Dog Constructor
```

### Uses
- Call parent constructor
- Call parent methods
- Access parent variables

---

## 8. Vikas Mehta: Explain the Request and Response Cycle in Django

The Django request-response cycle describes how Django processes an HTTP request and returns an HTTP response.

### Steps

1. Browser sends an HTTP request.
2. Django receives the request through the web server.
3. `urls.py` matches the requested URL.
4. The corresponding view in `views.py` is executed.
5. The view interacts with models (if needed).
6. Models communicate with the database.
7. The view prepares data and renders a template.
8. Django returns an HTTP response to the browser.

### Flow Diagram

```
Browser
   │
   ▼
HTTP Request
   │
   ▼
urls.py
   │
   ▼
views.py
   │
   ▼
models.py (Optional)
   │
   ▼
Database
   │
   ▼
Template (Optional)
   │
   ▼
HTTP Response
   │
   ▼
Browser
```

### Benefits
- Clear separation of concerns
- Easy URL routing
- Supports MVC-like architecture (MVT)
- Efficient request handling

---
