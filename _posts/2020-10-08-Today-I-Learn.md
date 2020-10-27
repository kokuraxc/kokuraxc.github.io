> Collection of bits of TILs

---
# Python

#### _2020.10.08_ **Genearte package list's `requirements.txt` file**

Before copying the Python program from dev computer to other computers, extract all the required packages with the command:

* Usage: `pipreqs [options] <path>`
* Example: `pipreqs C:\Users\zj\Desktop\py_program`

This will generate a `requirements.txt` file with all the package names and versions.

In other computers, run the command `pip install -r requirements.txt` to install all the required packages.

---
#### _2020.10.13_ 

**To reverse a string `str` or list `lst`**, do this: `str = str[::-1]`.

**Set**

* Sets are unordered.
* Set elements are unique. Duplicate elements are not allowed.
* A set itself may be modified, but the elements contained in the set must be of an immutable type.
  
```python
s = 'quux'
>>> set(s)
{'x', 'u', 'q'}

# check if there is duplicated elements
if len(s) > len(set(s)):
     pass
```

---

# MatLab

#### _2020.10.12_ **`sum`, `repmat`, and `randperm`**

`S = sum(A,dim)` returns the [sum](https://www.mathworks.com/help/matlab/ref/sum.html) along dimension dim. For example, if A is a matrix, then sum(A,2) is a column vector containing the sum of each row.
```matlab
A = [1 3 2; 4 2 5; 6 1 4]
> A = 3×3

     1     3     2
     4     2     5
     6     1     4

S = sum(A,2)
> S = 3×1

     6
    11
    11
```

`B = repmat(A,r1,...,rN)` specifies a list of scalars, r1,..,rN, that describes how copies of A are arranged in each dimension. When A has N dimensions, the size of B is size(A).*[r1...rN]. For example, repmat([1 2; 3 4],2,3) returns a 4-by-6 matrix.

```matlab
A = 1:4;
B = repmat(A,4,1)
> B = 4×4

     1     2     3     4
     1     2     3     4
     1     2     3     4
     1     2     3     4
```
```matlab
A = (1:3)';  
B = repmat(A,1,4)
> B = 3×4

     1     1     1     1
     2     2     2     2
     3     3     3     3
```
`p = randperm(n)` returns a row vector containing a random permutation of the integers from 1 to n without repeating elements.

`p = randperm(n)` returns a row vector containing a random permutation of the integers from 1 to n without repeating elements.

`p = randperm(n,k)` returns a row vector containing k unique integers selected randomly from 1 to n.

```matlab
r = randperm(6)
> r = 1×6

     6     3     5     1     2     4
```
```matlab
r1 = randperm(8,4)
> r1 = 1×4

     6     4     7     3
```

---

#### _2020.10.23_ 

**Get the index of the min/max vlaue of the vector/array**
```matlab
[M, I] = min(A)
% where M - is the minimun value
% I - is the index of the minimum value
% Similarly, it works for the max
```

**Get the mean of the array group by one column**
```matlab
X = [X idx];
centroids = grpstats(X(:, 1:n), X(:, (n+1)), "mean");
% get the mean of the 1~n columns
% group by the n+1 column values
```