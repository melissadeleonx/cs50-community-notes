---
title: CS50 Week 6 - Introduction to Python
tags: [getting_started, troubleshooting]
keywords:
summary: "Python is a high-level, general-purpose programming language known for its simplicity and readability. It is widely used for various applications, including web development, data science, artificial intelligence, and more."
sidebar: mydoc_sidebar
permalink: week_6
folder: mydoc
---

**Python** is a widely used modern programming language, currently ranking among the top five or six in popularity. It has been in existence for over 25 years and is known for its versatility and ease of use. While this introduction won't cover Python as extensively as the previous discussions on C, the goal is to provide an overview of the language's tools and capabilities.

## Python's Role
Python serves as a powerful language, particularly for simplifying complex operations that might be challenging in languages like C. It excels in string manipulation, networking, and is generally considered a versatile utility language capable of handling various tasks. Presently, Python is highly favored among data scientists for processing large datasets, generating graphs, charts, and obtaining results.

### Syntax and Style
Python draws inspiration from C, resulting in some similarities in syntax. Although the appearance might differ, Python maintains a consistent look and feel. Notable differences include the absence of as many curly braces as seen in C, but the style lessons learned in C remain applicable.

### Writing Python Files
Creating a Python file is straightforward. Open a file with the ".py" extension in CS50 IDE, and it will automatically provide syntax highlighting, indicating whether the code is valid Python. Unlike C, Python is not necessarily a compiled language. Python programs can be run in a Python interpreter, allowing code execution line by line.

## Python Basics - Variables and Control Flow

Let's delve into some basic concepts in C and explore their Python equivalents:

### Variables in Python
Variables in Python exhibit two notable differences from C. Firstly, there's no need to explicitly specify a data type, adding flexibility to the language. Secondly, variables must be initialized upon declaration, eliminating the option to declare a variable without assigning a value. For instance, in C, we might declare int x; and later assign a value, whereas in Python, x = 54 initializes and assigns the value simultaneously. Notably, Python statements do not require semicolons, enhancing code readability. 

```python
# Example in Python
x = 54
phrase = "This is CS50"
```

### Comments in Python
Comments in Python start with the hash symbol (#) and extend to the end of the line. They are essential for adding context to code, explaining functionality, or leaving notes for future reference.

### Printing Output
To display output in Python, you can use the `print()` function. It allows you to output variables, strings, or the result of expressions. By default, `print()` ends with a newline character, but you can change this behavior using the `end` parameter.

```python
# Printing output in Python
print("Hello, world!")
x = 10
print("The value of x is:", x)
```

## Basic Data Types
Python supports various data types, including integers, floats, strings, and booleans. Unlike some other languages, Python handles the allocation of memory for variables dynamically.

## Basic Arithmetic Operations
Python supports standard arithmetic operations, including addition (+), subtraction (-), multiplication (*), division (/), and exponentiation (**). The order of operations follows standard mathematical rules.

```python
# Arithmetic operations in Python
result = 10 + 5  # Addition
result = 10 - 5  # Subtraction
result = 10 * 5  # Multiplication
result = 10 / 5  # Division
result = 10 ** 2  # Exponentiation
```

### Control Flow - Conditionals
Python uses indentation to denote blocks of code, rather than curly braces. This indentation is crucial for determining the scope of conditional statements, loops, and functions. Python supports the standard if-else conditional structure.

```python
# Conditional statement in Python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is less than or equal to 5")
```

### Control Flow - Loops
Python provides two main types of loops: for and while. for loops are used for iterating over a sequence (such as a list, tuple, or string), while while loops continue iterating until a condition becomes false.

```python
# Loop example in Python
for i in range(5):
    print(i)  # Prints numbers from 0 to 4

while x > 0:
    print(x)
    x -= 1
```
## Data Structures
In Python, data structures are used to store and organize data in a structured manner, facilitating efficient manipulation, retrieval, and management of information. Python offers several built-in data structures, each designed to serve specific purposes and cater to different requirements. Some of the commonly used data structures in Python include lists, tuples, dictionaries, sets, and more.

### Lists
Lists are ordered collections of items, allowing for the storage of heterogeneous data types within the same list. They are mutable, meaning their elements can be modified after creation. Lists are denoted by square brackets [ ].

#### Creating and Accessing Lists
* **Creating a List:** A list is a mutable sequence in Python, created using square brackets. It can hold elements of different data types.
```python
my_list = [1, 2, 3, 'a', 'b', 'c', 'banana', 'banana']
```
* **Indexing:** Accessing elements by index.
```python
print("Element at index 0:", my_list[0])  # Output: 1
print("Element at index 3:", my_list[3]) # Output: a

print(my_list.index('b')) # Output: 4
```
* **Slicing:** Getting a sublist.
```python
print("Sublist from index 2 to 4:", my_list[2:5]) # Output: Sublist from index 2 to 4: [3, 'a', 'b']
```
#### Modifying Lists
* **Appending:** Adding elements to the end of the list.
```python
my_list.append('d')
print(my_list) # Output: [1, 2, 3, 'a', 'b', 'c', 'banana', 'banana', 'd']
```
* **Inserting:** Inserting elements at specific positions. The insert() method takes two arguments: the index at which to insert the element and the element itself. 
my_list.insert(3, 4)
```python
my_list.insert(3, 4)  # Inserts the value 4 at index 3 in the list
print(my_list)  # Output: [1, 2, 3, 4, 'a', 'b', 'c', 'banana', 'banana', 'd']

my_list.insert(4, 'z')
print("The new list:", my_list) # Output: The new list: [1, 2, 3, 4, 'z', 'a', 'b', 'c', 'banana', 'banana', 'd', 'e']
```

* **Removing:** Removing elements by value or index.
```python
my_list.remove(3)  # Removes the first occurrence of '3' from the list
print(my_list)  # Output: [1, 2, 4, 'a', 'b', 'c', 'banana', 'banana', 'd']

# Deleting by index, we can use the method del or pop()
del my_list[3]    # Deletes the element at index 3 from the list
print(my_list)  # Output: [1, 2, 4, 'b', 'c', 'banana', 'banana', 'd']

my_list.pop(4)
print(my_list) # Output: [1, 2, 4, 'a', 'c', 'banana', 'banana', 'd', 'e']
```
#### List Manipulation and Properties

* **Length:** Getting the length of the list using `len`.
```python
print("Length of the list:", len(my_list)) # Output: Length of the list: 9
```

* **Iterating:** Looping through elements of the list.
```python
my_list = [1, 2, 3, 4, 5]
for item in my_list:
    print(item) #Output: This would print each element of my_list on a new line.
```
* **Checking Membership:** Checking if an element exists in the list. To check if an element exists in a list, you can use the `in` operator. 
```python
my_list = ['a', 'b', 'c']
print("Is 'b' in the list?", 'b' in my_list)  # Output: Is 'b' in the list? True
print('z' in my_list)  # Output: False
```

#### List Methods and Functions
* **Counting Occurrences:** Counting occurrences of a specific value.
```python
my_list = ['banana', 'apple', 'banana', 'orange']
print(my_list.count('banana'))  # Output: 2
```

* **Sorting:** Sorting the list in ascending order
```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5]
my_list.sort()
print(my_list)  # Output: [1, 1, 2, 3, 4, 5, 5, 6, 9]
```
* **Reversing:** Reversing the elements of the list.
```python
my_list = [1, 2, 3, 4, 5]
my_list.reverse()
print(my_list)  # Output: [5, 4, 3, 2, 1]
```

#### Advanced List Operations
* **List Comprehensions:** Creating lists using concise expressions. They allow you to generate a new list by applying an expression to each item in an existing iterable.
```python
squares = [x**2 for x in range(5)]  # Output: [0, 1, 4, 9, 16]

even_numbers = [x for x in range(10) if x % 2 == 0]  # Output: [0, 2, 4, 6, 8]
```

* **String Manipulation:** List comprehensions can also be used to manipulate strings.
```python
string = 'hello'
uppercase_letters = [letter.upper() for letter in string]  # Output: ['H', 'E', 'L', 'L', 'O']
```
* **Filtering Elements in a List:** You can filter elements in a list based on certain conditions using list comprehensions. 
```python
sentence = 'My love for you is eternal and powerful for you are my everything'
words_with_greater_than_6 = [word for word in sentence.split() if len(word) > 6]
# Output: ['eternal', 'powerful', 'everything']
```

* **Nested Lists:** Lists can contain other lists as elements, creating nested data structures. They can be used to represent multi-dimensional data or hierarchical structures.

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# Accessing elements within the nested list:
print(matrix[0][0])  # Output: 1 (accessing the first element of the first inner list)
print(matrix[1][2])  # Output: 6 (accessing the third element of the second inner list)

# Modifying elements within the nested list:
matrix[2][1] = 10
print(matrix) 
# Output:
# [[1, 2, 3], [4, 5, 6], [7, 10, 9]]
```
* **Mutability:** Lists are mutable, meaning their elements can be modified after creation.

### Tuples










