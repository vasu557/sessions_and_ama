# Django Interview Questions & Answers

## 1. What is a Superuser?

A **Superuser** is a user with **all permissions** in Django.

### Features
- Can log in to Django Admin.
- Has all permissions automatically.
- Can add, update, delete, and manage every model.
- `is_staff = True`
- `is_superuser = True`

### Create a Superuser
```bash
python manage.py createsuperuser
```

---

## 2. What is `get_object_or_404`?

`get_object_or_404()` is a shortcut function that retrieves a single object from the database.

If the object exists:
- Returns the object.

If it does not exist:
- Raises an **HTTP 404 (Page Not Found)** instead of crashing.

### Syntax

```python
from django.shortcuts import get_object_or_404

post = get_object_or_404(Post, id=1)
```

### Equivalent Code

```python
try:
    post = Post.objects.get(id=1)
except Post.DoesNotExist:
    raise Http404
```

### When to use
Whenever you're fetching a single object from the database in a view.

---

## 3. What is `get_object_for_this_type()`?

It is a method provided by Django's **ContentType** framework.

It retrieves an object dynamically without directly using the model class.

### Example

```python
from django.contrib.contenttypes.models import ContentType

content_type = ContentType.objects.get_for_model(Post)

post = content_type.get_object_for_this_type(id=1)
```

This is equivalent to:

```python
Post.objects.get(id=1)
```

### Use Cases
- Generic Foreign Keys
- Audit systems
- Activity feeds
- Reusable apps that work with multiple models

---

## 4. What is `render_to_string()`?

`render_to_string()` renders a Django template into a **string** instead of an HTTP response.

### Syntax

```python
from django.template.loader import render_to_string

html = render_to_string(
    "email.html",
    {"name": "Vasu"}
)
```

### Common Uses
- Sending HTML emails
- Generating PDFs
- Rendering HTML for AJAX responses
- Creating notification content

Unlike `render()`, it **does not return an HttpResponse**.

---

## 5. Difference between Celery Worker and Celery Beat

| Celery Worker | Celery Beat |
|---------------|-------------|
| Executes background tasks | Schedules background tasks |
| Runs tasks from the queue | Places tasks into the queue at scheduled times |
| Can have multiple workers | Usually only one Beat scheduler |
| Used for asynchronous processing | Used for periodic tasks |

### Example

Worker:

```python
send_email.delay()
```

Beat:

```python
Every day at 9 AM:
send_email.delay()
```

**Simple Memory Tip**

- **Worker = Does the work**
- **Beat = Decides when to do the work**

---

## 6. What is `django.contrib.contenttypes`?

`django.contrib.contenttypes` is a Django application that stores information about all installed models.

It allows Django to refer to models dynamically.

Each model has an entry in the `django_content_type` table.

### Uses
- Generic Foreign Keys
- Django Admin logs
- Permissions system
- Reusable applications
- Audit logs

### Example

```python
from django.contrib.contenttypes.models import ContentType

ContentType.objects.get_for_model(Post)
```

---

## 7. What is Autocomplete in Elasticsearch?

Autocomplete suggests possible search terms while the user is typing.

Example:

User types:

```
Djan
```

Suggestions:

```
Django
Django REST Framework
Django Signals
```

### Benefits
- Faster searching
- Better user experience
- Fewer typing mistakes

### Common Elasticsearch Features
- Completion Suggester
- Edge N-Gram
- Search As You Type

---

## 8. What is the `Count` class?

`Count` is an aggregation function in Django used to count records.

Import:

```python
from django.db.models import Count
```

### Example

```python
from django.db.models import Count

Post.objects.aggregate(total=Count("id"))
```

Output

```python
{'total': 25}
```

### Annotate Example

```python
User.objects.annotate(post_count=Count("posts"))
```

This adds the number of posts for each user.

### Uses
- Counting related objects
- Dashboards
- Reports
- Statistics

---

## 9. When do we use CSRF protection?

CSRF (Cross-Site Request Forgery) protection prevents attackers from submitting requests on behalf of a logged-in user.

Use CSRF protection whenever a request **modifies data**.

### Use CSRF Token For
- POST
- PUT
- PATCH
- DELETE

Example

```html
<form method="post">
    {% csrf_token %}
</form>
```

### No CSRF Needed
- GET requests
- Read-only APIs

---

## 10. What are Auth Password Validators?

Password validators check whether a password meets security requirements.

Configured in `settings.py`.

Example

```python
AUTH_PASSWORD_VALIDATORS = [
    ...
]
```

### Default Validators

1. **UserAttributeSimilarityValidator**
   - Prevents passwords similar to username or email.

2. **MinimumLengthValidator**
   - Ensures minimum password length.

3. **CommonPasswordValidator**
   - Rejects common passwords like `password123`.

4. **NumericPasswordValidator**
   - Rejects passwords containing only numbers.

### Benefits
- Stronger passwords
- Better security
- Prevents weak passwords

---

## 11. Difference between `is_staff` and `is_superuser`

| `is_staff` | `is_superuser` |
|------------|----------------|
| Allows access to Django Admin | Gives all permissions automatically |
| Needs explicit permissions to manage models | Has every permission by default |
| Can only perform allowed actions | Can perform all actions |
| Usually used for employees/admin staff | Used for the main administrator |

### Example

```text
Staff User:
is_staff = True
is_superuser = False
```

Can log into admin, but permissions depend on what is assigned.

```text
Superuser:
is_staff = True
is_superuser = True
```

Can do everything without assigning permissions.

### Memory Tip

- **is_staff → Can enter Admin**
- **is_superuser → Can do everything**
