---
title: "Selection Sort   Sorting Algorithms"
date: 2024-03-12T22:52:04+02:00
draft: false
---

### Selection Sort

Sorts an array by making several passes through the
array, selecting the next smallest item in the array each
time and placing it where it belongs in the array

It attempts to localize exchanges by putting the item
directly in its final place.

Efficiency is **O(n*n)**

```c
void selectionSort(vector<int> &v, int n)
{
    for (int i = 0, j, mn; i < n - 1; i++)
    {

        for (j = i + 1, mn = i; j < n; j++)
        {
            if (v[j] < v[mn])
                mn = j;
        }
        swap(v[i], v[mn]);
    }
}
```

