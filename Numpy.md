
## Creating Arrays

### Basic Arrays
```python
import numpy as np

# Create 1D array
arr1d = np.array([1, 2, 3, 4, 5])

# Create 2D array
arr2d = np.array([[1, 2, 3], [4, 5, 6]])

# Create array with zeros
zeros = np.zeros((3, 4))

# Create array with ones
ones = np.ones((2, 3))

# Create identity matrix
identity = np.eye(3)

# Create array with range
range_arr = np.arange(0, 10, 2)  # start, stop, step

# Create linearly spaced array
linspace = np.linspace(0, 1, 5)  # start, stop, num_points
```

### Special Arrays
```python
# Empty array (contains garbage values)
empty = np.empty((2, 2))

# Full array
full = np.full((2, 2), 7)  # shape, fill_value

# Random array
random = np.random.random((2, 2))
```

## Array Attributes
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print("Array shape:", arr.shape)  # (2, 3)
print("Number of dimensions:", arr.ndim)  # 2
print("Number of elements:", arr.size)  # 6
print("Data type:", arr.dtype)  # int64
print("Item size:", arr.itemsize)  # 8 (bytes)
```

## Array Operations

### Arithmetic Operations
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print("Addition:", a + b)
print("Subtraction:", a - b)
print("Multiplication:", a * b)
print("Division:", b / a)
print("Exponentiation:", a ** 2)
```

### Matrix Operations
```python
mat1 = np.array([[1, 2], [3, 4]])
mat2 = np.array([[5, 6], [7, 8]])

# Matrix multiplication
print("Matrix multiplication:\n", np.dot(mat1, mat2))
print("Alternative multiplication:\n", mat1 @ mat2)

# Element-wise multiplication
print("Element-wise multiplication:\n", mat1 * mat2)
```

## Indexing & Slicing

### Basic Indexing
```python
arr = np.array([0, 1, 2, 3, 4, 5])

print("First element:", arr[0])
print("Last element:", arr[-1])
print("Slice from index 1 to 4:", arr[1:4])
print("Every other element:", arr[::2])
```

### Multi-dimensional Indexing
```python
arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

print("First row:", arr2d[0])
print("Last column:", arr2d[:, -1])
print("Submatrix:\n", arr2d[1:3, 0:2])
```

### Boolean Indexing
```python
arr = np.array([1, 2, 3, 4, 5, 6])
print("Elements greater than 3:", arr[arr > 3])
```

## Array Manipulation

### Reshaping
```python
arr = np.arange(1, 13)

# Reshape to 3x4 matrix
reshaped = arr.reshape(3, 4)

# Flatten array
flattened = reshaped.flatten()
```

### Stacking
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Vertical stack
vstack = np.vstack((a, b))

# Horizontal stack
hstack = np.hstack((a, b))
```

### Splitting
```python
arr = np.arange(1, 10)

# Split into 3 equal parts
split_arr = np.split(arr, 3)
```

## Universal Functions (ufuncs)
```python
arr = np.array([1.2, 2.3, 3.4])

print("Floor:", np.floor(arr))
print("Ceil:", np.ceil(arr))
print("Round:", np.round(arr))
print("Absolute:", np.abs(np.array([-1, -2])))
print("Square root:", np.sqrt(arr))
print("Exponential:", np.exp(arr))
print("Logarithm:", np.log(arr))
```

## Linear Algebra
```python
from numpy import linalg

mat = np.array([[1, 2], [3, 4]])

# Determinant
print("Determinant:", linalg.det(mat))

# Inverse
print("Inverse:\n", linalg.inv(mat))

# Eigenvalues and eigenvectors
eigenvalues, eigenvectors = linalg.eig(mat)
print("Eigenvalues:", eigenvalues)
print("Eigenvectors:\n", eigenvectors)

# Solve linear equations
# 1x + 2y = 5
# 3x + 4y = 6
a = np.array([[1, 2], [3, 4]])
b = np.array([5, 6])
print("Solution:", linalg.solve(a, b))
```

## Random Module
```python
# Random float between 0 and 1
print(np.random.rand())

# Random array
print(np.random.rand(2, 3))

# Random integers
print(np.random.randint(1, 10, size=(3, 3)))

# Normal distribution
print(np.random.normal(loc=0, scale=1, size=5))

# Shuffle array
arr = np.arange(10)
np.random.shuffle(arr)
print("Shuffled array:", arr)

# Set random seed for reproducibility
np.random.seed(42)
```

## Practical Examples

### Image Processing
```python
# Create RGB image (height, width, channels)
image = np.random.randint(0, 256, (100, 100, 3), dtype=np.uint8)

# Convert to grayscale
gray_image = np.mean(image, axis=2).astype(np.uint8)
```

### Data Analysis
```python
# Create sample data
data = np.random.normal(0, 1, 1000)

# Basic statistics
print("Mean:", np.mean(data))
print("Standard deviation:", np.std(data))
print("Median:", np.median(data))
print("Min/Max:", np.min(data), np.max(data))
```

### Solving Equations
```python
# Solve system of equations
A = np.array([[2, 1], [1, 3]])
B = np.array([8, 13])
solution = np.linalg.solve(A, B)
print("Solution (x, y):", solution)
```

## Conclusion
NumPy is essential for:
- Numerical computing in Python
- Data analysis and manipulation
- Machine learning and deep learning
- Scientific computing and research

### Best Practices
1. Use vectorized operations instead of loops
2. Leverage broadcasting for efficient computations
3. Prefer built-in functions over custom implementations
4. Use appropriate data types to save memory


```python
# Final Example: Image Filter
def apply_filter(image, filter_size=3):
    kernel = np.ones((filter_size, filter_size)) / (filter_size ** 2)
    filtered = np.zeros_like(image)
    for i in range(image.shape[0] - filter_size + 1):
        for j in range(image.shape[1] - filter_size + 1):
            filtered[i, j] = np.sum(image[i:i+filter_size, j:j+filter_size] * kernel)
    return filtered
```

4. Array manipulation methods
5. Linear algebra operations
6. Random number generation
7. Practical applications

You can save this as `numpy_tutorial.md` and upload it to GitHub. The tutorial is structured with clear examples and explanations suitable for beginners to intermediate users.
