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
