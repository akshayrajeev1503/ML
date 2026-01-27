## Merge two sorted lists
```python
list1 = [1,3,5,7,10,12]
list2 = [2,4,8,9]
def sortLists(list1, list2):
    i,j = 0,0
    sorted_list = []
    while i<len(list1) and j<len(list2):
        if list1[i]<list2[j]:
            sorted_list.append(list1[i])
            i+=1
        else:
            sorted_list.append(list2[j])
            j+=1
    if i<len(list1):
        sorted_list.extend(list1[i:])
    if j<len(list2):
        sorted_list.extend(list2[j:])
    return sorted_list
    
print(sortLists(list2, list1))
```
