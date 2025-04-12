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
