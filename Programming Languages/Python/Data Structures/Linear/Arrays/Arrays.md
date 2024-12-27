An array holds a **fixed** number of elements of the same kind, which are stored in contagious memory locations.

Array stores each element in a **continuous block** which can be accessed using its **index**.

# Declare One Dimensioanl Array
1. Use a list
```Python
arr = [1, 2, 3, 4, 5]

# Accessing elements
print(arr[0])  # Output: 1
print(arr[2])  # Output: 3
```

2. Use the `array` module
```Python
import array

arr = array.array('i', [1, 2, 3, 4, 5])  # 'i' stands for integer type

print(arr[0])  # Output: 1
print(arr[2])  # Output: 3
```

3. `numpy` library
```Python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr[0])  # Output: 1
print(arr[2])  # Output: 3
```

## Traversing the Array
Python uses 0-based indexing  
(There is also n-based indexing)

Use for loop to go through all the indices in the array.  
```Python
arr = [1, 2, 3, 4, 5]

# Iterating through all elements
for i in range(len(arr)):
    print(f"arr[{i}] = {arr[i]}")
```

## Inserting an Element in the Array
**At The End**  
```Python

# Inserting an element at the end
arr.append(6)
```

```Python
import numpy as np

# Initial array
arr = np.array([1, 2, 3, 4, 5])

arr = np.append(arr, 6)  # `np.append` returns a new array

print(arr)  # Output: [1 2 3 4 5 6]
```

**At Any Other Position**  
```Python
# Initial array
arr = [1, 2, 3, 4, 5]

# Input the element to be inserted and the position
num = int(input("Enter the number to be inserted: "))
pos = int(input("Enter the position at which the number is to be added: "))

# Insert the element at the specified position
arr.insert(pos, num)  # Position is 0-based

print("Updated array:", arr)  # Display the array
```

```Python
import numpy as np

# Initial array
arr = np.array([1, 2, 3, 4, 5])

# Input the element to be inserted and the position
num = int(input("Enter the number to be inserted: "))
pos = int(input("Enter the position at which the number is to be added: "))

# Insert the element at the specified position
arr = np.insert(arr, pos, num)  # `np.insert` returns a new array

print("Updated array:", arr)  # Display the array
```

## Deleting an Element in the Array
**At the End**  
```Python
# Initial array
arr = [1, 2, 3, 4, 5]

# Deleting the last element
if arr:  # Check if the array is not empty
    arr.pop()  # Removes the last element

print("Updated array:", arr)  # Output: [1, 2, 3, 4]
```

```Python
import numpy as np

# Initial array
arr = np.array([1, 2, 3, 4, 5])

# Deleting the last element
if arr.size > 0:  # Check if the array is not empty
    arr = np.delete(arr, -1)  # Deletes the last element

print("Updated array:", arr)  # Output: [1 2 3 4]
```

**At Any Other Position**  
```Python
# Initial array
arr = [1, 2, 3, 4, 5]

# Input the position of the element to delete
pos = int(input("Enter the position where the number has to be deleted: "))

# Deleting the element at the specified position
if 0 <= pos < len(arr):  # Check if the position is valid
    arr.pop(pos)  # Removes the element at the specified position

print("Updated array:", arr)  # Example Output: [1, 3, 4, 5]
```

```Python
import numpy as np

# Initial array
arr = np.array([1, 2, 3, 4, 5])

# Input the position of the element to delete
pos = int(input("Enter the position where the number has to be deleted: "))

# Deleting the element at the specified position
if 0 <= pos < arr.size:  # Check if the position is valid
    arr = np.delete(arr, pos)  # Deletes the element at the specified position

print("Updated array:", arr)  # Example Output: [1 3 4 5]
```

# Multi-Dimensional Array
The elements in multi-dimentional arrays are accessed using multiple indices.

**Two-Dimensional Array**
```Python
import numpy as np

# Declaring a 2D array
arr = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

# Accessing elements
print(arr[0, 1])  # Output: 2 (row 0, column 1)
print(arr[2, 2])  # Output: 9 (row 2, column 2)
```

**Three-Dimensional Array**
```Python
# 3D array with dimensions 3x3x3
arr = [
    [  # Layer 0
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ],
    [  # Layer 1
        [10, 11, 12],
        [13, 14, 15],
        [16, 17, 18]
    ],
    [  # Layer 2
        [19, 20, 21],
        [22, 23, 24],
        [25, 26, 27]
    ]
]

# Accessing an element (Layer 1, Row 2, Column 3; 0-based indexing)
print(arr[1][1][2])  # Output: 15
```

```Python
import numpy as np

# 3D array with dimensions 3x3x3
arr = np.array([
    [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ],
    [
        [10, 11, 12],
        [13, 14, 15],
        [16, 17, 18]
    ],
    [
        [19, 20, 21],
        [22, 23, 24],
        [25, 26, 27]
    ]
])

# Accessing an element (Layer 1, Row 2, Column 3; 0-based indexing)
print(arr[1, 1, 2])  # Output: 15
```
# Time Complexity of Arrays
**Access**: constant O(1)  
**Search**: O(n) (assume linear search), O(log n) (assume binary search and sorted)  
**Insertion**: O(n)  
**Deletion**: O(n)  
**Space Required**: O(n)

# Advantages of Arrays
- Arrays allow for **random access** of elements. Each element in the array can be interacted with by directly accessing to its index.
- Arrays have **good cache locality**, which means the speed of execution of code may be significantly faster in some cases due to nature how arrays are stored.

# Disadvantages of Arrays
- Insertion and deletion of elements in the array so that it maintains a continuous order may be expensive, as one may have to relocate all the elements.