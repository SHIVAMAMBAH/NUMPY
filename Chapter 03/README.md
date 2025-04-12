##  **Module 3: Basic Array Operations**

Basic array operations are fundamental when working with NumPy. They allow you to manipulate arrays efficiently and perform element-wise computations easily.

---

##  **(8) Basic Array Operations**

NumPy makes it easy to perform arithmetic and logical operations on arrays in a **vectorized** way, meaning operations are applied to **entire arrays at once**, not via loops.

###  1. **Arithmetic Operations**

These operations are performed **element-wise**:

```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)   # [5 7 9]
print(a - b)   # [-3 -3 -3]
print(a * b)   # [4 10 18]
print(a / b)   # [0.25 0.4  0.5 ]
```

 Supports:
- `+` (addition)
- `-` (subtraction)
- `*` (multiplication)
- `/` (division)
- `**` (exponentiation)
- `%` (modulus)

---

###  2. **Unary Operations**

Applied to a single array:
```python
a = np.array([-1, 2, -3])

print(np.abs(a))       # [1 2 3]
print(np.sqrt([1, 4])) # [1. 2.]
print(np.exp([1, 2]))  # [2.71828183 7.3890561 ]
print(np.log([1, np.e]))  # [0. 1.]
```

---

###  3. **Comparison Operations**

Result in **Boolean arrays**:
```python
a = np.array([1, 2, 3])
b = np.array([3, 2, 1])

print(a > b)  # [False False  True]
print(a == b) # [False  True False]
```

These are useful for **masking** and **conditional selection**.

---

###  4. **Aggregate Functions**

These functions compute values over arrays:
```python
a = np.array([[1, 2], [3, 4]])

print(a.sum())         # 10
print(a.min())         # 1
print(a.max())         # 4
print(a.mean())        # 2.5
print(a.std())         # standard deviation
```

You can also specify axis:
```python
print(a.sum(axis=0))   # column-wise sum: [4 6]
print(a.sum(axis=1))   # row-wise sum: [3 7]
```

---

###  5. **Dot Product and Matrix Operations**

```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[2, 0], [1, 3]])

print(a.dot(b))   # Matrix multiplication
```

Also supports:
- `np.matmul()`
- `@` operator (Python 3.5+)

---

###  What are Universal Functions (ufuncs)?

In **NumPy**, **universal functions**, or **ufuncs**, are functions that **operate element-wise on `ndarray` objects**. They are implemented in C for performance and support broadcasting, type casting, and multiple input/output arrays.

Ufuncs are much faster than looping through array elements in pure Python and are key to **NumPy’s speed and efficiency**.

---

##  **Categories of ufuncs**

Ufuncs are classified into different types based on the kind of operation they perform.

---

###  1. **Arithmetic ufuncs**
These perform element-wise arithmetic:

| Function         | Description              | Example                  |
|------------------|--------------------------|--------------------------|
| `np.add(x, y)`   | Addition                 | `np.add([1, 2], [3, 4])` → `[4 6]` |
| `np.subtract(x, y)` | Subtraction           | `[1, 2] - [3, 4]` → `[-2 -2]` |
| `np.multiply(x, y)` | Multiplication         | `[1, 2] * [3, 4]` → `[3 8]` |
| `np.divide(x, y)`   | Division               | `[4, 9] / [2, 3]` → `[2.0 3.0]` |
| `np.power(x, y)`    | Power (x^y)            | `np.power([2, 3], 2)` → `[4 9]` |
| `np.mod(x, y)`      | Modulus (remainder)    | `np.mod([5, 7], 2)` → `[1 1]` |

---

###  2. **Trigonometric ufuncs**

| Function         | Description                    | Example                  |
|------------------|--------------------------------|--------------------------|
| `np.sin(x)`      | Sine (radians)                 | `np.sin(np.pi/2)` → `1.0` |
| `np.cos(x)`      | Cosine                         | `np.cos(0)` → `1.0`       |
| `np.tan(x)`      | Tangent                        | `np.tan(np.pi/4)` → `1.0` |
| `np.arcsin(x)`   | Inverse sine                   | `np.arcsin(1)` → `π/2`    |

---

###  3. **Exponential and Logarithmic ufuncs**

| Function         | Description                | Example                  |
|------------------|----------------------------|--------------------------|
| `np.exp(x)`      | Exponential `e^x`          | `np.exp([1, 2])` → `[2.718, 7.389]` |
| `np.log(x)`      | Natural log                | `np.log([1, np.e])` → `[0, 1]` |
| `np.log10(x)`    | Base-10 log                | `np.log10([1, 10])` → `[0, 1]` |

---

###  4. **Rounding ufuncs**

| Function           | Description           | Example                  |
|--------------------|-----------------------|--------------------------|
| `np.round(x)`      | Round to nearest int  | `np.round([1.23, 2.56])` → `[1. 3.]` |
| `np.floor(x)`      | Round down            | `np.floor([1.9, 2.1])` → `[1. 2.]` |
| `np.ceil(x)`       | Round up              | `np.ceil([1.1, 2.5])` → `[2. 3.]` |

---

###  5. **Comparison ufuncs**

| Function             | Description       | Example                        |
|----------------------|-------------------|--------------------------------|
| `np.greater(x, y)`   | `x > y`           | `[3, 2] > [1, 2]` → `[True, False]` |
| `np.less_equal(x, y)`| `x <= y`          | `[1, 2] <= [2, 2]` → `[True, True]` |
| `np.equal(x, y)`     | `x == y`          | `[1, 2] == [1, 3]` → `[True, False]` |

---

##  Why use ufuncs?

- **Performance:** Way faster than Python loops (implemented in C).
- **Readability:** Makes code more concise and expressive.
- **Broadcasting support:** Works with arrays of different shapes.
- **Vectorized operations:** Enables parallelized computations.

---

###  What is Broadcasting?

**Broadcasting** is a set of rules used by NumPy to **perform operations on arrays of different shapes and sizes**. Instead of manually resizing arrays, NumPy automatically stretches the smaller array across the larger one so that element-wise operations can proceed.

This allows for **efficient vectorized computation** without writing explicit loops or reshaping arrays.

---

##  Broadcasting Rules

To determine whether broadcasting is possible, NumPy compares the shapes of the arrays **from right to left**.

### **Rule 1:** If the dimensions are equal, they’re compatible.  
### **Rule 2:** If one of the dimensions is `1`, it can be broadcast to match the other.  
### **Rule 3:** If neither dimension is equal or `1`, it's incompatible → **Error**.

---

##  Examples to Understand Broadcasting

###  **1. Scalar + Array**
```python
a = np.array([1, 2, 3])
b = 5
print(a + b)  # Output: [6 7 8]
```
The scalar `5` is broadcasted to `[5, 5, 5]`.

---

###  **2. 1D Array + 2D Array**
```python
a = np.array([[1], [2], [3]])  # Shape: (3, 1)
b = np.array([10, 20, 30])     # Shape: (3,)

# To broadcast, b becomes: [[10, 20, 30]]
# Resulting in shape (3, 3)
```

---

###  **3. Matrix + Row Vector**
```python
A = np.array([[1, 2, 3],
              [4, 5, 6]])    # Shape: (2, 3)

b = np.array([10, 20, 30])    # Shape: (3,)

# Result: each row of A has b added to it
```

---

###  **4. Incompatible Shapes**
```python
a = np.array([[1, 2], [3, 4]])  # Shape: (2, 2)
b = np.array([1, 2, 3])         # Shape: (3,)

#  Cannot broadcast: 2 ≠ 3 and neither is 1 → Error
```

---

##  Broadcasting in Action

```python
a = np.arange(3)              # [0 1 2]
b = np.arange(3).reshape(3, 1) # [[0], [1], [2]]

result = a + b
# Output:
# [[0 1 2]
#  [1 2 3]
#  [2 3 4]]
```

Here:
- `a` shape = `(3,)`
- `b` shape = `(3, 1)`
- Resulting shape = `(3, 3)` via broadcasting

---

##  Why Broadcasting is Important

| Feature         | Advantage                                  |
|----------------|---------------------------------------------|
| Efficiency      | Faster than loops (done in C backend)      |
| Simplicity      | Cleaner syntax for mathematical operations |
| Flexibility     | Works with arrays of different shapes      |

---


##  **Linear Algebra in NumPy**

NumPy offers a robust set of tools for **linear algebra**, which is the foundation of scientific computing, data science, computer graphics, and machine learning.

These operations are part of the `numpy.linalg` module (Linear Algebra module).

---

##  **1. Vectors and Matrices**

- **Vector** → 1D array  
  Example: `v = np.array([1, 2, 3])`
- **Matrix** → 2D array  
  Example: `M = np.array([[1, 2], [3, 4]])`

You can also create matrices using:
```python
np.matrix([[1, 2], [3, 4]])
```

---

##  **2. Matrix Operations**

| Operation                    | Function                          |
|------------------------------|-----------------------------------|
| Matrix multiplication        | `np.dot(A, B)` or `A @ B`         |
| Transpose                    | `A.T`                             |
| Determinant                  | `np.linalg.det(A)`                |
| Inverse                      | `np.linalg.inv(A)`                |
| Eigenvalues and Eigenvectors| `np.linalg.eig(A)`                |
| Solving Ax = B               | `np.linalg.solve(A, B)`           |
| Rank of matrix               | `np.linalg.matrix_rank(A)`        |
| Trace (sum of diagonals)     | `np.trace(A)`                     |

---

##  **3. Example Use Cases**

###  Matrix Multiplication:
```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[2, 0], [1, 2]])

np.dot(A, B) or A @ B
```

###  Solving a Linear System:
Solving `Ax = b`:
```python
A = np.array([[3, 1], [1, 2]])
b = np.array([9, 8])

x = np.linalg.solve(A, b)
```

---

##  Performance Benefits

- NumPy uses **optimized C/Fortran BLAS libraries** under the hood.
- Can handle **very large matrices** efficiently.
- Supports operations that are core to **machine learning** and **engineering problems**.

---

##  Applications in Real Life

| Field              | Usage                                      |
|--------------------|--------------------------------------------|
| Machine Learning   | Solving systems of equations, PCA, etc.     |
| Physics/Engineering| Simulating mechanics, electrical networks  |
| Graphics/Games     | 3D transformations and projections         |
| Data Science       | Dimensionality reduction, optimization     |

---

