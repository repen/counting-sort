### Counting Sort. Example Python
In computer science, counting sort is an algorithm 
for sorting a collection of objects according to keys
that are small integers; that is, it is an integer 
sorting algorithm. 

```
from functools import reduce

class ErrorLimitedlength(Exception):
    pass

def sort_counting(array):
    if max(array) > 1000:
        raise ErrorLimitedlength("Error! not effectively")
    containers = [[] for _ in range(max(array))]
    # [[], [], [], [], [], [], [], [], [], [], [], [], [], [], [], []]
    
    for arr in array:
        containers[arr-1] += [arr]
    #[[1, 1], [2, 2], [3], [4], [], [6], [], [], [9], [], [], [], [13], [], [15, 15], [16]]
    
    array = reduce(lambda x, y: x + y, containers)
    return array

res = sort_counting([16,9,2,15,15,2,4,6,1,1,3,13])
print(res) #[1, 1, 2, 2, 3, 4, 6, 9, 13, 15, 15, 16]
```
