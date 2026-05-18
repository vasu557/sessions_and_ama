# AMA Session Questions and Answers

## Adhikya Edammala: What is execution order in SQL?

Execution order is the internal order in which SQL processes a query.

**Order:**

```
FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

---

## Allanki VV Manikanta Sai: Deep Copy vs Shallow Copy

* **Shallow Copy:** Copies references (both objects point to same memory)
* **Deep Copy:** Creates a completely independent copy

**Example:**

```python
# Shallow copy
 a = [[1, 2]]
 b = a

# Deep copy
import copy
b = copy.deepcopy(a)
```

---

## Arpit Yadav: DBMS vs RDBMS vs NoSQL

* **DBMS:** Stores data without relationships (file-based systems)
* **RDBMS:** Stores data in tables with relationships
* **NoSQL:** Flexible schema (JSON, key-value, document-based)

---

## Boorle Sowmya Sri Lakshmi: Can we use WHERE condition with DROP and TRUNCATE?

 No

* DROP → deletes entire table
* TRUNCATE → deletes all rows
* WHERE → only used with SELECT / DELETE

---

## Injamuri Arun Kumar: Why do we use exception handling?

Used to handle runtime errors and prevent program crashes.

**Benefits:**

* Prevents program crash
* Ensures smooth execution

Structure:

```python
try:
    pass
except:
    pass
finally:
    pass
```

---

## Kamparapu Lakshman: What is abstraction?

Abstraction means hiding implementation details and showing only essential features.

---

## M Harivardhan Reddy: Use of SQL

* Insert data
* Read data
* Update data
* Delete data
* Manage database

---

## Md Musharaf: What is use of super() in Python?

Used to call parent class methods inside child class.

```python
class Parent:
    def show(self):
        print("Parent")

class Child(Parent):
    def show(self):
        super().show()
        print("Child")
```

---

## Naman Sharma: Difference between DDL and DML

* **DDL:** Defines structure (`CREATE`, `ALTER`, `DROP`)
* **DML:** Manages data (`INSERT`, `UPDATE`, `DELETE`)

---

## Nayunipatruni Harsha Vardhan: What is operator overloading in Python?

Operator overloading means giving special meaning to operators using methods like `__add__`.

```python
class A:
    def __init__(self, x):
        self.x = x

    def __add__(self, other):
        return self.x + other.x
```

---

## Parlapalli Sulochana: What is generic exception and its use?

Catches all types of exceptions.

* Used when error type is unknown
* Prevents program crash

---

## Rovinpal Udupi: What is GROUP BY in SQL?

Used to group rows with same values.

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

---

## Tumma Haritha: Why is round() function used in Python?

Used to round decimal numbers.

```python
round(3.567, 2)  # 3.57
```

---

## Vikas Mehta: What are flags for add and commit in single line in Git?

```bash
git commit -am "message"
```

* `-a` → stages tracked files
* `-m` → commit message


---

## Yash Nitin Raut: Where do we define attributes in a class?

Attributes are defined inside the class using `__init__` method or directly in class body.

```python
class Student:
    def __init__(self, name):
        self.name = name
```
