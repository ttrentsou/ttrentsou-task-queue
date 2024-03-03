````markdown
# Task Queue Package

Task Queue Package is a simple Node.js package that provides functionality to create and manage a queue of tasks with a specified concurrency level.

## Installation

You can install the package via npm:

```bash
npm install task-queue-package
```

## Usage

```javascript
const TaskQueue = require('task-queue-package');

// Create an instance of TaskQueue with the desired concurrency level
const taskQueue = new TaskQueue(2);

// Define some example tasks
const tasks = [
  (callback) => {
    console.log('Task 1 started');
    setTimeout(() => {
      console.log('Task 1 completed');
      callback();
    }, 2000);
  },
  (callback) => {
    console.log('Task 2 started');
    setTimeout(() => {
      console.log('Task 2 completed');
      callback();
    }, 1000);
  },
  (callback) => {
    console.log('Task 3 started');
    setTimeout(() => {
      console.log('Task 3 completed');
      callback();
    }, 3000);
  }
];

// Push tasks into the queue
tasks.forEach(task => {
  taskQueue.pushTask(task);
});
```

## API

### `TaskQueue(concurrency)`

Creates a new instance of TaskQueue with the specified concurrency level.

- `concurrency` (number): The maximum number of tasks that can run concurrently.

### `pushTask(task)`

Pushes a task into the queue.

- `task` (function): A function representing the task to be executed. It should accept a callback function as its argument, which should be called once the task is complete.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
