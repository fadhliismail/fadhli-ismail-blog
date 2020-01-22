---
title: Binary Search Tree
date: "2020-01-20T20:43:00.000Z"
description: "Binary Search Tree"
---

### What is a tree?

Tree is a data structure that consist of nodes in a parent and child relationship. It is a non linear data structure made up of root, parent, child, siblings, leaf, and edge.

There are many applications of tree all around us. We can see it in HTML DOM, network routing, computer file systems, artificial intelligence, etc.

In this post, I will talk about Binary Search Tree.

### Binary Search Tree

How it works?

A binary search tree is consist of a root node. This root node is also the first parent node of many. Every parent node has at most two children. Children node to the right usually has a value greater than the parent while children node to the left has a value less than the parent.

Let's take a look at the basic code for Binary Search Tree.

```
class Node {
    constructor(value) {
        this.value = value;
        this.right = null;
        this.left = null;
    }
}

class BinarySearchTree {
    constructor() {
        this.root = null;
    }
}

var tree = new BinarySearchTree();
tree.root = new Node(10);

```

Currently, the code above can only initialize a tree, and then set a root node for the tree. It's so simple and a very good introduction to tree data structures. We will later on continue on to methods for Binary Search Tree.

---

`Continue on Wednesday 22 January 2020, 21:34`

### Inserting

What is the point of having a binary tree if you cannot use it. Inserting into a binary tree is quite simple. We can do it either iteratively or recursively. I prefer an iterative solution as it is easier to understand.

Here are the steps:

```
- Create a new node with the value that we want to insert into
the tree.
- Check if there is a root. If not, assign the new node as the
root node.
- Initialize a current variable and store this.root in it.
- All the code after this have to be in a loop (while loop)
    - Check if the value has been inserted. A binary search tree
    does not need multiple copy of the same value.
    - If there is a root, check if the value of the new node is
    greater than or less than the value of the root.
        - If the value is greater,
            - Check to see if there is value to the right.
            - If there is, move to that node and repeat these steps.
            - Otherwise, add that node as the right property.
        - If the value is less,
            - Check to see if there is a value to the left.
            - If there is, move to that node and repeat these steps.
            - Otherwise, add that node as the left property.
```

Pretty easy right? These are the steps that we need to code to insert values into the Binary Search Tree.

Following are the code for `insert()`.

```
class BinarySearchTree {
    constructor() {
        this.root = null;
    }

    insert(value) {
        var newNode = new Node(value);
        if(!this.root) {
            this.root = newNode;
            return this;
        }

        var current = this.root;
        while(true) {
            if (value === current.value) return undefined;
            if (value < current.value) {
                if(!current.left) {
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(!current.right) {
                    current.right = newNode;
                    return this;
                }
                current = current.right;
            }
        }
    }
}
```

### Finding

Following are the steps to search for a value in a Binary Search Tree:

```
- Check if there is a root, if not we are done searching
- If there is a root, check if the value of the new node is the value we are looking for. If we found it, we are done.
- if not, check to see if the value is greater or less than the value of the root
- if greater
  - check to see if there is a node to the right
    - if there is, move to that node and repeat these steps
    - if not, we are done
- if less
  - check to see if there is a node to the left
    - if there is, move to that node and repeat
    - if not, we are done
```

These are the steps that we need to code to find values into the Binary Search Tree.

Following are the code for `find()`.

```
class BinarySearchTree {
    constructor() {
        this.root = null;
    }

    insert(value) {...}

    find(value) {
        if(!this.root) {
            return undefined;
        }

        var current = this.root;
        while(true) {
            if(value === current.value) return this;

            if(value > current.value) {
                if(current.right) {
                    current = current.right;
                } else {
                    return "Cannot find value";
                }
            } else {
                if(current.left) {
                    current = current.left;
                } else {
                    return "Cannot find value";
                }
            }
        }
    }
}
```

These two are some of the basics method that's usually included together with Binary Search Tree.
