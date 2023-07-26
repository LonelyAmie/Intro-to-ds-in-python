
here's a cool thing : 
``` python
map(func, iterable_1, iterable_2, ... )
 #  it applies the func to items of each iterable in parallel. there's no limits for giving inputs
```
Example : 
``` python

numbers1 = [1, 2, 3]
numbers2 = [4, 5, 6, 7]
sums = map(add, numbers1, numbers2)
list(sums)
```
output : 
``` python
[5, 7, 9]

```