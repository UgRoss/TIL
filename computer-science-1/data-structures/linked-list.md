# Linked List

## Description

**Please check my blog post on **[**ugross.dev**](https://ugross.dev/blog/data-structures-linked-list)

## Code

{% tabs %}
{% tab title="Singly Linked List" %}
{% code title="SinglyLinkedList.js" %}
```javascript
class Node {
  /**
   * @param {number} value of the Node
   * @param {(Node | null)} next - reference to the next Node
   */
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

export default class LinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  /**
   * Creates new node and inserts at the start of the list
   *
   * @param {number} value
   * @return {LinkedList}
   */
  prepend(value) {
    // Create new node with the next reference as the head
    const newNode = new Node(value, this.head);

    // Update our head to contain new element
    this.head = newNode;

    // If there is no tail update it too
    if (!this.tail) {
      this.tail = newNode;
    }

    return this;
  }

  /**
   * Creates new node and inserts in the end of the list
   *
   * @param {number} value
   * @return {LinkedList}
   */
  append(value) {
    const newNode = new Node(value);

    if (this.head == null) {
      this.head = newNode;
      this.tail = newNode;

      return this;
    }

    this.tail.next = newNode;
    this.tail = newNode;

    return this;
  }

  /**
   * Finds element inside the linked list
   *
   * @param {number} value
   * @return {(Node | null)}
   */
  find(value) {
    if (!this.head) {
      return null;
    }

    let currentNode = this.head;
    while (currentNode) {
      if (currentNode.value === value) {
        return currentNode;
      }
      currentNode = currentNode.next;
    }

    return null;
  }

  /**
   * Removes Node from the list by its value
   *
   * @param {number} value to remove
   * @return {Node | null} remove node or null
   */
  delete(value) {
    if (this.head === null) {
      return null;
    }

    let deletedNode = null; // Keep deleted Node to return it

    if (this.head.value === value) {
      deletedNode = this.head;
      // Now make next node to be a new head
      this.head = this.head.next;
    }

    let currentNode = this.head;
    if (currentNode !== null && deletedNode === null) {
      while (currentNode.next !== null) {
        if (currentNode.next.value === value) {
          deletedNode = currentNode.next;
          currentNode.next = currentNode.next.next;
        } else {
          currentNode = currentNode.next;
        }
      }
    }

    // Check if tail contains Node with the value we are looking for
    if (this.tail.value === value) {
      this.tail = currentNode;
    }

    return deletedNode;
  }

  /**
   * Converts linked list to array
   *
   * @return {Node[]}
   */
  toArray() {
    const nodes = [];

    let currentNode = this.head;
    while (currentNode) {
      nodes.push(currentNode);
      currentNode = currentNode.next;
    }

    return nodes;
  }

  /**
   * Converts linked link to string representation
   *
   * @return {string}
   */
  toString() {
    return this.toArray()
      .map(node => node.value)
      .toString();
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Doubly Linked List" %}
{% code title="DoublyLinkedList.js" %}
```javascript
class Node {
  /**
   * @param {number} value of the Node
   * @param {(Node | null)} next - reference to the next Node
   * @param {(Node | null)} previous - reference to the previous Node
   */
  constructor(value, next = null, previous = null) {
    this.value = value;
    this.next = next;
    this.previous = previous;
  }
}

export default class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  /**
   * Creates new node and inserts at the start of the list
   *
   * @param {number} value
   * @return {DoublyLinkedList}
   */
  prepend(value) {
    const newNode = new Node(value, this.head);

    // if there is head, then update it's previous reference as it won't be head anymore
    if (this.head) {
      this.head.previous = newNode;
    }
    this.head = newNode;

    // If there is no tail create it
    if (!this.tail) {
      this.tail = newNode;
    }

    return this;
  }

  /**
   * @param {*} value
   * @return {DoublyLinkedList}
   */
  append(value) {
    const newNode = new Node(value);

    // If there is no head create it
    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;

      return this;
    }

    // Add new node to the tail
    this.tail.next = newNode;
    // Update new Node's previous reference
    newNode.previous = this.tail;
    // Set new node to be the tail of the list.
    this.tail = newNode;

    return this;
  }

  /**
   * Finds Node inside the linked list by its value
   *
   * @param {number} value to find
   * @return {(Node | null)}
   */
  find(value) {
    if (!this.head) {
      return null;
    }

    let currentNode = this.head;
    while (currentNode) {
      if (currentNode.value === value) {
        return currentNode;
      }

      currentNode = currentNode.next;
    }

    return null;
  }

  /**
   * Removes Node from the list
   *
   * @param {number} value
   * @return {(Node | null)}
   */
  delete(value) {
    if (!this.head) {
      return null;
    }

    let deletedNode = null; // Save deleted node to return it in the end

    let currentNode = this.head;
    while (currentNode) {
      if (currentNode.value === value) {
        deletedNode = currentNode;

        if (deletedNode === this.head) {
          // 🔗 Node that we need to remove is in the head
          this.head = deletedNode.next;

          if (this.head) {
            this.head.previous = null; // update new head previous reference
          }

          if (deletedNode === this.tail) {
            // Our node is in the head and tail, so we can simply remove the tail
            this.tail = null;
          }
        } else if (deletedNode === this.tail) {
          // 🔗 Node that we need to delete is in the tail
          this.tail = deletedNode.previous;
          this.tail.next = null;
        } else {
          // 🔗 Node that we need to delete is the middle Node
          const previousNode = deletedNode.previous;
          const nextNode = deletedNode.next;

          previousNode.next = nextNode;
          nextNode.previous = previousNode;
        }
      }

      currentNode = currentNode.next;
    }

    return deletedNode;
  }

  /**
   * Converts linked list to array
   *
   * @return {Node[]}
   */
  toArray() {
    const nodes = [];

    let currentNode = this.head;
    while (currentNode) {
      nodes.push(currentNode);
      currentNode = currentNode.next;
    }

    return nodes;
  }

  /**
   * Converts linked link to string representation
   *
   * @return {string}
   */
  toString() {
    return this.toArray()
      .map(node => node.value)
      .toString();
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

