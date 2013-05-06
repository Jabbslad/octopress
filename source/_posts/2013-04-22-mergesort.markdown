---
layout: post
title: "mergesort"
date: 2013-04-22 21:59
comments: true
categories: mergesort java algorithm
published: false
---

# Introduction

Next in my review of algorithms is the MergeSort algorithm. MergeSort falls under the category of a [divide and conquer](http://en.wikipedia.org/wiki/Divide_and_conquer_algorithm) algorithm whereby a problem is repeatedly divided into sub-problems before being combined to return the solution. 

<!-- more -->

There are two key parts to the algorithm; The *divide* and the *merge*.

## 1. The Divide

The aim of the divide function is to recursively divide the unsorted list into sublists until there 

``` java
public int partition(int[] array, int low, int high) {
    int pivot = array[(low + high) / 2];  // (1)

    while(low < high) { // (2)
        while(array[low] < pivot) {
            low++;
        }
        while(pivot < array[high]) {
            high--;
        }
        if(low <= high) {
            swap(array, low, high); // (3)
            low++;
            high--;
        }
    }
    return low;
}

public void swap(int[] array, int low, int high) {
    int temp = array[low];
    array[low] = array[high];
    array[high] = temp;
}
```

## 2. The Recursive Sort

The recursive quickSort function gets the index of the partition (1) and then recusively calls itself on values to the left and right of the pivot (2 & 3)

``` java
public void quickSort(int[] array, int low, int high) {
    int index = partition(array, low, high); // (1)
    if(low < index - 1) {
        quickSort(array, low, index - 1); // (2)
    }
    if(index < high) {
        quickSort(array, index, high); // (3)
    }
}
```

# Performance

_To Be Completed: Explanation required_

## Worst Case
O(n^2)

## Average Case
O(n log n)
