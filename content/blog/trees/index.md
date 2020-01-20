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

Currently, the code above can only initialize a tree, and then set a root node for the tree. It's so simple and does not have any significant use. However, this is a very good introduction to tree data structures. I will later on continue about methods for Binary Search Tree.

<!-- ### Inserting -->
