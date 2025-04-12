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

Awesome! Let's now explore how NumPy handles **text and CSV files**. This is incredibly useful when you're dealing with real-world datasets, logs, or exported spreadsheets.

---

##  **Working with Text and CSV Files in NumPy**

NumPy offers simple yet powerful tools to read from and write to **text and CSV files** directly.

---

##  **1. Reading and Writing Arrays to/from Text Files**

###  `np.savetxt()`

Saves an array to a **plain text** file (including CSV format).

**Syntax:**
```python
np.savetxt('filename.txt', array, delimiter=',', fmt='%d')
```

**Example:**
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
np.savetxt('data.csv', arr, delimiter=',', fmt='%d')
```

---

###  `np.loadtxt()`

Loads data from a text file or CSV into an array.

**Syntax:**
```python
np.loadtxt('filename.txt', delimiter=',', dtype=int)
```

**Example:**
```python
data = np.loadtxt('data.csv', delimiter=',', dtype=int)
```

---

##  **2. Handling CSV Files**

For more flexibility (e.g., missing data, headers), NumPy provides:

---

###  `np.genfromtxt()`

- Reads CSV/text files.
- Handles **missing values**, **comments**, and **headers**.

**Syntax:**
```python
np.genfromtxt('file.csv', delimiter=',', skip_header=1, filling_values=0)
```

**Example:**
```python
data = np.genfromtxt('data_with_header.csv', delimiter=',', skip_header=1)
```

---

###  `np.recfromcsv()`

- Loads CSV data as a **record array** (like a table with named columns).
- Automatically **infers data types** from the header.

**Syntax:**
```python
np.recfromcsv('file.csv')
```

**Example:**
```python
records = np.recfromcsv('students.csv')
print(records.name)  # Access column by name
```

---

##  Summary Table

| Function             | Purpose                         | Key Feature                          |
|----------------------|----------------------------------|--------------------------------------|
| `np.savetxt()`       | Save array to plain text/CSV     | Simple and fast                      |
| `np.loadtxt()`       | Load text/CSV into array         | Clean files with no headers          |
| `np.genfromtxt()`    | Load with flexibility            | Skips headers, handles missing data  |
| `np.recfromcsv()`    | Record arrays from CSV           | Columns accessible by name           |

---
