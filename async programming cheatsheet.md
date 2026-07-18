#  Async Python Cheat Sheet

> **One-page reference for Modern Python Async Programming (Python 3.11+)**

---

##  Core Concepts

| Term | Meaning |
|------|---------|
| **Synchronous** | Tasks execute one after another |
| **Asynchronous** | Tasks pause while waiting so others can run |
| **Concurrency** | Managing multiple tasks at the same time (not necessarily in parallel) |
| **Parallelism** | Running tasks simultaneously on multiple CPU cores |
| **Coroutine** | An async function that can pause and resume |
| **Event Loop** | Scheduler that runs and resumes coroutines |
| **Task** | A coroutine scheduled by the event loop |
| **Future** | Placeholder for a value available later |

---

#  Sync vs Async

```
SYNC

Task1
██████████

Task2
██████████

Task3
██████████

Total = 9 sec
```

```
ASYNC

Task1 █──────█
Task2 ─█─────█
Task3 ──█────█

Total = 3 sec
```

---

#  Keywords

```python
async
await
```

```python
async def fetch():
    ...

await fetch()
```

---

#  Event Loop

```
Coroutine
      │
      ▼
Event Loop
      │
      ▼
Task Running
      │
await I/O
      │
      ▼
Run Another Task
      │
      ▼
Resume Previous Task
```

---

#  Basic Syntax

```python
import asyncio

async def hello():
    print("Hello")

asyncio.run(hello())
```

---

#  Waiting

```python
await asyncio.sleep(2)
```

X Don't use

```python
time.sleep(2)
```

---

#  Create Tasks

```python
task = asyncio.create_task(fetch())
```

Run independently.

---

#  Run Multiple Tasks

```python
await asyncio.gather(
    task1(),
    task2(),
    task3()
)
```

---

#  Timeout

```python
await asyncio.wait_for(fetch(), timeout=5)
```

---

#  Wait for Completion

```python
done, pending = await asyncio.wait(tasks)
```

---

# First Finished

```python
async for result in asyncio.as_completed(tasks):
    print(await result)
```

---

#  Lock

```python
lock = asyncio.Lock()

async with lock:
    ...
```

Prevents race conditions.

---

#  Semaphore

```python
sem = asyncio.Semaphore(5)

async with sem:
    ...
```

Limits concurrent tasks.

---

#  Queue

```python
queue = asyncio.Queue()

await queue.put(item)

item = await queue.get()

queue.task_done()
```

Producer → Consumer

---

#  Async Files

```python
import aiofiles

async with aiofiles.open("file.txt") as f:
    text = await f.read()
```

---

#  Async HTTP

```python
import aiohttp

async with aiohttp.ClientSession() as session:
    async with session.get(url) as r:
        data = await r.json()
```

---

#  Async Database

```python
asyncpg
SQLAlchemy Async
```

---

#  Async FastAPI

```python
@app.get("/")
async def home():
    return {"ok": True}
```

---

#  Async Iteration

```python
async for item in stream():
    ...
```

---

#  Async Context Manager

```python
async with connection:
    ...
```

---

#  Common Functions

| Function | Purpose |
|----------|---------|
| asyncio.run() | Start event loop |
| create_task() | Schedule coroutine |
| gather() | Run many tasks |
| wait() | Wait for tasks |
| wait_for() | Timeout |
| as_completed() | Process finished tasks |
| current_task() | Current running task |
| all_tasks() | All scheduled tasks |
| sleep() | Non-blocking delay |

---

#  Popular Libraries

- asyncio
- aiohttp
- aiofiles
- httpx
- FastAPI
- asyncpg
- SQLAlchemy Async
- websockets
- anyio
- aiosqlite

---

#  Real-World Uses

- FastAPI APIs

- AI Agents

- MCP Servers

- Web Scraping

- Chat Applications

- Discord Bots

- Telegram Bots

- Background Workers

- Notification Systems

- Streaming APIs

---

# X Common Mistakes

```python
await my_function()
```

✔ Correct

---

```python
my_function()
```

X Forgot `await`

---

```python
time.sleep(5)
```

X Blocks Event Loop

Use

```python
await asyncio.sleep(5)
```

---

```python
requests.get()
```

X Blocking HTTP

Use

```python
aiohttp
httpx.AsyncClient
```

---

```python
for url in urls:
    await fetch(url)
```

X Sequential

Use

```python
await asyncio.gather(*tasks)
```

---

#  Don't Use Async For

X Heavy Matrix Computations

X Image Processing

X Machine Learning Training

X Video Encoding

X CPU-heavy Loops

Use:

- multiprocessing
- concurrent.futures
- Ray
- Dask

---

#  Async Design Patterns

✔ Fire & Forget

✔ Producer–Consumer

✔ Worker Pool

✔ Fan-Out / Fan-In

✔ Pipeline

✔ Rate Limiter

✔ Retry with Backoff

✔ Circuit Breaker

✔ Pub/Sub

---

#  Interview One-Liners

- `async` defines a coroutine.
- `await` pauses a coroutine without blocking the thread.
- The **Event Loop** schedules coroutines.
- `create_task()` runs a coroutine concurrently.
- `gather()` waits for multiple coroutines together.
- `Semaphore` limits concurrency.
- `Lock` protects shared resources.
- Async is best for **I/O-bound** workloads.
- Multiprocessing is best for **CPU-bound** workloads.

---

#  Async Learning Flow

```
def
   ↓
async def
   ↓
await
   ↓
Event Loop
   ↓
Tasks
   ↓
gather()
   ↓
Locks
   ↓
Queues
   ↓
aiohttp
   ↓
FastAPI
   ↓
WebSockets
   ↓
AI Agents
   ↓
MCP Servers
```
