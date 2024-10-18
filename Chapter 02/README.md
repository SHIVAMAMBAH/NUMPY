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
Boolean masking is a powerful technique that allows you to filter or manipulate elements of an array based on conditions. A boolean mask is essentially an NumPy Array of the same shape as the original array, where each element is either <mark>Trus</mark> or <mark>False</mark>. When you apply this mask to an array, it returns the elmenets where the mask it <mark>True</mark>, filtering out the elements where the mask is <mark>False</mark>.

