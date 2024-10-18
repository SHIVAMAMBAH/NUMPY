# <div align = "center">NUMPY</div>
## Content
### Module 1 : Introduction to NumPy
- 1 . What is NumPy?
     - Overview of NumPy and its importance
     - Key features : performance, ease of use and broadcasting
     - Comparison with Python Lists
- 2 . NumPy Arrays v/s Python Lists
     - Why NumPy arrays are faster
     - Memory efficiency comparison
     - Basic operations on Python lists v/s NumPy arrays
- 3 . Creating NumPy Arrays
     - creatinig arrays using <mark>np.array()</mark>
     - Array data types
     - Creating multi-dimensional arrays
     - functions for array creation
       - <mark>np.zeroes()</mark>, <mark>np.ones()</mark>, <mark>np.full()</mark>, <mark>np.arange()</mark>, <mark>np.linspace()</mark>
- 4 . Array Attributes
     - Shape of arrays
     - Number of dimensions
     - Data type
     - Size of arrays
### Module 2 : Array Manipulation
- 5 . Indexing and Slicing
  - Accessing elements using indexing
  - Multi-dimensional array slicing
  - Fancy indexing
  - Boolean masking
- 6 . Reshaping and Resizing Arrays
  - Reshaping arrays using <mark>np.reshape()</mark>
  - Flattening arrays (<mark>.flattern()</mark>, <mark>ravel()</mark>)
  - Changing array dimension
  - Exapanding and sqeezing dimensions
- 7 . Concatenation and Splitting Arrays
  - Concatenating arrays (<mark>np.concatenate()</mark>, <mark>np.vstack()</mark>, <mark>np.hstack()</mark>)
  - Splitting arrays (<mark>np.split()</mark>, <mark>np.vsplit()</mark>, <mark>np.hsplit()</mark>)
### Module 3 : Operations on NumPy Arrays
- 8 . Basic Array Operation
  - Element-wise operations (+, -, *, /)
  - Universal functions(ufuncs) : <mark>np.sqrt()</mark>, <mark>np.sin()</mark>, <mark>np.exo()</mark>, <mark>np.log()</mark>
  - Broadcasting in NumPy
- 9 .Mathematical and Staistical Functions
  - Array-wide operations : <mark>np.sum()</mark>, <mark>np.min()</mark>, <mark>np.max()</mark>, <mark>np.mean()</mark>, <mark>np.std()</mark>, <mark>np.median()</mark>
  - Aggegrate functions : axis-based aggegration
- 10 . Linear Algebra in NumPy
  - Matrix multiplication (<mark>np.dot()</mark>, <mark>@</mark> operator)
  - Matrix transposition (.T)
  - Determinant and inverse of a matrix
  - Solving linear systems with <mark>np.linalg.solve()</mark>
### Module 4 : Advanced Array Concepts
- 11 . Broadcasting
  - Exaplanation of broadcasting rules
  - Practical examples
  - Understanding how arrays with different shapes interact
- 12 . Vectorization
  - Importance of vectorized operations for performance
  - Writing efficient NUmPy code
- 13 . Random Number Generator
  - using np.random module
  - Generating random numbers
  - Setting random seeds
  - Random sampling from disributions
### Module 5 : Input/Output with NumPy
- 14 . Saving and Loading data
  - saving arrays to files using <mark>np.save()</mark>, <mark>np.savez()</mark>
  - Loading arrays from files using
- 15 . Text and CSV files
  - Reading and writing arrays to/from text files (<mark>np.savetxt()</mark>, <mark>np.loadtxt()</mark>)
  - Handling CSV files (<mark>np.genfromtxt()</mark>, ,<mark>np.recfromcsv()</mark>)
### Module 6 : Numerical Computations and Performance
- 16 . Working with Large Arrays
  - handling large datasets with NumPy
  - Efficient memory usage
  - Performance considerations and optimization techniques
- 17 . NumPy with Pandas
  - Integrating NumPy arrays with Pandas DataFrames
  - Converting between NumPy arrays and Pandas objects
### Module 7 : Applications of NumPy
- 18 . Image Processing
- 19 . Solving Mathematical Equations
- 20 . Data Analysis and scientific Computing
