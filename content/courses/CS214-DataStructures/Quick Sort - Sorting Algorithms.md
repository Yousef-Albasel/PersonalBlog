
---
title: "Quick Sort   Sorting Algorithms"
date: 2024-03-18T17:26:40+02:00
draft: false
---

## Quick Sort Algoirthm
------

#### First Implementation

```c
void quickSort(int arr[], int start, int end)
{
    if (start <= end)
    {
        int pivot = partition(arr, start, end);
        quickSort(arr, start, pivot - 1);
        quickSort(arr, pivot + 1, end);
    }
}

int partition(int a[], int start, int end)
{
  int i = start;
  int j = end;
  int pivot = a[i];
  while (i < j){
    
    do {
      i++;
    } while(a[i] <= pivot); 
    do {
      j--;
    } while (a[j]> pivot);

    if (i<j)
      swap(a[i],a[j]);
  }
  swap(a[start],a[j]);
  return j;
}
```

#### Second Implementation

```c
int partition(int a[], int start, int end)
{
  int i = start;
  int pivot = a[i];

  for(int j = start + 1; j < end; j++){
    if (a[j] < pivot){
      i++;
      swap(a[i],a[j]);
    }
  }

  swap(a[i],a[start]);
  return i;
}
```

