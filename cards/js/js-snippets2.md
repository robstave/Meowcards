<!-- Card Start -->
### Front
Why should you usually use `const` when defining a class in JavaScript?

### Back
Because a class is just a value (a constructor function). Using `const` prevents reassigning the class binding while still allowing unlimited instance creation.

- `const MyClass = class { /* ... */ }` → can do `new MyClass()` many times
- Prevents accidental `MyClass = somethingElse` later
- Encourages immutability of the binding (good practice)

Instances are unaffected: `const` freezes the variable binding, not the class’s ability to create new objects.

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the difference between `for (c in chars)` and `for (c of chars)`?

### Back
- `for...in` iterates enumerable property KEYS (for arrays/strings: index keys like "0", "1", ...)
- `for...of` iterates the VALUES of any iterable (Arrays, Strings, Maps, Sets)

Array example:
```javascript
const chars = ['a', 'b', 'c'];
for (const c in chars) console.log(c);    // 0, 1, 2 (indexes as strings)
for (const c of chars) console.log(c);    // a, b, c (values)
```

String + Unicode example:
```javascript
const s = '😺a';
for (const i in s) console.log(i);        // 0, 1, 2 (UTF-16 code unit indexes)
for (const ch of s) console.log(ch);      // 😺, a (code points)
```

<!-- Card End -->

<!-- Card Start -->
### Front
When should you use `for...in` vs `for...of` with arrays/strings, and what are the gotchas?

### Back
- Prefer `for...of` for arrays/strings to get values directly (Unicode-aware for strings)
- Avoid `for...in` on arrays: it iterates keys (including non-index/inherited) and order isn’t guaranteed
- Use `for...in` for plain object property keys; otherwise use `Object.keys/entries` with `for...of`

Tips:
- Need index + value? `for (const [i, v] of chars.entries()) { ... }`
- If you must use keys: `for (const i of Object.keys(arr)) { const v = arr[i]; }`

<!-- Card End -->

<!-- Card Start -->
### Front
What JavaScript concept does this code demonstrate, and what does it log?

```javascript
function outer(x) {
  return function inner(y) {
    return x + y;
  };
}

const addFive = outer(5);
console.log(addFive(3));
```

### Back
This demonstrates a closure (and partial application/currying).

- `inner` closes over `x` from `outer`’s scope, preserving it after `outer` returns
- `addFive` is a function that adds 5 to its argument
- The code logs `8`

Arrow form:

```javascript
const outer = (x) => (y) => x + y;
```

Key idea: lexical scoping lets inner functions remember variables from their defining scope.

<!-- Card End -->

<!-- Card Start -->
### Front
What are inner functions in JavaScript, and why use them?

### Back
An inner function is a function defined inside another function. It forms a closure over the outer scope, so it can read (and mutate) outer variables even after the outer function returns.

Typical uses:
- Helper utilities scoped to a single function (not exported globally)
- Encapsulation/private state without classes
- Function factories, currying/partial application

Example:
```javascript
function makeAdder(a) {
  function add(b) { return a + b; } // inner function closes over a
  return add;
}
const add10 = makeAdder(10);
add10(5); // 15
```

<!-- Card End -->

<!-- Card Start -->
### Front
Inner functions: scope, hoisting, and `this` — what should you watch out for?

### Back
- Scope/hoisting:
  - Inner function declarations are hoisted within the enclosing function scope
  - Inner function expressions follow `var/let/const` rules (TDZ for `let`/`const`)
- `this` binding:
  - Normal inner functions get `this` from how they’re called
  - Arrow inner functions capture the outer lexical `this`
- Loops/closures: prefer `let` in loops or capture values to avoid late-binding pitfalls with `var`

Examples:
```javascript
const obj = {
  n: 0,
  incLater() {
    setTimeout(() => { this.n++; }, 0); // arrow keeps obj as this
    // setTimeout(function() { this.n++; }.bind(this), 0); // alternative
  }
};

function outer() {
  // declaration is hoisted inside outer
  function helper() { return 42; }
  const expr = () => 7; // follows const/TDZ
  return helper() + expr();
}
```

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the quickest way to build a character frequency counter with a plain object?

### Back
Use the classic fallback-increment pattern. Optionally use a null-prototype object to avoid prototype key collisions.

```javascript
// Simple
const charCount = {};
for (const ch of s) {
  charCount[ch] = (charCount[ch] || 0) + 1;
}

// Safer (no inherited props) + nullish coalescing
const cnt = Object.create(null);
for (const ch of s) {
  cnt[ch] = (cnt[ch] ?? 0) + 1;
}
```

Notes:
- `|| 0` treats 0, '', false as falsy; `?? 0` only treats null/undefined as missing
- Use `Object.create(null)` if keys might be like `__proto__`

<!-- Card End -->

<!-- Card Start -->
### Front
How do you build a frequency counter with `Map`, and why prefer it sometimes?

### Back
`Map` works with any key type and avoids string coercion. Increment with `get`/`set`.

```javascript
const counts = new Map();
for (const ch of s) {
  counts.set(ch, (counts.get(ch) ?? 0) + 1);
}

// Reading
const aCount = counts.get('a') || 0;
```

Alternative with `reduce`:

```javascript
const counts2 = [...s].reduce((m, ch) => m.set(ch, (m.get(ch) || 0) + 1), new Map());
```

Prefer `Map` when keys aren’t strings, you need guaranteed insertion order iteration, or you want clearer intent.

<!-- Card End -->

<!-- Card Start -->
### Front
In one line, what’s the essence of DFS?

### Back
DFS is about exploring possibilities: walk the search space (tree/graph) path-by-path, often via recursion/backtracking, to enumerate or find valid solutions.

- Great for generating permutations/combinations, path finding, constraint satisfaction
- Not inherently optimal; may revisit equivalent subproblems without pruning

<!-- Card End -->

<!-- Card Start -->
### Front
In one line, what’s the essence of Dynamic Programming (DP)?

### Back
DP is about optimizing exploration by reusing work: solve overlapping subproblems once and reuse results to avoid recomputation.

- Requires overlapping subproblems + optimal substructure
- Can be top-down (memoized recursion) or bottom-up (tabulation)

<!-- Card End -->

<!-- Card Start -->
### Front
How do DFS and DP overlap via memoization?

### Back
Memoization turns DFS into top-down DP: cache results keyed by state so repeated states return instantly.

- Keep DFS structure (backtracking, constraints)
- Add a map `state → answer` to prune exponential revisits
- Often converts exponential time to near-polynomial on problems with heavy overlap

<!-- Card End -->

<!-- Card Start -->
### Front
When should you use plain DFS, DP, or DFS + memoization?

### Back
- Use DFS when the space is small/moderately sized or you need to enumerate all solutions
- Use DP when you can define clear subproblem states and transitions and need optimal counts/values
- Use DFS + memoization when exploring a large constrained space with repeated states (scheduling, knapsack variants, grid paths)

Tip: Start with DFS, identify repeated states, then add memoization for a quick win.

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the difference between a singly and a doubly linked list?

### Back
- Singly: each node has `value` and `next`. Forward traversal only. Lower memory.
- Doubly: nodes have `value`, `next`, and `prev`. Bidirectional traversal. Easier deletes/inserts in middle but more memory and maintenance.

Use singly for simple stacks/queues; use doubly when frequent backward movement or O(1) delete given a node.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you represent a linked list node in JavaScript?

### Back
Minimal class/constructor example:

```javascript
class ListNode {
  constructor(val, next = null) {
    this.val = val;
    this.next = next;
  }
}
```

Head is a reference to the first node (or `null` for empty).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you traverse a singly linked list and collect values?

### Back
Iterate from `head` while advancing `current = current.next`.

```javascript
function toArray(head) {
  const out = [];
  for (let cur = head; cur; cur = cur.next) out.push(cur.val);
  return out;
}
```

Time O(n), space O(n) for array (O(1) if just visiting).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you insert at the head and at the tail of a singly linked list?

### Back
Head insert (O(1)):

```javascript
function pushFront(head, val) {
  return new ListNode(val, head);
}
```

Tail insert (O(n) without tail pointer):

```javascript
function pushBack(head, val) {
  const node = new ListNode(val);
  if (!head) return node;
  let cur = head;
  while (cur.next) cur = cur.next;
  cur.next = node;
  return head;
}
```

Maintain a tail pointer to make tail insert O(1).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you delete the first node with a given value from a singly linked list?

### Back
Track previous and current; adjust `prev.next`.

```javascript
function deleteValue(head, target) {
  if (!head) return head;
  if (head.val === target) return head.next;
  let prev = head, cur = head.next;
  while (cur) {
    if (cur.val === target) { prev.next = cur.next; break; }
    prev = cur; cur = cur.next;
  }
  return head;
}
```

Time O(n), space O(1).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you reverse a singly linked list iteratively?

### Back
Relink pointers using three variables.

```javascript
function reverseList(head) {
  let prev = null, cur = head;
  while (cur) {
    const next = cur.next;
    cur.next = prev;
    prev = cur;
    cur = next;
  }
  return prev;
}
```

Time O(n), space O(1).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you detect a cycle in a linked list?

### Back
Use Floyd’s tortoise and hare algorithm.

```javascript
function hasCycle(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow === fast) return true;
  }
  return false;
}
```

Time O(n), space O(1). With a `Set`, it’s O(n) space.

<!-- Card End -->

<!-- Card Start -->
### Front
How do you find the middle node of a singly linked list?

### Back
Fast/slow pointers: move `slow` by 1, `fast` by 2.

```javascript
function middleNode(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  return slow; // in even length, returns the second middle
}
```

Time O(n), space O(1).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you remove the Nth node from the end in one pass?

### Back
Two pointers spaced `n` apart; then move both until the lead hits the end.

```javascript
function removeNthFromEnd(head, n) {
  const dummy = new ListNode(0, head);
  let fast = dummy, slow = dummy;
  for (let i = 0; i < n; i++) fast = fast.next;
  while (fast.next) { fast = fast.next; slow = slow.next; }
  slow.next = slow.next.next;
  return dummy.next;
}
```

Time O(n), space O(1).

<!-- Card End -->

<!-- Card Start -->
### Front
How do you merge two sorted singly linked lists into one sorted list?

### Back
Use a dummy head and stitch nodes in order.

```javascript
function mergeTwoLists(l1, l2) {
  const dummy = new ListNode(0);
  let cur = dummy;
  while (l1 && l2) {
    if (l1.val <= l2.val) { cur.next = l1; l1 = l1.next; }
    else { cur.next = l2; l2 = l2.next; }
    cur = cur.next;
  }
  cur.next = l1 || l2;
  return dummy.next;
}
```

Time O(n+m), space O(1) extra.

<!-- Card End -->

<!-- Card Start -->
### Front
What are typical time/space complexities for common singly linked list ops?

### Back
- Access by index: O(n)
- Insert/delete at head: O(1)
- Insert/delete at tail: O(1) with tail pointer; otherwise O(n)
- Search by value: O(n)
- Reverse: O(n) time, O(1) space
- Detect cycle (Floyd): O(n) time, O(1) space

Linked lists trade random access for cheap structural mutation.

<!-- Card End -->


<!-- Card Start -->
### Front
What is a JavaScript class under the hood?

### Back
Syntactic sugar for a constructor function plus prototype methods. The identifier points to that constructor value.

```javascript
class MyClass {
  constructor(name) { this.name = name; }
}
// Roughly akin to a constructor function with methods on the prototype
```

So “the class” is a value bound to a variable name.

<!-- Card End -->

<!-- Card Start -->
### Front
Why not use `var` to declare classes?

### Back
- `var` is function-scoped (not block-scoped) and hoisted (initialized as `undefined`)
- Easier to accidentally overwrite or leak outside blocks
- Modern JavaScript style avoids `var` in favor of `let`/`const`

Prefer block-scoped `const` for class bindings to reduce bugs and improve clarity.

<!-- Card End -->

<!-- Card Start -->
### Front
When does `let` make sense for class declarations?

### Back
Use `let` if you intend to reassign the binding (rare but valid):

```javascript
let MyClass = class {};
MyClass = class extends MyClass { /* enhance or swap impl */ };
```

If you don’t need reassignment, choose `const`.

<!-- Card End -->

<!-- Card Start -->
### Front
What’s the subtle difference between `class MyClass {}` and `const MyClass = class {}`?

### Back
Both create a block-scoped binding named `MyClass`, and both are in the TDZ until evaluated (not usable before the line).

Differences:
- Declaration vs expression style: `class MyClass {}` is a declaration; `const MyClass = class {}` binds a class expression to a `const` variable
- Class expressions can be anonymous or have an internal name for self-reference:
  ```javascript
  const MyClass = class NamedInside { /* use NamedInside only inside the class body */ };
  ```
- Using `const` makes the outer binding non-reassignable by construction; a plain class declaration doesn’t by itself imply `const`, but its binding is still not re-declarable in the same scope

In practice, both work similarly; teams often prefer `const = class {}` to signal an immutable binding.

<!-- Card End -->

const 