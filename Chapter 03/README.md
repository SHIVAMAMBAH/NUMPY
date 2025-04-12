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

## ⚙️ **Categories of ufuncs**

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

