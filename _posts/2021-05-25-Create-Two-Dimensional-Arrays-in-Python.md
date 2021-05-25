> Without corrupting the data unintentionally 

I created a 2D array in Python.
```py
dp = [[0] * 5] * 3
>>> 
[[0, 0, 0, 0, 0], 
[0, 0, 0, 0, 0], 
[0, 0, 0, 0, 0]]
```
To modify the [2][3] element,
```py
dp[2][3] = 5
>>>
[[0, 0, 0, 5, 0], 
[0, 0, 0, 5, 0], 
[0, 0, 0, 5, 0]]
```
As you can see from the above output, all the fourth elements of the inner lists were modified.

This is not what I wanted.

Reading this [stack**overflow**](https://stackoverflow.com/questions/21036140/python-two-dimensional-array-changing-an-element) post, I realized *"the middle items are all referring to the same list, so updating one causes the change to be reflected in the others"*. That's a side effect of the way how I constructed the list.

To avoid this issue, the *correct* way to follow is:
```py
dp = [[0] * 5 for _ in range(3)]
>>>
[[0, 0, 0, 0, 0], 
[0, 0, 0, 0, 0], 
[0, 0, 0, 0, 0]]
```
Now,
```py
dp[2][3] = 5
>>>
[[0, 0, 0, 0, 0], 
[0, 0, 0, 0, 0], 
[0, 0, 0, 5, 0]]
```