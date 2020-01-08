# Function, generator, and class

### Function
A function can be seen as executable code blocks, which is reusable.
It start with the def keyword, a function name with input parameters, and use return to output values.

- Example
```
def f(x,y):
    return x*y
```
```
f(3,4)
```
12

- Print a sequence without for loop, a function can return itself
```
def f(x,y):
    print(x)
    if x < y:
        x = x + 1
        return f(x, y)
```
```
f(1,5)
```
1<br/>
2  
3<br/>
4  
5

- Binary search
```
## binary search : only for sorted array, repeatedly dividing the search interval in half, O(logN)
def binary_search(X, x, l, r):
    if r >= l:
        mid = l + (r - l)//2
        if X[mid] == x:
            return mid
        elif X[mid] > x:
            return binary_search(X, x, l=0, r=mid-1)
        else:
            return binary_search(X, x, l=mid+1, r=len(X))
    else:
        return "Not found!"
```
```
A = list(range(10))
binary_search(A, 7, l=min(A), r=max(A))
```
7

### Generator
A generator is an iterator, but we can only iterate over them once.
