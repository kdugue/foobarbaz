---
layout: post
title: "Singly Linked List Implementation in JavaScript"
date: 2018-10-04 19:13:46 -0400
categories: jekyll update
---

A linked list is a type of data structure that is composed of nodes that hold references that point
to the next and/or previous node. Each node itself contains some value, along with a
pointer to the next node. Each time a node is added to the linked list, each node is
responsible for remembering the next element.

Though there are various types of linked lists, however, this post will cover the implementation of
a singly linked list in JavaScript. This type of linked list is unidirectional - each node has a pointer only to the next node.

The main methods for singly linked list are:

- Append: adding elements to the linked list
- Remove: removing elements from the linked list
- Search: finds, if possible, the element of the list

To start, we will create the Linked List class and Node helper class:

The Linked List class is defined with a length of 0 and head initially set to null.
When a node is created, it will be created through the Node class, and contain a value,
in addition to a next and previous property, which is initially set to null

```
class LinkedList {
  constructor() {
    this.length = 0;
    this.head = null;
  }

  append() {}
  remove() {}
  search() {}
}

class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.previous = null;
  }
}
```

Next, we will define each of our methods within the Linked List class.

Append method: The append method is responsible for adding elements to the linkedlist. The method takes in a value, which is the value of the node. We need to make sure that the linked list is not empty, so we’ll check to see if there exists a value for the head. If there is a value, we will enter a loop, which will run only during the condition of that the node which is being pointed to contains a value. While in the loop, we will set the head’s value to it’s pointed node’s value, in order to continue to move through the list. Once there exists no value for the head’s next value, we will set the node’s pointed node value to to the current head.

```
append(value) {
  const node = new Node(value);

  if(!this.head) {
    //case for an empty linked list
    this.head = node;
    this.tail = node;
  }

  while(this.head.next) {
    this.head = this.head.next;
  }

  node.next = this.head;
  this.head.previous = node;
  this.head = node;
}
```

Remove method: The remove method removes a node from the linkedlist. We initially check the starting Node’s next value to see if it exists. If it doesn’t, we set the starting node’s next value to the head. The remove method returns the node that.

```
remove(nodeToRemove) {
  let startingNode = this.head;
  let previousNode = null;

  if(startingNode.next === null) {
    this.head = startingNode.next;
    return this.head;
  }

  while (startingNode.next) {
    previousNode.next = startingNode.next;
    startingNode = null;
  }

  previousNode.next = startingNode.next;
  startingNode = null;
  return this.head;
}
```

Search method: The search method looks for a given value and returns that value if the node exists in the list. If the node doesn’t exist in the list, a false boolean value.

```
search(value) {
  let currentNode = this.head;

  while(currentNode) {
    if(typeof value === "string") && currentNode.value === value) {
      return value;
    } else if(typeof val === "function" && val(currentNode.value)) {
      return currentNode.value;
    }

    //update pointer to the next node
    currentNode = currentNode.next;
  }
}
```
