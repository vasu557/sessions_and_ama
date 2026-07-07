# Django Interview Questions & Answers (Easy)

## 1. Difference between Django and Django REST Framework (DRF)

| Django | Django REST Framework (DRF) |
|--------|------------------------------|
| Used to build web applications (HTML pages). | Used to build REST APIs. |
| Returns HTML templates. | Returns JSON data. |
| Uses Django Forms. | Uses Serializers. |
| Best for websites. | Best for mobile apps and frontend frameworks like React or Angular. |

**Example:**
- Django → Login page rendered in the browser.
- DRF → `/api/login/` returns JSON.

---

## 2. What is a Router in DRF?

A **Router** automatically creates URL patterns for a ViewSet.

Instead of writing multiple URLs manually, the router generates them for you.

**Example:**

```python
router.register("users", UserViewSet)
```

Automatically creates URLs like:

```
GET    /users/
POST   /users/
GET    /users/1/
PUT    /users/1/
DELETE /users/1/
```

**One-line interview answer:**
> Router automatically generates API URLs for ViewSets.

---

## 3. What are Serializers?

A **Serializer** converts Django model objects into JSON and converts JSON back into Python objects.

It is similar to Django Forms, but for APIs.

**Example**

Model object:

```python
User(name="Vasu", age=22)
```

Serializer output:

```json
{
    "name": "Vasu",
    "age": 22
}
```

**Uses**
- Convert Model → JSON
- Convert JSON → Model
- Validate incoming data

---

## 4. What is `request.data` in DRF?

`request.data` contains the data sent by the client in an API request.

It works for JSON, form data, and multipart data.

**Example**

Client sends:

```json
{
    "name": "Vasu",
    "age": 22
}
```

In the view:

```python
print(request.data)
```

Output:

```python
{'name': 'Vasu', 'age': 22}
```

**One-line interview answer:**
> `request.data` is used to access data sent by the client in an API request.

---

## 5. What is AJAX?

**AJAX** stands for **Asynchronous JavaScript and XML**.

It allows the browser to communicate with the server **without reloading the entire page**.

**Example**
- Like a post on social media.
- The like count updates instantly without refreshing the page.

**Benefits**
- Faster user experience
- No full page reload
- Less data transfer

---

## 6. What are Generic Views?

Generic Views are **pre-built views** provided by Django (and DRF) that reduce repetitive code.

Instead of writing CRUD logic manually, you can use generic views.

**Examples**

```python
ListAPIView
CreateAPIView
RetrieveAPIView
UpdateAPIView
DestroyAPIView
```

**Example**

Instead of writing:

```python
def get(self):
    ...
```

Use:

```python
class UserList(ListAPIView):
    queryset = User.objects.all()
```

**One-line interview answer:**
> Generic Views provide ready-made CRUD functionality with less code.

---

## 7. What is a Framework?

A **Framework** is a collection of pre-written code, tools, and libraries that helps developers build applications faster.

It provides a fixed structure so developers don't have to write everything from scratch.

**Examples**
- Django
- Django REST Framework
- React
- Spring Boot

**One-line interview answer:**
> A framework provides a ready-made structure and reusable code for building applications quickly.

---

## 8. What is `request.user`?

`request.user` returns the **currently logged-in user**.

If the user is not logged in, it returns **AnonymousUser**.

**Example**

```python
print(request.user.username)
```

Output:

```
vasu
```

**Uses**
- Check who is logged in
- Restrict access
- Save the logged-in user as the creator of an object

Example:

```python
post.author = request.user
```

---

## 9. Explain ACID Properties

ACID properties ensure that database transactions are reliable and safe.

### A - Atomicity

A transaction is completed **fully or not at all**.

**Example**
If money is deducted from one account but not added to another, the whole transaction is cancelled.

---

### C - Consistency

The database always remains in a **valid state** before and after the transaction.

**Example**
If account balance cannot become negative, the database prevents it.

---

### I - Isolation

Multiple transactions do not interfere with each other.

**Example**
Two users booking the last seat at the same time won't both get it.

---

### D - Durability

Once a transaction is committed, it is permanently saved, even if the system crashes.

**Example**
After payment is successful, the record remains saved even after a power failure.

**One-line interview answer:**
> ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure safe and reliable database transactions.
