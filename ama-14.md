# Interview Questions & Answers

## 1. Adhikya Edammala - What is the difference between Redis and RabbitMQ?

| Redis | RabbitMQ |
|--------|----------|
| In-memory data store (cache, database, message broker). | Dedicated message broker. |
| Mainly used for caching, session storage, and fast data access. | Mainly used for reliable message queuing between applications. |
| Extremely fast because data is stored in RAM. | Slightly slower but provides reliable message delivery. |
| Supports Pub/Sub and simple queues. | Supports advanced routing, acknowledgments, retries, and durable queues. |
| Example: Store user sessions or cache API responses. | Example: Queue emails, notifications, background jobs using Celery. |

**In one line:**  
**Redis is mainly for fast data storage/caching, while RabbitMQ is mainly for reliable message queuing.**

---

## 2. Allanki VV Manikanta Sai - What is Docker Compose?

**Docker Compose** is a tool used to define and run multiple Docker containers using a single `docker-compose.yml` file.

### Example
```yaml
version: "3"

services:
  web:
    build: .
    ports:
      - "8000:8000"

  redis:
    image: redis

  postgres:
    image: postgres
```

Instead of starting each container separately, simply run:

```bash
docker compose up
```

**In one line:**  
**Docker Compose manages multiple Docker containers as a single application.**

---

## 3. Boorle Sowmya Sri Lakshmi - What is a document in MongoDB?

A **document** is a single record in MongoDB.

- Stored in **BSON** (Binary JSON) format.
- Consists of **key-value pairs**.
- Similar to a row in an SQL table.

### Example

```json
{
  "_id": 1,
  "name": "Vasu",
  "age": 21,
  "city": "Hyderabad"
}
```

Here, the entire JSON object is **one document**.

**In one line:**  
**A document is a single JSON-like record stored inside a MongoDB collection.**

---

## 4. Md Musharaf - What is the difference between Serializer and ModelSerializer?

| Serializer | ModelSerializer |
|------------|-----------------|
| Fields must be defined manually. | Fields are automatically generated from the Django model. |
| More control over validation and fields. | Less code and faster development. |
| Used when data doesn't come directly from a model. | Used for Django model objects. |
| Requires custom `create()` and `update()` methods. | Provides `create()` and `update()` automatically. |

### Serializer Example

```python
class StudentSerializer(serializers.Serializer):
    name = serializers.CharField()
    age = serializers.IntegerField()
```

### ModelSerializer Example

```python
class StudentSerializer(serializers.ModelSerializer):
    class Meta:
        model = Student
        fields = "__all__"
```

**In one line:**  
**Serializer requires manual field definition, whereas ModelSerializer automatically generates fields from a Django model.**

---

## 5. Nayunipatruni Harsha Vardhan - What is a Dockerfile?

A **Dockerfile** is a text file containing instructions to build a Docker image.

### Example

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

Build the image:

```bash
docker build -t myapp .
```

Run the container:

```bash
docker run -p 8000:8000 myapp
```

**In one line:**  
**A Dockerfile is a blueprint used to create a Docker image.**

---

## 6. Vikas Mehta - How do you secure a Django App?

Some common Django security best practices are:

1. Set `DEBUG = False` in production.
2. Store secret keys in environment variables.
3. Use HTTPS with SSL/TLS.
4. Enable Django's CSRF protection.
5. Use Django Authentication and Permissions.
6. Prevent SQL Injection by using Django ORM.
7. Enable secure cookies:
   - `SESSION_COOKIE_SECURE = True`
   - `CSRF_COOKIE_SECURE = True`
8. Keep Django and dependencies updated.
9. Validate and sanitize user input.
10. Restrict allowed hosts:

```python
ALLOWED_HOSTS = ["example.com"]
```

11. Use strong passwords and password hashing.
12. Protect APIs using JWT or Token Authentication.
13. Regularly back up the database.
14. Configure proper logging and monitoring.
15. Limit file upload types and sizes.

**In one line:**  
**Secure a Django app by using HTTPS, environment variables, authentication, CSRF protection, secure cookies, input validation, and keeping dependencies updated.**
