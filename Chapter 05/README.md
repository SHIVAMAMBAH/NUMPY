##  **Saving and Loading Data in NumPy**

NumPy provides built-in functions to **save** and **load** arrays in binary format for quick and efficient reuse.

---

##  **1. Saving Arrays to Files**

###  `np.save(filename, array)`
- Saves a single NumPy array to a binary file in `.npy` format.
- Fast and space-efficient.
  
**Example:**
```python
arr = np.array([1, 2, 3, 4])
np.save('my_array.npy', arr)
```

---

###  `np.savez(filename, array1, array2, ...)`
- Saves **multiple arrays** into a single `.npz` file (a zipped archive).
- You can use **keywords** to name the arrays.

**Example:**
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
np.savez('arrays.npz', first=a, second=b)
```

---

##  **2. Loading Arrays from Files**

###  `np.load(filename)`
- Loads `.npy` or `.npz` files back into NumPy.

**For `.npy` file:**
```python
arr = np.load('my_array.npy')
```

**For `.npz` file:**
```python
data = np.load('arrays.npz')
print(data['first'])   # Output: array([1, 2, 3])
print(data['second'])  # Output: array([4, 5, 6])
```

---

##  Advantages

| Feature           | `.npy` / `.npz` Format |
|------------------|------------------------|
|  Speed         | Binary format is very fast |
|  Compression   | `.npz` uses zipped archive |
|  Easy to Use   | One-liners to save/load arrays |
|  Metadata      | Keeps data types and shapes |

---

##  Summary

| Task        | Function             | Format     |
|-------------|----------------------|------------|
| Save array  | `np.save()`          | `.npy`     |
| Save multiple arrays | `np.savez()` or `np.savez_compressed()` | `.npz` |
| Load array  | `np.load()`          | `.npy`, `.npz` |

---
