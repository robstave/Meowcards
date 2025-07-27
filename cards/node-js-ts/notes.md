 ChatGPT said:
Here’s your flashcard deck in the style you like — simple Q&A format, great for study or import into tools like Obsidian or Anki:

Q: What is the Node.js event loop used for?
A: To handle asynchronous I/O in a single-threaded environment by offloading tasks and executing callbacks when ready.

Q: Name the main phases of the Node.js event loop.
A: Timers, Pending Callbacks, Idle/Prepare, Poll, Check, Close Callbacks.

Q: What is the difference between microtasks and macrotasks in Node.js?
A: Microtasks (e.g., process.nextTick, Promise.then) run immediately after the current operation and before the event loop continues. Macrotasks (e.g., setTimeout, setImmediate) are scheduled for specific event loop phases.

Q: In what order do the following run? setTimeout, setImmediate, process.nextTick, Promise.then
A: process.nextTick → Promise.then → (setTimeout or setImmediate, order may vary depending on context)

Q: What is process.nextTick() used for?
A: It defers the execution of a callback until the current call stack is cleared, before the next event loop tick.

Q: What happens if you throw an error inside a setTimeout() callback?
A: It will cause an uncaught exception unless handled inside the callback. The process may crash if not handled globally.

Q: How do you handle uncaught exceptions globally in Node.js?
A: Use process.on('uncaughtException', handler) to log or clean up, but always exit the process afterward.

Q: How do you handle unhandled Promise rejections globally in Node.js?
A: Use process.on('unhandledRejection', handler) to log or recover, but prefer handling rejections locally.

Q: Why is it a bad idea to rely solely on uncaughtException or unhandledRejection?
A: They are for last-resort handling and don’t allow safe recovery. The app state might be corrupted—graceful shutdown is preferred.

Q: What tool can you use to auto-restart a Node.js process on fatal errors?
A: A process manager like PM2, or use container health checks (e.g., with Docker or Kubernetes).

Q: What is a safe pattern for global error handling?
A: Log the error, clean up resources, and exit with process.exit(1) to allow a supervisor to restart the app.


diff between var and let

