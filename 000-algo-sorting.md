[TOC]

## Sorting Algorithms

### Selection Sort

Find the minimum value in each iteration and swap it to the subarray that is sorted.

* Time: $O(n^2)$
* Space: $O(1)$

### Bubble Sort

Compare each element with its adjacent one and swap them if necessary, like bubbling the large values up to the rear part of the array.

* Time: $O(n^2)$
* Space: $O(1)$

If sorting in an asending way, and iterations start from the index 0, after i interation, which part of the array is sorted?

```java
// iteration can be written in this way
for (int i = 0; i < nums.length - 1; i++) {
    for (int j = i; j < nums.length - i - 1; j++) {
        if (nums[i] > nums[i + 1]) {
            // swap the adjacent element.
        }
    }
}
```

This can also be implemented in a recursive way.

### Insertion Sort

Iterate through the array and find the right place to insert the element. The search part can be done using Binary Search.

* Time: $O(n^2)$ -- although the search part can be done in $O(logn)$ in each iteration, it would still take $O(n)$ to do swapping.
* Space: $O(1)$ can be done in place

This can also be done in a recursive way.

### Merge Sort

关键在于 implement `merge` 算法。

Note that if it's an array, a buffer is needed. In-place merge is possible but will deteriorate the time complexity.

* Time: $O(nlogn)$
* Space: $O(n)$

```java
static void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = (l+r)/2;
        mergeSort(arr, l, m);
        mergeSort(arr , m+1, r);
        merge(arr, l, m, r);
    }
}
```

### Quick Sort

Also a Divide and Conquer algorithm. Pick a pivot and partition the array around the pivot by putting the smaller ones in the front and larger ones in the back.

- Time: $O(nlogn)$
- Space: $O(n)$

