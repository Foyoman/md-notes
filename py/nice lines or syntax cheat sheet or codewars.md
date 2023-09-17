```python
file = open("sums.txt", "r")

for line in file:
    print(sum(list(map(int, line.split()))))
```

```python
def filter_type(array):
	def check_type(value):
		return isinstance(value, str) # str, int, etc
		
	return list(filter(check_type, array))
```

```python
for _ in array:
	pass
```

```python
def number(lines):
	"""maps an array with index plus one prefixed to each value"""	
	return [f"{i + 1}: {x}" for i, x in enumerate(lines)]
```

```python
def stray(arr):
	"""returns the odd value out in an array of same values besides one"""
	for val in arr:
		if arr.count(val) == 1:
			return val
```

```python
lambda val : int(val)
```

```python
int_nums = [int(val) for val in split_ip]
```

```python
all(condition) and any(condition)
```

```python
def remove_url_anchor(url):
	return url.split('#')[0]
```

```python
def is_prime(num):
    return all(num % i != 0 for i in range(2, num))
```