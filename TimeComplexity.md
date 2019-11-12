## O(n^2) 

* Simple select sort:
```python
items = [1,2,3,4,5,6,7,100,8,9]
def select_sort(list, comp=lambda x,y: x<y):
    item = list
    for i in range(len(item)-1):
        min_ind = i
        for j in range(i+1, len(item)):
            if comp(item[j],item[min_ind]):
                min_ind=j
        item[i],item[min_ind]=item[min_ind],item[i]
    return item
    
```
* bubble sort 
```python
from random import shuffle
shuffle(items)
def bubbleSort(list):
    for i in range(len(list)):
        swapped = False
        for j in range(0,len(list)-i-1):
            if list[j]>list[j+1]:
                list[j],list[j+1] = list[j+1],list[j]
                swapped = True
        if swapped == False:
            break
```

## O(n*log<sub>2</sub>n)
* merge sort
* quick sort

## O(n)
* sequence search

## O(n^3)
* matrix multiply

## O(log<sub>2</sub>n)
* binary search 


