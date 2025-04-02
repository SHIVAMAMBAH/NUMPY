## Indexing and Slicing
### Accessing elements using indexing
```
# for 1D array
import numpy as np
arr = np.array([12,34,56,78])
print(arr[0]) # give the first element
print(arr[1]) # give the second element
print(arr[-1]) # give the last element
print(arr[-2]) # give the second last element
```
Output
```
12
34
78
56
```
```
# for 2D array
import numpy as np
arr = np.array([[12,34,56,78],[23,54,67,89]])
print(arr[0][0]) # give the first element of first row
print(arr[1][0]) # give the second element first element of second row
```
Output
```
12
23
```
```
# for 3D array
import numpy as np
arr = np.array([[[12,56,78],[23,54,89]],[[22,64,56],[54,67,89]]])
print(arr[0][0][0]) 
print(arr[1][0][0])
print(arr[0][1][0])
```
Output
```
12
22
23
```
### Multi-dimensional array slicing
```
import numpy as np
array_2D = np.array([[1,2,3,5],
                     [5,6,7,8],
                     [9,10,11,12],
                     [13,14,15,16]])
row_slice = array_2D[1,:] # slice the second row (index 1)
print(row_slice)

column_slice = array_2D[:,2] # slice the third column (index 2)
print(column_slice)

submatrix = array_2D[0:2, 0:2] # top-left 2x2 matrix
print(submatrix)

reverse_rows = array_2D[::-1,:]
print(reverse_rows)
```
Output
```
[5 6 7 8]
[3 7 11 15]
[[1 2]
 [5 6]]
[[13 14 15 16]
 [9 10 11 12]
 [5  6  7  8]
 [1  2  3  4]]
```
```
import numpy as np
array_3D = np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]],[[13,14,15],[16,17,18]]])

submatrix_3d = array_3D[:2,:,:] # to slice the first two 2D arrays
print(submatrix_3d)

slice_3d = array_3d[:,0,0] # to slice the first element from all 2D matrices
print(slice_3d)
```
```
[[[ 1  2  3]
  [ 4  5  6]]

 [[ 7  8  9]
  [10 11 12]]]
[1 7 13]
```
### fancy indexing
Fancy indexing refers to using arrays of integers or boolean values to index into another array. It is more flexible and powerful than regular slicing, allowing for non-sequential and complex element access.
```
import numpy as np
array = np.array([10,20,30,40,50,60])
indices = np.array([0,2,4])
print(array[indices])
```
Output
```
[10,30,50]
```
### Boolean masking
Boolean masking is a powerful technique that allows you to filter or manipulate elements of an array based on conditions. A boolean mask is essentially an NumPy Array of the same shape as the original array, where each element is either <mark>True</mark> or <mark>False</mark>. When you apply this mask to an array, it returns the elmenets where the mask it <mark>True</mark>, filtering out the elements where the mask is <mark>False</mark>.

```
import numpy as np
arr = np.array([12,23,35,56,67,90])
mask = arr>25
print(arr[mask])
```
Output
```
[35,56,67,90]
```
The condition <mark>arr>25</mark> creates a boolean mask
```
[False, False, True, True, True ,True,True]
```
Set elements greater than 25 to 100
```
arr[mask] = 100
print(arr)
```
output
```
[12,23,100,100,100,100]
```
Combining multiple conditions with boolean masking by using the logical operator (&, |,~)
```
mask = (arr>25) & (arr<45)
print(arr[mask])
```
Output
```
[35]
```
## Reshaping and Resizing Arrays
### Reshaping arrays using np.reshape()
```
import numpy as np

arr = np.array([12,23,34,65,67,89,90,87])
arr.resize(2,4) # resize to get 2 rows and 4 columns
print(arr)

arr = arr.resize(-1) # to get to the original array

arr = arr.resize(4,2) # resize to the 4 rows and 2 columns
print(arr)

arr = arr.reshape(-1)

arr = arr.resize(arr,(10,)) # resize to get the 10 elements, extra elements will repeat if necessary
print(arr)

arr = arr.resize(arr,(6,)) # resize to get the 6 elements, extra elements will get truncate
print(arr)

```
Output
```
[[12,23,34,65]
 [67,89,90,87]]

[[12,23]
 [34,65]
 [67,89]
 [90,87]]

[12,23,34,65,67,89,90,87,12,23]

[12,23,34,65,67,89]
```
## **Key Differences**
| Feature         | `reshape()` | `resize()` |
|---------------|------------|------------|
| Returns a new array? | ✅ Yes (does NOT modify original) | ❌ No (modifies original array) |
| Supports `-1`? | ✅ Yes | ❌ No |
| Requires exact match of elements? | ✅ Yes | ❌ No (fills with zeros if needed) |
| Works in-place? | ❌ No | ✅ Yes |
---

### Flattening arrays (.flattern(), ravel())
Both are used to convert multi-dimensional arrays into a one-dimensional array, but they gave some key differences in how they handle the original data.
- **flatten()** : It returns a copy of the original array in 1D form, meaning it always created a new copy. The original array remaines unchanged.
```python
import numpy as np

# Create a 2D array
array_2d = np.array([[1, 2, 3], [4, 5, 6]])

# Flatten the array
flattened_array = array_2d.flatten()

print(flattened_array)

```

- **ravel()** : It returns a flattened view of the original array whenever possible, meaning it tries to avoid creating a copy and returns a view. However, if the memory layout doesn't allow, it might create a copy. 
