
## 1. Python is pass by reference or pass by value?

**Answer:**
Python is **neither pass by value nor pass by reference**.

It uses **Pass by Object Reference (Pass by Assignment)**.

- Immutable objects (int, float, string, tuple) cannot be changed.
- Mutable objects (list, dictionary, set) can be changed inside a function.

**Example:**

```python
def add(lst):
    lst.append(4)

nums = [1, 2, 3]
add(nums)

print(nums)   # [1, 2, 3, 4]
```

---

# 2. Difference between `docker run` and `docker start`

| docker run | docker start |
|------------|--------------|
| Creates a new container and starts it. | Starts an existing stopped container. |
| Used first time. | Used after stopping a container. |
| Creates a new container every time. | Does not create a new container. |

**Example**

```bash
docker run nginx
```

Creates and starts a new container.

```bash
docker start mycontainer
```

Starts the existing container named `mycontainer`.

---

# 3. How to create a Docker Image?

### Step 1: Create a Dockerfile

```dockerfile
FROM python:3.11

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```

### Step 2: Build the image

```bash
docker build -t myapp .
```

- `-t` = image name
- `.` = current folder

### Step 3: Check images

```bash
docker images
```

### Step 4: Run image

```bash
docker run myapp
```

---

# 4. What is a Chain in Celery?

A **Chain** is used to execute multiple tasks **one after another**.

The output of one task becomes the input of the next task.

Example:

```
Task A
   ↓
Task B
   ↓
Task C
```

If Task A returns `10`, then Task B receives `10`.

---

# 5. What is the use of `docker-compose.yaml`?

`docker-compose.yaml` is used to run **multiple containers together**.

Instead of running many `docker run` commands, we define all services in one file.

Example:

```
Django
   │
Redis
   │
PostgreSQL
```

Run everything with one command:

```bash
docker compose up
```

Benefits:

- Start multiple containers
- Easy configuration
- Networking between containers
- Volume management

---

# 6. What is Redis Pub/Sub?

Redis Pub/Sub means **Publish and Subscribe**.

It is used for sending messages between applications.

- Publisher → sends message
- Subscriber → receives message

Example:

```
Publisher
     │
 Redis Channel
     │
Subscriber 1
Subscriber 2
```

Use cases:

- Chat applications
- Live notifications
- Real-time updates

---

# 7. What is `CMD` in Dockerfile?

`CMD` tells Docker **which command should run when the container starts**.

Example:

```dockerfile
CMD ["python", "app.py"]
```

When the container starts:

```bash
python app.py
```

**Note:**
A Dockerfile should normally have only **one CMD**.

---

# 8. Difference between `docker pull` and `docker run`

| docker pull | docker run |
|-------------|------------|
| Downloads an image from Docker Hub. | Creates and starts a container from an image. |
| Does not start a container. | Starts the application. |

Example:

```bash
docker pull nginx
```

Downloads the image.

```bash
docker run nginx
```

Creates and starts a container.

---

# 9. Persistent Mechanism in Redis

Redis stores data in memory, but persistence saves data to disk so it is not lost after restart.

There are **two persistence methods**:

### 1. RDB (Redis Database)

- Saves a snapshot of data.
- Faster.
- May lose recent data if Redis crashes.

### 2. AOF (Append Only File)

- Saves every write operation.
- Better data safety.
- File size is larger than RDB.

---

# 10. Difference between Redis and MongoDB

| Redis | MongoDB |
|--------|----------|
| In-memory database | Disk-based NoSQL database |
| Very fast | Slower than Redis |
| Key-Value database | Document database (JSON/BSON) |
| Mainly used for caching | Mainly used for permanent storage |
| Temporary data | Long-term data |
| Supports Pub/Sub | Does not provide Redis-style Pub/Sub |

### Example

**Redis**

```
user:1 -> "Vasu"
```

**MongoDB**

```json
{
  "id": 1,
  "name": "Vasu",
  "age": 22
}
```
