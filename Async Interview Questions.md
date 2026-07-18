# 🚀 Async Python Interview Cheat Sheet (Ultra Packed)

> **50+ Most Asked Async Python Interview Questions & Answers (Python 3.11+)**

---

# ⭐ Beginner Level

### 1. What is Asynchronous Programming?

**Answer:**
A programming model where a task can pause while waiting for an I/O operation, allowing other tasks to execute instead of blocking the program.

---

### 2. What is a Coroutine?

A coroutine is an **async function** that can suspend execution using `await` and resume later.

```python
async def fetch():
    ...
```

---

### 3. Difference between Function and Coroutine?

| Function | Coroutine |
|-----------|-----------|
| def | async def |
| Runs immediately | Returns coroutine object |
| Cannot await | Can await |

---

### 4. What does `async` do?

Marks a function as a coroutine.

---

### 5. What does `await` do?

Pauses the coroutine until the awaited task completes **without blocking the thread**.

---

### 6. Can we use await outside async?

❌ No.

---

### 7. What happens when you call an async function?

It returns a **coroutine object**.

```python
obj = fetch()
```

---

### 8. How do you execute a coroutine?

```python
asyncio.run(main())
```

---

### 9. What is asyncio?

Python's built-in asynchronous programming library.

---

### 10. What is the Event Loop?

The scheduler that executes, pauses and resumes coroutines.

---

# ⭐ Intermediate Level

### 11. Blocking vs Non-blocking?

| Blocking | Non-blocking |
|-----------|--------------|
| Waits | Doesn't wait |
| Stops thread | Releases thread |
| Slow I/O | Efficient I/O |

---

### 12. Sync vs Async?

Sync executes tasks sequentially.

Async overlaps waiting time.

---

### 13. Concurrency vs Parallelism?

Concurrency = multiple tasks making progress.

Parallelism = multiple CPU cores executing simultaneously.

---

### 14. CPU-bound vs IO-bound?

CPU-bound → multiprocessing

IO-bound → asyncio

---

### 15. What is asyncio.run()?

Starts an event loop and executes the main coroutine.

---

### 16. What is asyncio.sleep()?

Non-blocking sleep.

---

### 17. Difference between time.sleep() and asyncio.sleep()?

| time.sleep | asyncio.sleep |
|-------------|---------------|
| Blocks thread | Doesn't block |
| Stops everything | Lets other tasks run |

---

### 18. What is create_task()?

Schedules a coroutine for concurrent execution.

```python
task = asyncio.create_task(fetch())
```

---

### 19. What is gather()?

Runs multiple coroutines concurrently.

```python
await asyncio.gather(a(), b(), c())
```

---

### 20. gather() vs create_task()?

create_task() schedules.

gather() schedules + waits.

---

### 21. What is wait()?

Waits until tasks finish.

---

### 22. What is wait_for()?

Adds timeout.

---

### 23. What is as_completed()?

Returns tasks as soon as they finish.

---

### 24. What is a Task?

A scheduled coroutine managed by the event loop.

---

### 25. What is a Future?

Placeholder for a value available later.

---

# ⭐ Advanced Level

### 26. What is a Race Condition?

Multiple coroutines modifying shared data simultaneously.

---

### 27. How do you avoid race conditions?

```python
asyncio.Lock()
```

---

### 28. What is Semaphore?

Limits concurrent tasks.

Example:

Only 5 API requests at once.

---

### 29. What is Queue?

Producer-Consumer communication.

---

### 30. What is async with?

Async context manager.

---

### 31. What is async for?

Iterates asynchronous data streams.

---

### 32. What is aiohttp?

Asynchronous HTTP client/server library.

---

### 33. Why use aiohttp instead of requests?

requests is blocking.

aiohttp is asynchronous.

---

### 34. Why does FastAPI recommend async?

Handles thousands of concurrent requests efficiently.

---

### 35. Can async speed up CPU-heavy work?

❌ No.

---

### 36. Why?

Async only improves waiting time.

---

### 37. When should you avoid async?

- Image Processing
- Video Encoding
- ML Training
- Matrix Operations

---

### 38. Multiprocessing vs Async?

| Multiprocessing | Async |
|----------------|-------|
| CPU-bound | IO-bound |
| Multiple CPUs | Single thread |
| Heavy computation | Waiting operations |

---

### 39. Multithreading vs Async?

Threads use OS scheduling.

Async uses event loop scheduling.

---

### 40. Can async replace threading?

No.

Each solves different problems.

---

# ⭐ Scenario Questions

### 41. Download 1000 images quickly?

Use:

- asyncio
- aiohttp
- gather()

---

### 42. Build ChatGPT API backend?

Use Async.

---

### 43. Web scraping 10,000 pages?

Use Async.

---

### 44. AI Agent making multiple API calls?

Use Async.

---

### 45. FastAPI backend?

Use Async.

---

### 46. Database CRUD API?

Use Async ORM.

---

### 47. Live Chat Application?

Use WebSockets + Async.

---

### 48. Notification Service?

Use Async Workers.

---

### 49. Telegram Bot?

Use Async.

---

### 50. Discord Bot?

Use Async.

---

# ⭐ Code Output Questions

### Q51

```python
async def hello():
    print("Hi")

hello()
```

Output?

✅ No output.

Returns coroutine object.

---

### Q52

```python
asyncio.run(hello())
```

Output?

```
Hi
```

---

### Q53

```python
await asyncio.sleep(2)
```

Does it block?

❌ No.

---

### Q54

```python
time.sleep(2)
```

Blocks Event Loop?

✅ Yes.

---

### Q55

```python
await gather(a(), b())
```

Sequential?

❌ Concurrent.

---

# ⭐ Common Interview Mistakes

❌ Forgetting `await`

❌ Mixing sync and async incorrectly

❌ Using `requests` inside async code

❌ Using `time.sleep()`

❌ Creating tasks without awaiting results

❌ Running CPU-heavy loops in async

❌ Blocking the event loop

---

# ⭐ Libraries to Mention

- asyncio
- aiohttp
- httpx
- aiofiles
- asyncpg
- SQLAlchemy Async
- FastAPI
- websockets
- anyio

---

# ⭐ Real-world Use Cases

✔ FastAPI

✔ AI Agents

✔ MCP Servers

✔ RAG Systems

✔ LLM APIs

✔ Chat Applications

✔ Web Scraping

✔ Background Workers

✔ Streaming APIs

✔ Notification Services

---

# ⭐ Interview Rapid Fire

| Question | Answer |
|----------|--------|
| async keyword? | Defines coroutine |
| await keyword? | Pause without blocking |
| Event Loop? | Scheduler |
| create_task()? | Concurrent task |
| gather()? | Run multiple tasks |
| Semaphore? | Limit concurrency |
| Lock? | Prevent race condition |
| Queue? | Producer-Consumer |
| aiohttp? | Async HTTP client |
| FastAPI async? | Better concurrency |
| CPU-bound? | Multiprocessing |
| IO-bound? | Asyncio |
| requests? | Blocking |
| aiohttp? | Non-blocking |
| sleep()? | asyncio.sleep() |

---

# ⭐ One-Liner Revision

```
async → Coroutine

await → Pause

Event Loop → Scheduler

Task → Running Coroutine

Future → Future Result

create_task → Concurrent Task

gather → Run Many

Semaphore → Limit Tasks

Lock → Protect Resource

Queue → Communication

aiohttp → Async Requests

FastAPI → Async Backend

WebSockets → Real-time Apps

Async = Best for IO-bound Workloads
```
