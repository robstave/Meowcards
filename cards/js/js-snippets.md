<!-- Card Start -->
### Front
What JavaScript loop syntax is used here, and what does it do?

```javascript
for (let fruit of fruits) {
    console.log(fruit);
}
```

### Back
This is the ES6 `for...of` loop.

- Iterates over the values of any iterable (Arrays, Strings, Maps, Sets)
- Yields each element value (not the index/key)
- Cleaner than index-based loops when you only need values

Comparisons:
- `for...of` → values: `for (const v of arr) {}`
- `for...in` → keys/indexes (object property names); not recommended for arrays
- Classic `for (let i=0; i<arr.length; i++)` → manual index control

Tip: Need index and value? `for (const [i, v] of fruits.entries()) { ... }`

<!-- Card End -->

<!-- Card Start -->
### Front
In JavaScript, what does the `entries()` method return and how do you iterate it?

### Back
`entries()` returns an iterator of pairs you can loop with `for...of`:

- Arrays → `[index, value]`
- Maps → `[key, value]`
- Sets → `[value, value]` (same value twice for compatibility)

Examples:

```javascript
// Array
for (const [i, v] of ["a", "b"].entries()) {
    console.log(i, v);
}

// Map
const m = new Map([["k1", 1], ["k2", 2]]);
for (const [k, v] of m.entries()) {
    console.log(k, v);
}
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do you traverse a `Set` vs a `Map`, and what does `for...of` yield for each?

### Back
- `Set`: `for...of` yields values
- `Map`: `for...of` yields `[key, value]` pairs

```javascript
const s = new Set(["a", "b"]);
for (const v of s) {
    console.log(v); // a, b
}

const m = new Map([["k1", 1], ["k2", 2]]);
for (const [k, v] of m) {
    console.log(k, v); // k1 1, k2 2
}
```

<!-- Card End -->

<!-- Card Start -->
### Front
What are the key differences between `forEach` and `for...of`?

### Back
- Control flow: `for...of` supports `break`/`continue`/`return`; `forEach` does not
- Async: `await` works inside `for...of`; `forEach` callbacks aren’t awaited
- Scope/API: `forEach` is a method (Arrays, Maps, Sets); `for...of` works on any iterable

```javascript
// Async handling
for (const url of urls) {
    const res = await fetch(url); // OK
}

urls.forEach(async (url) => {
    await fetch(url); // Not awaited by forEach
});
```

<!-- Card End -->

<!-- Card Start -->
### Front
How does `for (const [i, v] of fruits.entries())` work, and when should you use it?

### Back
`Array.prototype.entries()` produces `[index, value]` pairs; array destructuring gives you both in the loop.

```javascript
const fruits = ["apple", "banana", "cherry"];
for (const [i, v] of fruits.entries()) {
    console.log(i, v); // 0 apple, 1 banana, 2 cherry
}
```

Use it when you need both index and value without managing a manual counter.

<!-- Card End -->

<!-- Card Start -->
### Front
Does using `array.forEach(async ...)` send requests in parallel? Does the caller wait?

### Back
- The async callbacks are invoked immediately and start tasks concurrently.
- `forEach` does not await them, so the surrounding code continues without waiting.
- Think “concurrent requests in flight,” not guaranteed CPU parallelism.

To wait for them to finish, collect promises and `await` them:

```javascript
const promises = urls.map((u) => fetch(u));
const responses = await Promise.all(promises); // waits for all or throws on first rejection
```

If you need to observe all outcomes without short-circuiting:

```javascript
const results = await Promise.allSettled(urls.map((u) => fetch(u)));
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do you run multiple requests concurrently and wait for completion?

### Back
Use `map` to create promises and `await Promise.all`:

```javascript
const data = await Promise.all(
    urls.map(async (u) => {
        const res = await fetch(u);
        if (!res.ok) throw new Error(`${u} failed`);
        return res.json();
    })
);
```

Notes:
- `Promise.all` rejects fast on the first failure; use `allSettled` for best-effort aggregation.
- Order of results matches order of input.

<!-- Card End -->

<!-- Card Start -->
### Front
How can you limit concurrency (e.g., 3 at a time) without extra libraries?

### Back
Process in batches and `await` each batch:

```javascript
const chunk = (arr, n) => arr.reduce((a, _, i) => (i % n ? a : [...a, arr.slice(i, i + n)]), []);

for (const group of chunk(urls, 3)) {
    await Promise.all(group.map((u) => fetch(u)));
}
```

This keeps at most 3 concurrent requests. For fine-grained control, consider a small promise pool or a utility like `p-limit`.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you run async tasks strictly one-by-one in order?

### Back
Use `for...of` with `await` for sequential execution:

```javascript
for (const u of urls) {
    const res = await fetch(u); // next starts only after this awaits
}
```

Alternative with `reduce`:

```javascript
await urls.reduce(
    (p, u) => p.then(() => fetch(u)),
    Promise.resolve()
);
```

Sequential execution is useful when order matters or when the server has strict rate limits.

<!-- Card End -->

<!-- Card Start -->
### Front
What does `Array.prototype.reduce()` do, and how do you use it for a classic sum accumulator?

### Back
`reduce` folds an array into a single value by repeatedly calling a reducer function with an accumulator and the current element.

```javascript
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, n) => acc + n, 0);
// sum = 10
```

Notes:
- Always provide an initial value (here `0`). Without it, the first element is used as the initial accumulator and empty arrays throw.
- Shape of the accumulator is up to you (number, object, Map, etc.).

<!-- Card End -->

<!-- Card Start -->
### Front
How can you count occurrences of values in an array using `reduce`?

### Back
Aggregate into an object (or Map) keyed by the item.

```javascript
const pets = ['cat', 'dog', 'cat', 'bird'];
const counts = pets.reduce((acc, p) => {
    acc[p] = (acc[p] ?? 0) + 1;
    return acc;
}, {});

// counts = { cat: 2, dog: 1, bird: 1 }
```

Tip: Use `new Map()` when keys are not strings or when you need ordered iteration.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you group an array of objects by a property using `reduce`?

### Back
Build a dictionary keyed by the property and push into arrays.

```javascript
const items = [
    { id: 1, type: 'fruit', name: 'apple' },
    { id: 2, type: 'veg', name: 'carrot' },
    { id: 3, type: 'fruit', name: 'banana' }
];

const byType = items.reduce((acc, item) => {
    (acc[item.type] ??= []).push(item);
    return acc;
}, {});

/* byType = {
    fruit: [ {id:1,...}, {id:3,...} ],
    veg:   [ {id:2,...} ]
} */
```

Variation: Use a `Map` for non-string keys or to preserve insertion order reliably.

<!-- Card End -->

<!-- Card Start -->
### Front
What is hoisting in JavaScript, and what actually gets hoisted?

### Back
Hoisting is JavaScript’s compile-time behavior where declarations are processed before code runs.

- `function` declarations: name and body are hoisted (callable before the line appears)
- `var` declarations: name is hoisted and initialized to `undefined`
- `let`/`const`/`class`: names are hoisted but uninitialized (Temporal Dead Zone)

In practice: declarations are known up front; initializations still happen at runtime where written.

```javascript
console.log(x); // undefined (var name hoisted)
var x = 1;

foo();          // OK (function declaration hoisted)
function foo() { /*...*/ }
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do function declarations differ from function expressions and arrow functions with hoisting?

### Back
- Function declarations are fully hoisted (you can call them before their definition line)
- Function expressions/arrow functions assigned to variables follow the variable’s hoisting rules
    - with `var`: variable exists as `undefined` until assignment
    - with `let`/`const`: in TDZ until the declaration line executes

```javascript
declared(); // OK
function declared() {}

// expressed(); // TypeError or ReferenceError depending on var/let/const
var expressed = function () {};
// expressed is undefined until this line; calling earlier is TypeError

// const arrow; // ReferenceError (TDZ) if accessed before this line
const arrow = () => {};
```

Rule of thumb: don’t rely on hoisting; define before use unless it’s a deliberate function declaration pattern.

<!-- Card End -->

<!-- Card Start -->
### Front
What is the Temporal Dead Zone (TDZ) for `let`/`const`/`class` and how does it differ from `var`?

### Back
- `let`/`const`/`class` are hoisted but inaccessible from start of scope until the declaration runs (TDZ)
- Accessing them early throws `ReferenceError` (even with `typeof`)
- `var` is hoisted and initialized to `undefined`, so early access yields `undefined`

```javascript
// console.log(a); // ReferenceError (TDZ)
let a = 1;

console.log(b);   // undefined (var)
var b = 2;

// typeof c; // ReferenceError (TDZ for let/const)
const c = 3;

// class is also TDZ
// new Person(); // ReferenceError
class Person {}
```

Best practices:
- Prefer `const`/`let`; place declarations at top of their scope
- Avoid depending on hoisting for readability and fewer bugs

<!-- Card End -->

<!-- Card Start -->
### Front
What are the scoping differences between `var`, `let`, and `const`?

### Back
- `var` is function-scoped; it ignores block boundaries (`if`, `for`, `{}`)
- `let` and `const` are block-scoped; they exist only inside the nearest `{}` block
- In loops, `let` creates a new binding per iteration; `var` reuses one binding

```javascript
if (true) {
    var x = 1;
    let y = 2;
}
console.log(x); // 1 (leaked)
// console.log(y); // ReferenceError (block-scoped)

for (var i = 0; i < 3; i++) setTimeout(() => console.log('var', i)); // 3,3,3
for (let j = 0; j < 3; j++) setTimeout(() => console.log('let', j)); // 0,1,2
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do hoisting and the Temporal Dead Zone (TDZ) differ for `var`, `let`, and `const`?

### Back
- `var` declarations are hoisted and initialized to `undefined`; accessing before assignment gives `undefined`
- `let`/`const` are hoisted but uninitialized until their declaration line; accessing earlier is a TDZ `ReferenceError`
- `const` also requires an initializer at declaration

```javascript
console.log(a); // undefined (var hoisted)
var a = 1;

// console.log(b); // ReferenceError (TDZ)
let b = 2;

// console.log(c); // ReferenceError (TDZ) and must be initialized
const c = 3;
```

<!-- Card End -->

<!-- Card Start -->
### Front
Which can be reassigned or redeclared, and what about global bindings? When should you use each?

### Back
- Reassignment: `let` can be reassigned; `const` cannot; `var` can be reassigned
- Redeclaration in same scope: `var` allows it; `let`/`const` throw
- `const` freezes the binding, not the value; objects/arrays remain mutable
- Global: top-level `var` creates a property on the global object (e.g., `window.x`); `let`/`const` do not

```javascript
const user = { name: 'Ada' };
// user = {}    // TypeError (rebind)
user.name = 'Lovelace'; // OK (mutate)

var g = 1; // window.g in browsers
let h = 2; // not attached to window
```

Best practice: prefer `const` by default, use `let` when reassignment is needed, avoid `var`.

<!-- Card End -->

<!-- Card Start -->
### Front
What is a closure in JavaScript?

### Back
A closure is the combination of a function and the lexical environment where it was declared. The function remembers variables from its outer scope even after that scope has returned.

```javascript
function makeCounter() {
    let n = 0; // captured
    return () => ++n; // closure uses n
}
const next = makeCounter();
next(); // 1
next(); // 2
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do closures enable private state or encapsulation?

### Back
Use a factory to expose methods that share access to hidden variables.

```javascript
function createBankAccount(balance = 0) {
    return {
        deposit(x) { balance += x; },
        withdraw(x) { if (x <= balance) balance -= x; },
        getBalance() { return balance; }
    };
}
const acct = createBankAccount(10);
acct.deposit(5);
acct.getBalance(); // 15
```

The `balance` is not directly accessible from the outside.

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the classic closure-in-a-loop pitfall and how do you fix it?

### Back
Using `var` captures a single variable that changes, so callbacks see the final value.

```javascript
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 0); // 3,3,3
}

// Fixes:
for (let j = 0; j < 3; j++) { // block-scoped
    setTimeout(() => console.log(j), 0); // 0,1,2
}
// or IIFE
for (var k = 0; k < 3; k++) {
    ((kCopy) => setTimeout(() => console.log(kCopy), 0))(k);
}
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do closures relate to currying and partial application?

### Back
Closures can capture fixed arguments and return a new function that accepts the rest.

```javascript
const add = (a) => (b) => a + b; // curry
const add10 = add(10);
add10(5); // 15

function partial(fn, ...fixed) {
    return (...rest) => fn(...fixed, ...rest);
}
```

Comparison: `Function.prototype.bind` also creates partially applied functions while binding `this`.

<!-- Card End -->

<!-- Card Start -->
### Front
Can closures cause memory leaks? How do you avoid problems?

### Back
Closures keep references alive. If a long-lived closure captures large objects or DOM nodes, they won’t be GC’d.

Tips:
- Null out references when no longer needed
- Prefer narrow scopes; avoid capturing more than necessary
- Unsubscribe event handlers to break closure chains

<!-- Card End -->

<!-- Card Start -->
### Front
What is a Promise and what are its states and handlers?

### Back
A Promise represents a value that may be available now, later, or never.

States: pending → fulfilled | rejected
Handlers: `.then(onFulfilled)`, `.catch(onRejected)`, `.finally(onSettled)`

```javascript
new Promise((res, rej) => res(42))
    .then(x => x + 1)
    .catch(console.error)
    .finally(() => console.log('done'));
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do `async`/`await` simplify Promise handling and error flow?

### Back
`await` pauses within an async function until the Promise settles; use `try/catch` for errors.

```javascript
async function getUser(id) {
    try {
        const res = await fetch(`/users/${id}`);
        if (!res.ok) throw new Error('HTTP');
        return res.json();
    } catch (err) {
        // handle error
        throw err;
    }
}
```

Note: `await` works only directly inside `async` functions (or top-level in supported envs).

<!-- Card End -->

<!-- Card Start -->
### Front
What are the differences among `Promise.all`, `allSettled`, `race`, and `any`?

### Back
- `Promise.all` → waits for all to fulfill; rejects fast on first rejection
- `Promise.allSettled` → waits for all to settle; gives success/failure per item
- `Promise.race` → settles with the first settled promise (fulfill or reject)
- `Promise.any` → fulfills with the first fulfillment; rejects if all reject (AggregateError)

```javascript
const results = await Promise.allSettled(tasks.map(run));
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do you convert a callback-style API into a Promise (promisify)?

### Back
Wrap the function and resolve/reject in the callback.

```javascript
const promisify = (fn) => (...args) =>
    new Promise((resolve, reject) =>
        fn(...args, (err, value) => (err ? reject(err) : resolve(value)))
    );
```

Use with Node-style `(err, value)` callbacks or browser APIs with callbacks.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you run async tasks sequentially vs concurrently with `async`/`await`?

### Back
Sequential (order, rate-limits):

```javascript
for (const item of items) {
    await work(item);
}
```

Concurrent (faster, control with `Promise.all`):

```javascript
const results = await Promise.all(items.map(work));
```

Pick based on dependency, ordering, and resource constraints.

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the difference between `call`, `apply`, and `bind`?

### Back
- `fn.call(thisArg, ...args)` → calls immediately with `this` and arguments list
- `fn.apply(thisArg, argsArray)` → calls immediately with `this` and array of args
- `fn.bind(thisArg, ...args)` → returns a new function with bound `this` and optional partial args

```javascript
function greet(g, n) { return `${g}, ${n}`; }
greet.call(null, 'Hi', 'Ada');      // immediate
greet.apply(null, ['Hi', 'Ada']);   // immediate
const hiAda = greet.bind(null, 'Hi', 'Ada');
hiAda();                            // later
```

<!-- Card End -->

<!-- Card Start -->
### Front
How would you implement a simple `Function.prototype.bind` polyfill?

### Back
```javascript
if (!Function.prototype.myBind) {
    Function.prototype.myBind = function (thisArg, ...boundArgs) {
        const fn = this;
        function boundFn(...callArgs) {
            const isNew = this instanceof boundFn;
            return fn.apply(isNew ? this : thisArg, [...boundArgs, ...callArgs]);
        }
        if (fn.prototype) boundFn.prototype = Object.create(fn.prototype);
        return boundFn;
    };
}
```

Supports partial application and `new` with proper prototype chain.

<!-- Card End -->

<!-- Card Start -->
### Front
How would you implement `Function.prototype.call`?

### Back
```javascript
if (!Function.prototype.myCall) {
    Function.prototype.myCall = function (thisArg, ...args) {
        const ctx = thisArg ?? globalThis;
        const sym = Symbol('fn');
        ctx[sym] = this;
        try { return ctx[sym](...args); }
        finally { delete ctx[sym]; }
    };
}
```

Uses a unique temporary property to invoke with a specific `this`.

<!-- Card End -->

<!-- Card Start -->
### Front
How would you implement `Function.prototype.apply`?

### Back
```javascript
if (!Function.prototype.myApply) {
    Function.prototype.myApply = function (thisArg, args) {
        const ctx = thisArg ?? globalThis;
        const sym = Symbol('fn');
        ctx[sym] = this;
        try { return Array.isArray(args) ? ctx[sym](...args) : ctx[sym](); }
        finally { delete ctx[sym]; }
    };
}
```

Accepts arguments as an array-like and spreads them into the call.

<!-- Card End -->

<!-- Card Start -->
### Front
What is memoization and when should you use it?

### Back
Memoization caches results of pure function calls so repeated calls with the same inputs return instantly.

Use when:
- Function is pure (same inputs → same output)
- Computation is expensive
- Input domain has repetition

Avoid when inputs are large/mutable or memory pressure is a concern.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you implement a simple memoization helper (single or multi-arg)?

### Back
Single-argument (Map):

```javascript
const memo1 = (fn) => {
    const cache = new Map();
    return (x) => cache.has(x) ? cache.get(x) : (cache.set(x, fn(x)), cache.get(x));
};
```

Multiple args (keyed):

```javascript
const memoN = (fn) => {
    const cache = new Map();
    return (...args) => {
        const key = JSON.stringify(args); // simple keying; customize for perf
        if (cache.has(key)) return cache.get(key);
        const val = fn(...args);
        cache.set(key, val);
        return val;
    };
};
```

Consider `WeakMap` for object keys and an eviction strategy for unbounded caches.

<!-- Card End -->
<!-- Card Start -->
### Front
How does `Array.prototype.sort()` work by default, and how do you sort numbers correctly (ASC/DESC)?

### Back
Default behavior is lexicographic (string) compare, and it mutates the array.

```javascript
const nums = [10, 2, 1];
nums.sort();              // [1, 10, 2] (WRONG for numeric intent)

// Numeric ascending / descending
nums.sort((a, b) => a - b); // [1, 2, 10]
nums.sort((a, b) => b - a); // [10, 2, 1]

// Non-mutating pattern (ES6):
const asc = [...nums].sort((a, b) => a - b);
```

Key points:
- Provide a comparator for numeric sorts
- `sort` mutates; clone first with spread if you need immutability

<!-- Card End -->

<!-- Card Start -->
### Front
How do you sort an array of objects by a property (numeric and string)?

### Back
Numeric property:

```javascript
products.sort((a, b) => a.price - b.price);
```

String property (locale-aware):

```javascript
users.sort((a, b) => a.name.localeCompare(b.name));
// Case-insensitive:
users.sort((a, b) => a.name.localeCompare(b.name, undefined, { sensitivity: 'base' }));
```

Notes:
- `localeCompare` handles accents and locale rules better than `a<b ? -1 : 1`
- Clone first if you must keep the original order elsewhere: `const sorted = [...users].sort(...)`

<!-- Card End -->

<!-- Card Start -->
### Front
How do you sort by a date field (ISO string or Date instance)?

### Back
For ISO 8601 strings (e.g., `2024-07-10T12:00:00Z`), string compare works:

```javascript
events.sort((a, b) => a.when.localeCompare(b.when));
```

For general date values, compare timestamps:

```javascript
events.sort((a, b) => new Date(a.when).getTime() - new Date(b.when).getTime());
```

Performance tip (expensive key): precompute, sort, then unwrap (Schwartzian transform):

```javascript
const sorted = events
    .map(e => ({ e, t: new Date(e.when).getTime() }))
    .sort((x, y) => x.t - y.t)
    .map(({ e }) => e);
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do you implement a multi-key sort with tie-breakers?

### Back
Chain comparisons with `||` so the next key is used on ties:

```javascript
people.sort((a, b) =>
    a.last.localeCompare(b.last) ||
    a.first.localeCompare(b.first) ||
    a.id - b.id
);
```

Notes:
- Modern JS engines implement stable sort, so prior order of equal items is preserved
- Keep comparisons fast; avoid heavy work inside the comparator

<!-- Card End -->

<!-- Card Start -->
### Front
How do you avoid mutating the original array when sorting?

### Back
Clone, then sort:

```javascript
const sorted = [...arr].sort((a, b) => a - b);
```

Why:
- `sort` mutates the array in place
- Cloning preserves the original for other consumers

Tip: In very modern JS, `arr.toSorted(cmp)` returns a sorted copy without mutating (not ES6, but useful to know).

<!-- Card End -->


