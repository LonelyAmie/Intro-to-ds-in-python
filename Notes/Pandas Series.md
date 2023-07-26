- a single dimensional data like a 2 column data 
1. Creation 
	- missing data 
		1. numbers : Nan (numerical value)
		2. other objects : None
	```python
	import panda as pd
	x = pd.series([a1, NaN, a3, ...])
	x
	```
	```python
	0 a1
	1 NaN
	2 a3
	...
	```

2. Creation + Dict 
- For assigning new values after the creation of series, we use it like a Dict()
	```python
	x = pd.series({'amir' : 19, 'aram' : 20})
	x['aram']
	x
	# For assigning new values, we use it like a Dict()
	x['mona'] = 34
	x
	```
	```python
	19 
	---
	'amir' 19
	'aram' 20
	---
	'amir' 19
	'aram' 20
	'mona' 34
	
	```
	Another way of creation and Key assigning
		
	```python
	x = pd.series([19, 20, 18], index = ['amir', 'aram', 'sara'])
	```

3. Excluding data : will be overridden and assigned to NaN|None  
	```python
	A = {'amir' : 20, 'aram' : 19}
	x = pd.series(A, index = {'amir', 'sara'})
	x
	```
	```python
	'amir' 20
	'sara' NaN
	```
4. Indexing 
	1. .iloc[num] : List indexing
	2. .loc['something'] : Dictionary key
	``` python
	x = pd.series([2, 5, 6], index = ['amir', 'aram', 'sara'])
	x.iloc[0]
	x.loc['amir']
	```
	```python
	2
	2
	```
4. Generating Big lists
	```python
	x = pd.series(np.random.randint(0, 1000, 684))
	x.head() # Shows the first 5 elements
	```
# If you find yourself iterating *ANYTIME* in pandas, you should think again
some of the features : 

6. Broadcasting :
	```python
	x = pd.series([0,3,8,9])
	x += 2
	x
	```
	```python
	2
	5
	10
	11
	```
7. .iteritem() : works like Dict.items()
	```python
	x = pd.series([0,3,8,9])
	x.iteritems()
	```
	```python
	[(0,0), (1,3), (2, 8), (3, 9)] # [(index, value)] or [(key, value)]
	```

8. Not Unique keys 
```python
B = pd.series(['art', 'math', 'biology'], 
			  index= ['aram', 'aram', 'aram'])

A = pd.series({'amir' : 'computer', 'sara' : 'sports'})
c = A.append(B)
c
print('---')
c.loc['aram']
```
- .Append() Doesn't change the first series. instead, creates a new series
```python
'amir' 'computer' 
'sara' 'sports' 
'aram' 'math'
'aram' 'art'
'aram' 'biology'
---
'aram' 'math'
'aram' 'art'
'aram' 'biology'
```

