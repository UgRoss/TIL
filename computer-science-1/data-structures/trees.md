# Trees

> A tree data structure is defined as a collection of nodes (starting at the root node), where each node is a data structure consisting of a value and a list of references to nodes (the “children”), with the constraints that there are no duplicate references, and no references point to the root. These references are often referred to as edges. (Trekhleb & Shoemaker, 2019)

As opposed to Linked Lists, which are linear, Trees can have 0 or more child nodes.

#### What is a node?

> A node is a basic unit used in computer science. Nodes are individual parts of a larger data structure, such as linked lists and tree data structures. Nodes contain data and also may link to other nodes. Links between nodes are often implemented by pointers. -Wikipedia24

In tree data structure one node can link to many others, which means that trees can grow in different shapes and ways. 

## Trees components

![](../../.gitbook/assets/IMG\_0141.jpeg)

* _**root node**_ - the topmost node.
* _**edge**_ or _**link **_- it's a connection between nodes. Parent node contains references to its child nodes.
* _**child**_ - any node that has a parent node.
* _**parent - **_any node that has a reference/link to another node.
* _**sibling nodes**_ - any group of nodes that are children of the same node.
* _**leaf**_ - any node that doesn't have any children in the tree.



_References:_

* Trekhleb, O., & Shoemaker, S. (2019). JavaScript Algorithms. Retrieved January 13, 2021, from [https://www.newline.co/javascript-algorithms](https://www.newline.co/javascript-algorithms)
