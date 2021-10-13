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

Symbols can be used as object properties. Additionally, symbols are not enumerated (for example, they are ignored in `for ... in` loop and `Object.keys()` method). This allows us to create kind of "hidden" properties that prevent accidantal access. 

```javascript
const id = Symbol('id');
const myObj = {
  description: "Lorem Ipsum is simply dummy text",
  toggled: false,
  [id]: "My secret key"
};

// A (non-enumerable) symbol property demo:
console.log(Object.keys(myObj)); // => ['description', 'toggled']

for (const prop in myObj) {
  console.log(prop);
}
// => 'description'
// => 'toggled'
```

### Use Case 2: System Symbols

There are many JavaScript symbols which are accessible by `Symbol.*`. For example:

* [`Symbol.iterator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator)
* [`Symbol.toPrimitive`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/toPrimitive)
* [`Symbol.hasInstance`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/hasInstance)
* etc...

With the help of `Symbol.iterator` we can specify iterator for an object:

```
const iterableObject = {
  value: '🧑‍💻',
  anotherValue: '🚀',
};

iterableObject[Symbol.iterator] = function* () {
    yield* Object.values(this);
};

for (let value of iterableObject) {
  console.log(value);
}
```

### Symbol.for





Links:

* [MDN | list of system symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol?retiredLocale=uk#static_properties)
* [MDN | yield\* expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield\*?retiredLocale=uk)
* [MDN | Symbol.for()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/for)
