## 1. Adhikya Edammala - What is pruning?

**Answer:**

Pruning is the process of reducing the size of the prompt or conversation context by removing information that is no longer needed.

### Why is pruning used?
- Reduces token usage and cost.
- Keeps the context window from filling up.
- Improves model performance by keeping only relevant information.

**Example:**
If a conversation contains 100 messages but only the last 10 are relevant to the current task, the earlier 90 messages can be pruned.

---

# 2. Allanki VV Manikanta Sai - How do you test a non-deterministic model?

**Answer:**

A non-deterministic model may produce different outputs for the same input, so you cannot test it using exact output matching.

### Common testing methods:
- Define expected behaviors instead of exact answers.
- Use evaluation criteria (correctness, relevance, safety).
- Run the same prompt multiple times.
- Use automated evaluators (LLM-as-a-judge or rule-based checks).
- Compare outputs against acceptance thresholds.

**Example:**
Instead of checking whether the answer is exactly the same, verify that it:
- Answers the question.
- Contains correct facts.
- Follows the required format.
- Is safe and relevant.

---

# 3. Boorle Sowmya Sri Lakshmi - What is integration testing?

**Answer:**

Integration testing verifies that multiple components of an application work correctly together.

Unlike unit testing, which tests individual functions, integration testing checks interactions between components.

### Example

A chatbot application:

User → API → Claude API → Database

Integration testing verifies that:
- API sends the correct request.
- Claude returns a response.
- Response is stored in the database.
- User receives the expected output.

---

# 4. Md Musharaf - What is the difference between `skill.md` and `CLAUDE.md`?

| `skill.md` | `CLAUDE.md` |
|------------|-------------|
| Defines a reusable skill. | Defines project-wide instructions. |
| Loaded only when the skill is triggered. | Loaded automatically for the project. |
| Used for a specific task (e.g., code review, testing). | Used to guide Claude's behavior across the repository. |
| Multiple skill files can exist. | Typically one `CLAUDE.md` per project. |

### Example

**skill.md**
- Generate unit tests
- Review React code
- Write documentation

**CLAUDE.md**
- Follow coding standards
- Preferred architecture
- Naming conventions
- Project instructions

---

# 5. Vikas Mehta - Why are dictionaries fast for lookup?

**Answer:**

Dictionaries (hash maps) are fast because they use a **hash table**.

### How it works

1. A key is passed to a hash function.
2. The hash function calculates an index.
3. The value is stored at that index.
4. Looking up the same key computes the same index directly.

Instead of searching every item, the dictionary jumps directly to the correct location.

### Time Complexity

| Operation | Average Time |
|-----------|--------------|
| Lookup | **O(1)** |
| Insert | **O(1)** |
| Delete | **O(1)** |

Worst case (many hash collisions): **O(n)**, but a good hash function keeps collisions rare.

### Example (Python)

```python
student = {
    "name": "Vasu",
    "age": 21
}

print(student["name"])
```

The dictionary computes the hash of `"name"` and directly retrieves `"Vasu"` without scanning all keys.

**Why is it fast?**
Because it performs **direct access using a hash table**, avoiding a linear search through all elements.
