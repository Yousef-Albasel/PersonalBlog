---
title: "Insertion Sort   Sorting Algorithms"
date: 2024-03-12T22:51:54+02:00
draft: false
---

### Insertion Sort

Maximum number of comparisons is **O(n &sup2;)**

In the best case, number of comparisons is **O(n)**

The number of shifts performed during an insertion is
one less than the number of comparisons or, when the
new value is the smallest so far, the same as the number
of comparisons


```c
void insertionSort(vector<int> &v, int n)
{
  for (int i = 1, j; i < n; i++)
  {
    int temp = v[i];
    for (j = i; j > 0 && temp < v[j - 1]; j--)
    {
      v[j] = v[j - 1];
    }
    v[j] = temp;
  }
}
```
