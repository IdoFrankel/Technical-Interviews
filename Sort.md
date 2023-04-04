# Sort

## Quicksort

> Complexity:
> - worst-case: O(n^2)
> - average & best: O(nlogn)

> algorithm:
> 1. randomly select pivot
> 2. sort, such every element bigger than pivot are on the right of the pivot
> 3. recursivly, preform the algorithm on the right and left parts of the array.
> 4. stopping creteria: when the array is 1-length


```
def quicksort(arr, left, right):
    if left < right: # stopping point
        index = partition(arr, left, right)
        quicksort(arr, left, index-1)
        quicksort(arr, index+1, right)
        
def partition(arr, left, right):
    x = arr[right]
    i = left - 1
    j = left
    while j <= right-1:
        if arr[j] <= x:
            i += 1
            exchange(arr, i, j)
        j += 1
    exchange(arr, i+1, right)
    return i+1

def exchange(arr, i, j):
    arr[i], arr[j] = arr[j], arr[i]
```

## mergesort

Divide and Conquer
> 1. if len(array) <= 1: return array
> 2. left, right = 0, len(array)
> 3. mid = (left + right)/2
> 4. mergresort(array, left, mid)
> 5. mergresort(array, mid+1, right)
> 6. mergre(array, left, mid,right)


```
def mergresort(arr):
    if len(arr) <= 1:
        return
    
    mid = len(arr)//2
    L, R = arr[:mid], arr[mid:]
    mergeSort(L), mergresort(R)

    i = j = k = 0
    while i < len(L) and j < len(R):
        if L[i] <= R[j]:
            arr[k] = L[i]
            i+=1
        else:
            arr[k] = R[j]
            j +=1
        k+=1
    while i< len(L):
        arr[k] = L[i]
        i +=1
        k+=1
    while j < len(R):
        arr[k] = R[j]
        j+=1
        k+=1

```

## Python sort (TimSort)
> 1. First using insertionSort on blocks of length `minRun` (tipically of power of 2)
> 2. Than use mergesort on those mergedruns.