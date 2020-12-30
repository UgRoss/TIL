---
description: >-
  ℹ️ They are similar in many ways. The key differences are: type can be used
  for primitives and type can be used for union of other types/interfaces.
---

# Interface vs Type alias

Mostly, type alias is used to represent a more complex type like the union of a few different types:

```typescript
type Figure = IRectangle | ICircle;
```

Interfaces are used to represent the shape of an object \(for example, to create classes or to use in function parameters\):

{% code title="Person.js" %}
```typescript
interface IPerson {
  name: string;
  age: number;
  sayHi(): void;
}

// Example:
class Person implements IPerson {
  constructor(public name, public age) {}

  public sayHi() {
    console.log('Hello!');
  }
}
```
{% endcode %}

Type aliases and interfaces are similar in many ways, except syntax. Nevertheless, they have differences that you need to know.

### Similarities

An object can be represented using both interface and type:

```typescript
interface IPlayer {
  name: string;
  age: number;
  jump(): void;
}

type PlayerType = {
  name: string;
  age: number;
  jump(): void;
};

// We can assign variable with the `IPlayer` interface
// to variable with `PlayerType`, or vice versa.
let player: IPlayer;
let playerType: PlayerType;

player = playerType;
```

Interfaces can create the same structure as type aliases, except [types union](https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types) and primitives:

```typescript
type Jump = () => void;
type PlayersIDs = string[];

// 🔽 Equivalent using interfaces
interface IJump {
  (food: string): void;
}

interface IPlayersIDs {
}
```

It's also possible to merge interfaces or types:

```typescript
type IMerged = IFirst & ISecond;
// or
interface IMerged extends IFirst, ISecond {}
```

### Differences

#### Primitive types

It's possible to describe primitive only with the type alias:

```typescript
type Name = string;
```

As mentioned above, type alias can be used to describe the union:

#### Type Alias union

```typescript
interface ICircle {}
interface ISquare {}

type ShapeType = ICircle | ISquare;
```

_ℹ️ Note:_ a type alias with [union](https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types) can't be used inside interface or class anymore, what is logic, as class or interface can only represent a **specific structure**, not one or another.

#### Mapped Types

With type alias it's possible to create [mapped types](https://www.typescriptlang.org/docs/handbook/advanced-types.html#mapped-types):

```typescript
type Keys = 'name' | 'breed';

type Flags = { [K in Keys]: boolean };
```

#### Declaration Merging is possible only with interfaces

You can define the same interface multiple times, and their definitions will be merged into one:

```typescript
interface Dog {
  name: string;
  breed: string;
}

// ....

interface Dog {
  age: number;
}

let oscar: Dog = { age: 5, breed: 'pug', name: 'Oscar' }; // --> ✅ valid
console.log(oscar.breed, oscar.age);
```

### Read More

* [Interface vs. Type Alias](https://www.typescriptlang.org/docs/handbook/advanced-types.html#interfaces-vs-type-aliases)
* [Union Types](https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types)
* [Mapped Types](https://www.typescriptlang.org/docs/handbook/advanced-types.html#mapped-types)

