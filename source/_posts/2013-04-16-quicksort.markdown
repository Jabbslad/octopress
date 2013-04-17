---
layout: post
title: "An Explanation of QuickSort in Java"
date: 2013-04-16 23:09
comments: true
categories: java quicksort algorithm
---

# Introduction

I will be kicking off my review of data structures and algorithms with a look at the QuickSort algorithm. QuickSort falls under the category of a [divide and conquer](http://en.wikipedia.org/wiki/Divide_and_conquer_algorithm) algorithm whereby a problem is repeatedly divided into sub-problems before being combined to return the solution. 

<!-- more -->

There are two key parts to the algorithm; A *partition* and a *sort*.

## 1. The Partition

The aim of the partition is to select a _pivot_ value within the middle of the array (1) and then enter a loop (2) where all values smaller than the pivot are swapped to the left hand side of the array and all values greater than the pivot are swapped to the right hand side (3).

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


