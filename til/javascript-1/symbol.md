---
description: >-
  Symbols are created using `Symbol(optionalDesc)`. Symbols are always different
  values. They are mainly used for two things: to create "hidden" object
  properties and to alter some built-in behaviors.
---

# Symbol

### Symbols

```javascript
// ✨ Creation
const id = Symbol(); // Symbol without description
const blockId = Symbol('ID'); // Symbol with description

// Access Symbol description
id.description; // => undefined
blockId.description // => "ID"

// Types
typeof id; // => "symbol":
```

**Symbols are guaranteed to be unique**. For example, we can create two symbols with the same description but they will not be equal:

```javascript
const symbol = Symbol("Cool Symbol 🚀");
const symbol2 = Symbol("Cool Symbol 🚀");

console.log(symbol === symbol2); // => false
```

### Use Case 1: Create "hidden" object props

TODO

### Use Case 2: Global Symbol Registry

TODO
