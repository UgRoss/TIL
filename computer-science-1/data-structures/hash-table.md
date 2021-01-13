---
description: WIP
---

# \[WIP\] Hash Table

##  🚧 WORK IN PROGRESS

## Description

A hash table is a data structure that stores data in the form of key-value pairs. This means that inside a hash table each key is mapped to a value. For example, names of your friends can be used as unique identifiers \(keys\) of their numbers \(values\) inside a phone book \(hash table\).

```typescript
phoneBook.set('John Doe', '111-222-333');

phoneBook.set('Alberto Anderson', '111-333-444');
```

// image

A hash table is an array of slots/buckets. “A hash table stores its data using a computed index, the result of which is always an integer. The computation of this index is called a hash function and it uses the value you want to store to derive the key”

### Base Operations

| Operation | Description |
| :--- | :--- |
| _`set(key, value)`_ | add an element to a hash table based on key and value. |
| _`get(key)`_ | get a value by its key. |
| _`delete(key)`_ | delete value by its key. |

### When to use

Hash tables are one of the most common data structures just because they are fast. However, everything depends on the hashing algorithm, it can make a hash table slow.   
And because you are in an interview 🙂

### Time Complexity

| Operation | Average Complexity | Worst Complexity |
| :--- | :--- | :--- |
| Insertion | _O\(1\)_ | O\(n\) |
| Deletion | _O\(1\)_ | O\(n\) |
| Search | O\(1\) | O\(n\) |

## Code

```typescript
import { LinkedList } from '../LinkedList/LinkedList';

export class HashTable<T> {
  // Allowed buckets number. The bigger the bucket number the fewer collisions we will get.
  private static readonly defaultBucketsNumber = 30;
  // hash table that will store buckets with linked list.
  private readonly buckets: LinkedList<{ key: string; value: T }>[];

  constructor(bucketsNumber = HashTable.defaultBucketsNumber) {
    // Create hash table of certain size and fill each bucket with empty linked list.
    this.buckets = Array(bucketsNumber)
      .fill(null)
      .map(() => new LinkedList());
  }

  /** Add or Update the value by its key */
  public set(key: string, value: T) {
    const bucketLinkedList = this.getBucketLinkedList(key);
    const node = bucketLinkedList.find((item) => Object.is(item.key, key));

    if (!node) {
      bucketLinkedList.append({ key, value }); // Add new node
    } else {
      node.value.value = value; // Update value of already existing node
    }
  }

  /** Get the value by its key */
  public get(key: string): T | null {
    const bucketLinkedList = this.getBucketLinkedList(key);
    const node = bucketLinkedList.find((item) => Object.is(item.key, key));

    return node?.value.value || null;
  }

  /** Delete the value by its key */
  public delete(key: string): T | null {
    const bucketLinkedList = this.getBucketLinkedList(key);
    const node = bucketLinkedList.find((item) => Object.is(item.key, key));
    const deletedNode = bucketLinkedList.delete(node?.value);

    return deletedNode?.value.value || null;
  }

  /** Returns bucket linked list based on key */
  private getBucketLinkedList(key: string): LinkedList<{ key: string; value: T }> {
    const keyHash = this.hash(key);
    return this.buckets[keyHash];
  }

  /** Converts key string to hash number */
  private hash(key: string): number {
    // Simple hash function that calculates sum of all characters codes inside the key
    // You may want to use better hashing function to reduce the number of collisions
    const hashCode = Array.from(key).reduce(
      (hashAcc, keySymbol) => hashAcc + keySymbol.charCodeAt(0),
      0
    );

    // Reduce hash code number to fit inside available buckets number
    // Example: 37 % 30 = 3; 79 % 30 = 19
    return hashCode % this.buckets.length;
  }
}
```

#### Links:

* [Linked List record](linked-list.md).
* Code on [Github](https://github.com/UgRoss/data-structures-typescript/tree/main/src/data-structures/HashTable).
* Solve problems using Stack on [LeetCode](https://leetcode.com/tag/hash-table/).
* [Big-O Cheat Sheet](https://www.bigocheatsheet.com/).

