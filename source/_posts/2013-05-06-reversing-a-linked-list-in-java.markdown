---
layout: post
title: "Reversing a Linked List in Java"
date: 2013-05-06 23:08
comments: true
categories: java interview algorithm
---

A question on how to reverse a singly linked list popped up in a recent interview question. I stumbled through the question at the time but wanted to revisit my solution and refine it somewhat.

<!-- more -->

# The Node Class

``` java
public class Node<T> {
	public T item;
	public Node next;
}
```
# Iterative Approach

``` java
public static <T> Node reverse(Node<T> head) {
    Node curr = head;
    head = null;
    while(curr != null) {
        Node newHead = curr;
        curr = curr.next;
        newHead.next = head;
        head = newHead;
    }
    return head;
}
```

# Recursive Approach

``` java
public static <T> Node reverse(Node<T> head) {
    if(head == null) {
        return null;
    }

    if(head.next == null) {
        return head;
    }

    Node rest = reverse(head.next);
    head.next.next = head;
    head.next = null; // remove circular reference

    return rest;
}
```


