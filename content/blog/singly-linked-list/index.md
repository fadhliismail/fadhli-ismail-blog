---
title: Singly Linked List
date: "2020-01-23T13:19:00.000Z"
description: "Singly Linked List"
---

### What is a linked list?

A linked list is a data structure that have a head, a tail, and length property. It is consists of multiple nodes which hold values, with a pointer to another node or null values. In short, a linked list is a bunch of nodes pointing to another nodes.

### Singly Linked List

In this article, I will talk about Singly Linked List, which is a one directional list. In summary, a linked list has no indexes, it's connected via nodes with a next pointer, and random access in linked list is impossible.

```
// a linked list is made up of nodes
class Node {
    constructor(value) {
        this.val = value;
        this.next =  null;
    }
}

// a class of Singly Linked List
class SinglyLinkedList {
    constructor() {
        this.head = null;   // initialize head
        this.tail = null;   // and tail to null
        this.length = 0;    // and length to 0
    }
}
```

With the above code, we will be able to initialize a Singly Linked List with nothing inside it.

### Pushing

`push()` method is use to add a node at the end of the linked list.

```
- function should accept a value
- Create a new node with the value passed to the function
- if there is no head property on the list, set the head and
tail to be the newly created node
- otherwise set the next property on the tail to be the new
node and update the tail property on the list to be the newly
created node.
- increment the length by one
- return the linked list

```

The code in JavaScript,

```
class SinglyLinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    push(value) {
        var newNode = new Node(value);  // initialize a new node with value
        if(!this.head) {                // check if the value of head exist (not null)
            this.head = newNode;        // if head has no value, set the head to newNode
            this.tail = this.head;      // and the tail to the head (newNode)
        } else {
            this.tail.next = newNode;   // if there is a head, set the newNode in addition to the end of the tail
            this.tail = newNode;        // and set that new added node as the new tail
        }
        this.length++;                  // increment length of the list by 1
        return this;                    // return the list
    }
}
```

### Popping

`pop()` is a method to remove a node from the end of the linked list. Push and pop. Get it?

```
- if there are no nodes in the list, return undefined
- loop through the list until we reach the tail
- set the next property of the 2nd to last node to be null
- set the tail to be the 2nd to last node
- decrement the length of the list by 1
- return the value of the node removed
```

In Javascript,

```
class SinglyLinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    push(value) {...}

    pop() {
        if(!this.head) return undefined;    // check if there is nodes in the list

        var current = this.head;            // set var current equal to current head
        var beforeTail = current;           // set var beforeTail equal to current (our target is the value just before the current tail)
        while(current.next) {               // while loop will continue running as long as current.next is not null
            beforeTail = current;           // this loop will get current to be reassign to current.next
            current = current.next;
        }
        this.tail = beforeTail;             // set this.tail to be the value just before the current tail, effectively take away pointer
        this.tail.next = null;              // to the old tail. Set this tail.next value to null (before this its pointing to old tail)
        this.length--;                      // decrement the length of list by 1

        // if no item left
        if(this.length === 0) {
        this.head = null;
        this.tail = null;
        }
        return current;                     // return the pop() value
    }
}

```
