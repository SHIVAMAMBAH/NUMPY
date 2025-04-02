## Indexing and Slicing
### Accessing elements using indexing
```python
# for 1D array
import numpy as np
arr = np.array([12,34,56,78])
print(arr[0]) # give the first element
print(arr[1]) # give the second element
print(arr[-1]) # give the last element
print(arr[-2]) # give the second last element
```
Output
```python
12
34
78
56
```
```python
# for 2D array
import numpy as np
arr = np.array([[12,34,56,78],[23,54,67,89]])
print(arr[0][0]) # give the first element of first row
print(arr[1][0]) # give the second element first element of second row
```
Output
```python
12
23
```
```python
# for 3D array
import numpy as np
arr = np.array([[[12,56,78],[23,54,89]],[[22,64,56],[54,67,89]]])
print(arr[0][0][0]) 
print(arr[1][0][0])
print(arr[0][1][0])
```
Output
```python
12
22
23
```
### Multi-dimensional array slicing
```python
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
```python
[5 6 7 8]
[3 7 11 15]
[[1 2]
 [5 6]]
[[13 14 15 16]
 [9 10 11 12]
 [5  6  7  8]
 [1  2  3  4]]
```
```python
import numpy as np
array_3D = np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]],[[13,14,15],[16,17,18]]])

submatrix_3d = array_3D[:2,:,:] # to slice the first two 2D arrays
print(submatrix_3d)

slice_3d = array_3d[:,0,0] # to slice the first element from all 2D matrices
print(slice_3d)
```
```python
[[[ 1  2  3]
  [ 4  5  6]]

 [[ 7  8  9]
  [10 11 12]]]
[1 7 13]
```
### fancy indexing
Fancy indexing refers to using arrays of integers or boolean values to index into another array. It is more flexible and powerful than regular slicing, allowing for non-sequential and complex element access.
```python
import numpy as np
array = np.array([10,20,30,40,50,60])
indices = np.array([0,2,4])
print(array[indices])
```
Output
```python
[10,30,50]
```
### Boolean masking
Boolean masking is a powerful technique that allows you to filter or manipulate elements of an array based on conditions. A boolean mask is essentially an NumPy Array of the same shape as the original array, where each element is either <mark>True</mark> or <mark>False</mark>. When you apply this mask to an array, it returns the elmenets where the mask it <mark>True</mark>, filtering out the elements where the mask is <mark>False</mark>.

```python
import numpy as np
arr = np.array([12,23,35,56,67,90])
mask = arr>25
print(arr[mask])
```
Output
```python
[35,56,67,90]
```
The condition <mark>arr>25</mark> creates a boolean mask
```
[False, False, True, True, True ,True,True]
```
Set elements greater than 25 to 100
```python
arr[mask] = 100
print(arr)
```
output
```python
[12,23,100,100,100,100]
```
Combining multiple conditions with boolean masking by using the logical operator (&, |,~)
```python
mask = (arr>25) & (arr<45)
print(arr[mask])
```
Output
```python
[35]
```
## Reshaping and Resizing Arrays
### Reshaping arrays using np.reshape()
```python
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
```python
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
Output
```python
[1 2 3 4 5 6]
```
- **ravel()** : It returns a flattened view of the original array whenever possible, meaning it tries to avoid creating a copy and returns a view. However, if the memory layout doesn't allow, it might create a copy.

```python
# Ravel the array
raveled_array = array_2d.ravel()

print(raveled_array)

```
output
```python
[1 2 3 4 5 6]
```
### **Key Differences Between `flatten()` and `ravel()`**

| Feature            | `flatten()`                         | `ravel()`                            |
|--------------------|-------------------------------------|--------------------------------------|
| **Return Type**     | Always returns a new copy           | Returns a view whenever possible     |
| **Modifications**   | Changes to the flattened array don't affect the original | Changes to the raveled array may affect the original if it’s a view |
| **Memory Efficiency** | Less memory efficient (creates a new copy) | More memory efficient (avoids creating a copy if possible) |
| **Usage**           | Use when you need a completely new, independent array | Use when you need a flattened view of the original array |
---

## **3. Expanding Dimensions (`np.newaxis`, `expand_dims()`)**
Sometimes, we need to increase the dimensions of an array.

### **Example: Converting a 1D array to 2D (Row Vector)**
```python
array_1D = arr = np.array([12,23,34,45,56,67,78])
array_row_vector = array_1d[np.newaxis, :]
print(array_row_vector)  # (1, 8)
```
**Output:**
```
[[12,23,34,45,56,67,78]] # 2D array with 1 row and 8 columns
```

### **Example: Converting a 1D array to 2D (Column Vector)**
```python
array_column_vector = array_1d[:, np.newaxis]
print(array_column_vector)  # (8, 1)
```
**Output:**
```
[[12]
 [23]
 [34]
 [45]
 [56]
 [67]
 [78]]
```
- `np.newaxis` adds an extra dimension to convert a 1D array into a 2D row or column vector.

Alternatively, you can use `expand_dims()`:
```python
array_expanded = np.expand_dims(array_1d, axis=0)  # Adds dimension at axis 0
print(array_expanded.shape)  # (1, 6)
```

## **4. Squeezing Dimensions (`squeeze()`)**
The `squeeze()` function removes single-dimensional entries from the shape of an array.

### **Example: Removing Single-Dimensional Entries**
```python
array_3d = np.array([[[1, 2, 3]]])  # Shape (1, 1, 3)

array_squeezed = np.squeeze(array_3d)

print(array_squeezed)  # (3,)
```
**Output:**
```python
[1, 2,3]
```

- `squeeze()` removes dimensions of size 1, making the array more compact.

---

## **Summary**
| Function | Purpose | Modifies Data? | Example |
|----------|---------|---------------|---------|
| `reshape()` | Change shape while keeping the same number of elements | No (returns a new array) | `array.reshape(2,3)` |
| `flatten()` | Convert multi-dimensional array to 1D | Yes (returns a copy) | `array.flatten()` |
| `ravel()` | Convert multi-dimensional array to 1D | No (returns a view) | `array.ravel()` |
| `np.newaxis` | Add a new axis (increase dimensions) | No | `array[:, np.newaxis]` |
| `expand_dims()` | Add an extra dimension | No | `np.expand_dims(array, axis=0)` |
| `squeeze()` | Remove single-dimensional entries | No | `np.squeeze(array)` |
| `resize()` | Change size and modify original array | Yes (modifies in-place) | `array.resize((3,2))` |


## **Concatenating Arrays in NumPy**
NumPy provides multiple ways to combine (concatenate) arrays along different axes. The three most commonly used functions for concatenation are:

1. **`np.concatenate()`** – General-purpose concatenation along any axis.
2. **`np.vstack()`** – Stacks arrays vertically (row-wise).
3. **`np.hstack()`** – Stacks arrays horizontally (column-wise).

---

## **1. `np.concatenate()` – General Concatenation**
The `np.concatenate()` function is used to join two or more arrays along a specified axis.

### **Example: Concatenating 1D Arrays**
```python
import numpy as np

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

result = np.concatenate((arr1, arr2))

print(result)
```
**Output:**
```
[1 2 3 4 5 6]
```
- By default, `np.concatenate()` joins arrays along axis `0` (row-wise for 1D arrays).

---

### **Example: Concatenating 2D Arrays**
```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

# Concatenating along axis=0 (row-wise)
result1 = np.concatenate((arr1, arr2), axis=0)

# Concatenating along axis=1 (column-wise)
result2 = np.concatenate((arr1, arr2), axis=1)

print(result1)  # Row-wise concatenation
print(result2)  # Column-wise concatenation
```
**Output:**
```
[[1 2]
 [3 4]
 [5 6]
 [7 8]]

[[1 2 5 6]
 [3 4 7 8]]
```
- **`axis=0` (rows)** → New rows are added.
- **`axis=1` (columns)** → New columns are added.

---

## **2. `np.vstack()` – Vertical Stacking (Row-wise)**
- `np.vstack()` stacks arrays **vertically** (along axis `0`).
- It is a shortcut for `np.concatenate(..., axis=0)`.

### **Example: Stacking Arrays Vertically**
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

result = np.vstack((arr1, arr2))

print(result)
```
**Output:**
```
[[1 2 3]
 [4 5 6]]
```
- `vstack()` creates a **2D array** from **1D arrays**.

For **2D arrays**, it works the same as `concatenate(..., axis=0)`:
```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

result = np.vstack((arr1, arr2))

print(result)
```
**Output:**
```
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

---

## **3. `np.hstack()` – Horizontal Stacking (Column-wise)**
- `np.hstack()` stacks arrays **horizontally** (along axis `1`).
- It is a shortcut for `np.concatenate(..., axis=1)`.

### **Example: Stacking Arrays Horizontally**
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

result = np.hstack((arr1, arr2))

print(result)
```
**Output:**
```
[1 2 3 4 5 6]
```
- `hstack()` behaves like simple concatenation for 1D arrays.

For **2D arrays**, it works like `concatenate(..., axis=1)`:
```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

result = np.hstack((arr1, arr2))

print(result)
```
**Output:**
```
[[1 2 5 6]
 [3 4 7 8]]
```
- Columns from `arr2` are added to `arr1`.

---

## **Summary Table**
| Function | Concatenation Type | Default Axis | Example |
|----------|--------------------|--------------|---------|
| `np.concatenate()` | General-purpose concatenation | Can be any axis | `np.concatenate((arr1, arr2), axis=1)` |
| `np.vstack()` | Vertical stacking (row-wise) | `axis=0` | `np.vstack((arr1, arr2))` |
| `np.hstack()` | Horizontal stacking (column-wise) | `axis=1` | `np.hstack((arr1, arr2))` |

---

## **Splitting Arrays in NumPy**
NumPy provides several functions to split an array into multiple sub-arrays. The most commonly used functions for array splitting are:

1. **`np.split()`** – General-purpose splitting along a specified axis.
2. **`np.vsplit()`** – Splits an array **vertically** (row-wise).
3. **`np.hsplit()`** – Splits an array **horizontally** (column-wise).

---

## **1. `np.split()` – General Array Splitting**
The `np.split()` function is used to split an array into multiple sub-arrays along a given axis.

### **Example: Splitting a 1D Array**
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])

# Splitting into 3 equal parts
result = np.split(arr, 3)

print(result)
```
**Output:**
```
[array([1, 2]), array([3, 4]), array([5, 6])]
```
- The array is divided into three equal parts.

> **Note:** The number of elements must be **evenly divisible** by the number of splits, otherwise it will raise an error.

### **Example: Splitting a 2D Array**
```python
arr = np.array([[1, 2, 3], 
                [4, 5, 6], 
                [7, 8, 9]])

# Splitting into 3 parts along axis 1 (column-wise)
result = np.split(arr, 3, axis=1)

print(result)
```
**Output:**
```
[array([[1],
        [4],
        [7]]), 
 array([[2],
        [5],
        [8]]), 
 array([[3],
        [6],
        [9]])]
```
- The array is split **column-wise** into three sub-arrays.

---

## **2. `np.vsplit()` – Vertical Splitting (Row-wise)**
- `np.vsplit()` is used to split an array **vertically** (row-wise).
- Equivalent to `np.split(..., axis=0)`.

### **Example: Splitting a 2D Array Row-wise**
```python
arr = np.array([[1, 2, 3], 
                [4, 5, 6], 
                [7, 8, 9]])

# Splitting into 3 rows
result = np.vsplit(arr, 3)

print(result)
```
**Output:**
```
[array([[1, 2, 3]]), 
 array([[4, 5, 6]]), 
 array([[7, 8, 9]])]
```
- The array is **split row-wise** into three sub-arrays.

---

## **3. `np.hsplit()` – Horizontal Splitting (Column-wise)**
- `np.hsplit()` is used to split an array **horizontally** (column-wise).
- Equivalent to `np.split(..., axis=1)`.

### **Example: Splitting a 2D Array Column-wise**
```python
arr = np.array([[1, 2, 3, 4], 
                [5, 6, 7, 8]])

# Splitting into 2 equal parts column-wise
result = np.hsplit(arr, 2)

print(result)
```
**Output:**
```
[array([[1, 2], 
        [5, 6]]), 
 array([[3, 4], 
        [7, 8]])]
```
- The array is **split column-wise** into two parts.

---

## **Summary Table**
| Function | Splitting Type | Default Axis | Example |
|----------|---------------|--------------|---------|
| `np.split()` | General-purpose splitting | Can be any axis | `np.split(arr, 2, axis=1)` |
| `np.vsplit()` | Vertical splitting (row-wise) | `axis=0` | `np.vsplit(arr, 3)` |
| `np.hsplit()` | Horizontal splitting (column-wise) | `axis=1` | `np.hsplit(arr, 2)` |

---
