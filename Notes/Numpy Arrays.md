# Array Creation 
## Given arguments : 
- a list
- a list of lists
``` python
a = np.array([[1, 3, 5], [3 , 9, 6]])
b = np.array([2, 3, 5])

# number of dimensions : 
a.ndim # output is 2
b.ndim # output is 1
``` 
__disclaimer__ : 
```python
# the columns (length of each list) must be the same
a = np.array([[1, 3, 5], [3 , 9, 6, 8]]) # Error raised
```
---
## Shape of a array  : (x, y)
*x refers to ==Rows== and y refers to ==columns==*
```python
a.shape # output : (2,3)
b.shape # output : (1, 3)
```

## Type of a array 
```python
a.dtype # int64
```
## Creating with placeholder (0 or 1 or k)
```python
a = np.zeros((2, 3)) # 2 row and 3 columns
b = np.ones((1, 4)) # 1 row and 4 columns
c = np.full((3, 4), k)
```
## Random generation 
```python
a = np.random.rand(2, 3) #shape of (2, 3)
```
## Changing the type of an array
``` python
modified = a.astype(np.unit8)
```
# Creating within a range 
- Integers 
	```python
	np.arange(2, 35, 3) #Start : 2, End(exclusive) : 35, Step : 3
	```
- Floats 
	 ```python
	 np.linspace(2, 35, 10) # start : 2, End(inclusive) : 35
	                        # array len : 10
	```

---
# Operations 
- *every operations is ==elementwise==*
## conditions 
- returns an array of Booleans 
```python 
a = np.array([10,20, -30])
a > 0 
```
output : 
```python
array([True, True, False])
```

## Matrix product 
with the ==@== symbol 
- the matrix product condition must be met
```python
a = np.array ([[1,3], [6, 8], [9, 15]]) # (2, 3)
b = np.array([[1], [4], [5]]) # (3, 1)
product = a @ b # (2, 1)
```

## Creating and reshaping 
- used for ==stretching== images and etc.
``` python
a = np.arang(1, 16, 1).reshape(3, 5)
b = np.linspace(1,16, 15).reshape (5, 3)
```

## Indexing 
- just like python, in numpy, everything starts at 0
``` python
a = np.array([2,3], [7,6], [6,15] )
a[1, 0] # 7

# selecting multiple items 
a[[2, 2, 0], [1, 0, 1]] # [15, 6, 3]
# first list : Rows, Second list : Columns
```
- [x] Negative Indexing

## Boolean indexing
```python
a = np.array([3, 4], [5, 9], [6, 7])
a[a > 5] --> [9, 6, 7] #one-dimensional
```

## Slicing
1. Consecutive 
	- one dimensional : like lists
	```python
	a[2:5] # from 2 (inclusive) to 5 (exclusive)
	```  
	-  multi-dimensional : selecting Rows and Columns
	```python
	a[2:6, 3:7] # -> Rows : [2,6)   Columns : [3,7) 
	```
	- Tip 
```python
		# All rows, first column
		a[:, 0] -> [a1, a2, a3, ...]
		a[:, 0:1] -> [[a1],
					  [a2],
					  [a3,
					  .
					  .
					  .
					]
```

2. Non-Consecutive : selecting each row and column separately 
```python
# all rows, (1st, 2nd, 6th) column
a[: , [2, 3, 7]]
# (1st, 3rd, 5th) row, (1st, 2nd, 6th) column 
a[[2, 4, 6], [2, 3, 7]]
```
---
## Loading a DataSet 
```python
students = np.genfromtxt(file_name, delimiter=',' , skip_headers= 1, 
dtype = None ,names=
('seria','gre','tofel','rating','sop','lor','cgpa','research','chance')
			            )
```
- delimiter (__OPTIONAL__) : usually ==,== (working with csv)
- skip headers (__OPTIONAL__) : number of headers to skip
- names (__OPTIONAL__) : name of each column 
	- Acts like ==dictionary keys==
- (dtype = None) => Numpy infers the data type itself

```python
file['name'][3:10]
```
meaning : All data for "name" column in rows [3-10)

```python
file[file['grade'] > 15]['name']
```
meaning : All data in "name" column where grade > 15
