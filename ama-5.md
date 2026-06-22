## 1. What is Atomic Transaction?
**Answer:**
An atomic transaction ensures that all database operations inside a transaction are completed successfully. If any operation fails, all changes are rolled back.

Example:
```python
from django.db import transaction

with transaction.atomic():
    # database operations
```

---

## 2. How to Create a Superuser in Django?
**Answer:**
Run the following command:

```bash
python manage.py createsuperuser
```

Then enter:
- Username
- Email
- Password

---

## 3. How Do We Add an Image to Templates?
**Answer:**

1. Store images in the `media` folder.
2. Configure `MEDIA_URL` and `MEDIA_ROOT` in `settings.py`.
3. Display image in template:

```html
<img src="{{ object.image.url }}" alt="Image">
```

---

## 4. Difference Between manage.py, views.py, urls.py, models.py

| File | Purpose |
|--------|---------|
| manage.py | Executes Django commands |
| views.py | Contains business logic |
| urls.py | Maps URLs to views |
| models.py | Defines database tables |

---

## 5. What is a Request in Django?
**Answer:**

A request is an HTTP request sent by the client (browser) to the Django server.

Example:

```python
def home(request):
    return HttpResponse("Hello")
```

`request` contains user data, form data, headers, etc.

---

## 6. How Do We Register Models in Admin Panel?
**Answer:**

```python
from django.contrib import admin
from .models import Student

admin.site.register(Student)
```

---

## 7. Why is Django Called a Batteries-Included Framework?
**Answer:**

Because Django provides many built-in features:

- Admin Panel
- Authentication
- ORM
- Security
- Sessions
- Form Handling

No need for many external libraries.

---

## 8. What is the Use of CSRF Token?
**Answer:**

CSRF Token protects forms from Cross-Site Request Forgery attacks.

Example:

```html
<form method="POST">
    {% csrf_token %}
</form>
```

---

## 9. Different Template Tags in Django

**Common Template Tags:**

```html
{% if %}
{% for %}
{% block %}
{% extends %}
{% include %}
{% url %}
{% csrf_token %}
```

Used to add logic inside templates.

---

## 10. How Many Ways to Insert a Record Using ORM?

### Method 1

```python
Student.objects.create(name="Vasu")
```

### Method 2

```python
obj = Student(name="Vasu")
obj.save()
```

---

## 11. What is the Use of F() Method?
**Answer:**

`F()` allows database operations without fetching values into Python.

Example:

```python
from django.db.models import F

Product.objects.update(quantity=F('quantity') + 1)
```

Used for efficient updates.

---

## 12. Why Do We Use DEBUG = True?
**Answer:**

```python
DEBUG = True
```

- Shows detailed error pages.
- Useful during development.

In production:

```python
DEBUG = False
```

for security reasons.

---

## 13. Why Do We Use Redirect After Form Submission?
**Answer:**

To prevent duplicate form submissions when the user refreshes the page.

Example:

```python
return redirect('home')
```

This follows the POST-Redirect-GET pattern.

---

## 14. What Architecture is Followed by Django?
**Answer:**

Django follows the **MVT (Model-View-Template)** architecture.

### Components

**Model**
- Handles database.

**View**
- Handles business logic.

**Template**
- Handles UI and presentation.

### Flow

```
User → URL → View → Model → Template → Response
```

---
