## Redis Semaphore

### Semaphore Utility for Managing Concurrency in Shared Resources Using Redis

This repository contains a `Semaphore` class designed to implement semaphore-like control over access to variables using a Redis server. This utility is particularly useful for synchronizing access to shared resources in distributed systems, ensuring that concurrent processes can safely and efficiently manage shared resources without conflicts.

### Features

- **Acquire Locks:** Safely acquire locks on variables, ensuring exclusive access to prevent race conditions and data corruption.
- **Release Locks:** Release locks when tasks are complete, allowing other processes to acquire them and maintain smooth workflow.
- **Check Lock Status:** Retrieve the status of locks to monitor and manage access effectively, ensuring transparency in resource allocation.
- **Timeout Management:** Locks come with an expiration time to prevent deadlocks and ensure timely resource availability, thus maintaining system robustness.

### Installation

To use this utility, ensure you have Redis installed and running on your system.

### Usage

Below is an example demonstrating how to use the `Semaphore` class to handle concurrent access to shared resources:

```python
from semaphore import Semaphore

# Creating a Semaphore instance
semaphore = Semaphore()

# Acquiring a lock for a variable
lock_acquired = semaphore.acquire_lock(var_name='my_variable', task_name='my_task')
if lock_acquired:
    print("Lock acquired successfully.")
else:
    print("Failed to acquire lock.")

# Releasing a lock for a variable
lock_released = semaphore.release_lock(var_name='my_variable')
if lock_released:
    print("Lock released successfully.")
else:
    print("Failed to release lock.")

# Checking the status of a lock
lock_status = semaphore.status_lock(var_name='my_variable')
print(f"Lock status: {lock_status}")
```

### Configuration

You can configure the default timeout and Redis server URL during initialization:

```python
semaphore = Semaphore(default_timeout=1800, redis_server='redis://localhost:6379')
```

### Dependencies

- `ct_libs.helpers.logging`: Logging utility.
- `ct_libs.helpers.redis`: Redis connection and encoding/decoding utilities.

Ensure these dependencies are available in your environment.

### License

This project is licensed under the MIT License.

---

### Repository Structure

- `semaphore.py`: The main module containing the `Semaphore` class.
- `README.md`: This file, provides an overview and usage instructions.

Feel free to contribute by opening issues or submitting pull requests. Your feedback and improvements are welcome!
