## What is NumPy?
### Overview of NumPy and its Importance
NUmPy (Numerical Python) is a **open-source** Python library that provides powerful tools for scientific computing and numerical data processing. At its core, NumPy introduces the array data structure, which is similar to lists in Pyhton but with enhanced performance and functionality.<br>
**Key features of the NumPy** : <br>
- **Multi-dimensional Arrays** : NumPy provides support for n-dimensional arrays, allowing you to store and manipulate data in multi-dimensional formats like matrices, tensors etc.
- **Vectorized Operations** : With NumPy, operations are performed element-wise, allowing for vectorized computations. Thus leads to faster and more efficient code execution.
- **Mathematical Functions** : It provides a wide range of mathematical functions such as linear algebra operations, fourier trasnsforms, random number generator, and statistical calculations.
- **Broadcasting** : NumPy can handle arrays of different shapes and sizes through a mechanism called broadcasting, allowing for operations that involve arrays of different dimensions without explicitly rehshaping them.<br>

**Importance of NumPy** <br>
- High performance and efficiency
- Foundation of the scientific pythin ecosystem
- Ease of use with mathemtical operations
- Memory Efficiency
- Data Analyst and Machine Learning
### Key features : performance, ease of use and broadcasting
**Performance** <br>
NumPy is highly optimized for performance, especialy when working with large datasets and numerical computations. Its performance advantages primarily come from one of the following factors:
- **vectorization** : NumPy performs element-wise operations on arrays without the need for explicit loops in python. This is achieved through vectorization, *which is the process of applying operations over entire arrays*, making use of fast, low-level machine instructions.
- **Cotiguous Memory layout** : Unlike python lists, which are a collection of pointers to objects stored in memory, NumPy arrays are stored in contiguous blocks of memory. This allows for more efficient memory access and makes operations like slicing, indexing, and broadcasting extremely fast.
- **Low-Level Optimizationss** : NumPy is implemented in C and uses optimized, comppiled code for its core functions. This ensures that operations on arrays are performed at near-native speeds. Additionally, NumPy leverages multi-threading for operations that can be parallelized, leading to further performance gains.
- **Efficient Mathematical Libraries** : NumPy uses highly optimized libraraies like **BLAS** (Basic Linear Algebra Subprograms) and **LAPACK** (Linear Algebra Package) for performaing linear algebra operations. These libraries are highly tuned and offer significant speed improvments for matrix operations, such as matrix multiplication, inversion and eigenvalue computations.<br>

**NumPy Arrays v/s Python Lists**<br>

|**Feature**|**Arrays**|**Lists**|  
|-------|------|-----|
|**Performance**|Much faster due to optimized C implementation and vectorized operations|Slower, as list store pointers to objects and require python loops for operations|
|**Memory Efficiency**|More memory-efficient, as arrays store data in contiguous blocks with fixed data types.|Less memory-efficient, as each element is a reference to an object, and types can vary|
|**Data Type**|Homogeneous (all elements must be of the same type)|Heterogeneous (element can be of different types)|
|**Mathematical Operations**| Supports element-wise operations and built-in mathematical functions (e.g. <mark>sum()</mark>, <mark>mean()</mark>, etc).|Requires manual looping or list comprehensions for element-wise operations.|
|**Dimensionality**|Supports multi-dimensional arrays (e.g. 2D, 3D arrays, matrices)|Primarily 1D, though you can nest lists to create multi-dimensional structures, but they're less efficient and harder to manipulate|
|**Broadcasring**|Supports broadcasting, allowing operations between arrays of different shapes|No broadcasting supports; operations requires matching list lengths or explicit reshaping|
|**Memory usage**|uses less memory for large datasets due to homogeneous data storage and contiguous memory allocation|USes more memory as each element is an object, requiring extra overhead for references|

### Creating NumPy arrays
Install numpy in your local device.<br>
For windows(make sure python is installed) : Open command prompt or cmd and the type
```
pip install numpy
```
we can create a NumPy array by using the array() function present in the NumPy.
```
import numpy as np
arr = np.array([12,23,45,67,89]) # 1D array with int values
arr = np.array([12.32,45.87,45.76,78.90]) # 1D array with float values
arr = np.array([[21,32,43],[56,67,89]]) # 2D array
arr = np.array([[[21,32,43],[56,67,89]],[[11,82,63],[50,60,80]]]) # 3D array
# 2D and 3D array with float values can be created in the similar way
```
you can check the data type of the array by using the array.dtype method 
```
arr.dtype
```
This is a list of data types that exits in numpy
```
np.int8 # 8-bit
np.int16 # 16-bit
np.int32 # 32-bit
np.int64 # 64-bit
np.unit8 # 8-bit
np.uint16 # 16-bit
np.uint32 # 32-bit
np.uint64 # 64-bit
np.float16 # half precision floating point
np.float32 # single precision floating point
np.float64 # double precision floatinig point
np.complex64 # complex numbers, represented by two 32-bit floats
np.complex128 # complex numbers, represented by two 64-bit floats
np.bool # Boolean type (True or Flase)
np.object # Python object type (can hold any python object)
np.str # string data tyoe
np.void # represent raw data (no specific type)
```
Using functions np.zeros(), np.ones(), np.full(), np.arange(), np.linspace() for creating arrays
```
import numpy as np
arr = np.zeros(2,3) # create an array of size 2x3 filled with zeroes
print(arr)
```
Output
```
[[0. 0. 0.]
 [0. 0. 0.]]
```
```
import numpy as np
arr = np.ones(2,3) # create an array of size 2x3 filled with ones
print(arr)
```
Output
```
[[1 1 1]
 [1 1 1]]
```
```
import numpy as np
arr = np.full((2,3),7) # create an array of size 2x3 filled with 7
print(arr)
```
Output
```
[[7 7 7]
 [7 7 7]]
```
```
import numpy as np
arr = np.arange(0,10,2) # create an array with evenly spaced values within a given interval
print(arr)
```
Output
```
[0 2 4 6 8]
```
```
import numpy as np
arr = np.linspace(0,1,5) # create an array with evenly spaced values within a given interval
print(arr)
```
Output
```
[0. 0.25 0.5 0.75 1.]
```
**Array Attributes**
```
import numpy as np
arr = np.array([12,23,45,54])
print(arr.size) 
print(arr.shape)
print(arr.ndim)
print(arr.dtype)
```
Output
```
4 # size
(4,) # shape
1 # ndim
int16 # datatype
```



