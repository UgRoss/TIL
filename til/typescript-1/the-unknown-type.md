---
description: The 'unknown' type in TypeScript is the type-safe counterpart of 'any'.
---

# The unknown type

**`unknown` is the type-safe counterpart of `any`.**

> Anything is assignable to `unknown`, but `unknown` isn’t assignable to anything but itself and `any` without a type assertion or a control flow based narrowing. Likewise, no operations are permitted on an `unknown` without first asserting or narrowing to a more specific type.

The easiest way to understand `unknown` is to compare it with `any`. As we know `any` type is used to opt-out of type checking. By using `any` type we can perform any action:

```typescript
let value: any;

value = true;          // ✅ OK
value = 42;            // ✅ OK
value = null;          // ✅ OK
value = undefined;     // ✅ OK
// And so on... We can assign anything

/** ⬇️ The same remains for using our value. We can do whatever we want. */
value.foo.bar;  // ✅ OK
value();        // ✅ OK
value[0][1];    // ✅ OK
new value();    // ✅ OK
```

Just like all types are assignable to `any`, all types are assignable to `unknown`:

```typescript
let value: unknown;

value = true;          // ✅ OK
value = 42;            // ✅ OK
value = null;          // ✅ OK
value = undefined;     // ✅ OK
```

However, we can't simply perform any operations with our variable like it was with `any` type:

```typescript
let value: unknown;

value.foo.bar;  // ❌ ERROR
value();        // ❌ ERROR
value[0][1];    // ❌ ERROR
new value();    // ❌ ERROR

// ================

if (typeof value === 'function') {
    value();    // ✅ OK
}

if (Array.isArray(value)) {
  value[0];    // ✅ OK
} 
```

Additionally, we can't assign `unknown` type to any other types except itself and `any`:

```typescript
let unknownValue: unknown;
let anyValue: any;

let value1: unknown = unknownValue;   // ✅ OK
let value2: any = unknownValue;       // ✅ OK
let value3: unknown = anyValue;       // ✅ OK

let value4: boolean = unknownValue;   // ❌ ERROR
let value5: string = unknownValue;    // ❌ ERROR
let value6: object = unknownValue;    // ❌ ERROR
let value7: any[] = unknownValue;     // ❌ ERROR
```



#### Read more:

* [typescriptlang.org \| New Unknown Type](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-0.html#new-unknown-top-type)

