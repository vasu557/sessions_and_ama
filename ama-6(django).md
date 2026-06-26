# 1. Difference between `null=True` and `blank=True`

**`null=True`**
- Database option.
- Stores `NULL` in the database.

```python
age = models.IntegerField(null=True)
```

**`blank=True`**
- Form validation option.
- Allows the field to be left empty.

```python
bio = models.TextField(blank=True)
```

| `null=True` | `blank=True` |
|-------------|--------------|
| Database | Forms/Admin |
| Stores NULL | Allows empty input |

---

# 2. Why do we use Pillow?

Pillow is a Python library used to handle images.

Required when using `ImageField`.

```python
profile_pic = models.ImageField(upload_to="profiles/")
```

Without Pillow:

```text
Cannot use ImageField because Pillow is not installed.
```

---

# 3. What is `psycopg2-binary`?

It is a PostgreSQL adapter for Python.

It allows Django to connect to PostgreSQL.

```bash
pip install psycopg2-binary
```

Flow:

```text
Django ORM
     ↓
psycopg2-binary
     ↓
PostgreSQL
```

---

# 4. What are Signals?

Signals automatically execute code when an event occurs.

Example:

```python
@receiver(post_save, sender=User)
def create_profile(sender, instance, created, **kwargs):
    if created:
        Profile.objects.create(user=instance)
```

Here, a Profile is created automatically after a User is created.

---

# 5. Common ASGI Servers

ASGI servers run Django async applications.

Common servers:
- Uvicorn
- Daphne
- Hypercorn

Example:

```bash
uvicorn project.asgi:application
```

---

# 6. What is Manager in Django?

A Manager is used to query the database.

Default manager:

```python
User.objects.all()
```

Here:
- `objects` → Manager
- `all()` → QuerySet method

---

# 7. What is `annotate()`?

`annotate()` adds calculated values to each object.

Example:

```python
from django.db.models import Count

Author.objects.annotate(total_books=Count("book"))
```

Result:

```text
John   → total_books = 5
Alice  → total_books = 3
```

---

# 8. What is `validate_password()`?

Checks whether a password follows Django's password rules.

```python
from django.contrib.auth.password_validation import validate_password

validate_password(password)
```

Checks:
- Minimum length
- Common password
- Numeric password
- Similar to username

---

# 9. Some ORM Operations

Create

```python
User.objects.create(username="vasu")
```

Get

```python
User.objects.get(id=1)
```

Filter

```python
User.objects.filter(is_active=True)
```

Update

```python
User.objects.filter(id=1).update(username="new")
```

Delete

```python
User.objects.filter(id=1).delete()
```

Count

```python
User.objects.count()
```

---

# 10. Difference between `auto_now_add` and `auto_now`

**`auto_now_add=True`**
- Sets date/time only once (on create).

```python
created_at = models.DateTimeField(auto_now_add=True)
```

**`auto_now=True`**
- Updates date/time on every save.

```python
updated_at = models.DateTimeField(auto_now=True)
```

| `auto_now_add` | `auto_now` |
|----------------|------------|
| Only on create | Every save |
| Creation time | Last updated time |

---

# 11. What does `request.user` give?

`request.user` returns the currently logged-in user.

```python
print(request.user.username)
```

If logged in:

```text
<User: vasu>
```

If not logged in:

```text
AnonymousUser
```

Common use:

```python
post.author = request.user
```
