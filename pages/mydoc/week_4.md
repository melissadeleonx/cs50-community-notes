---
title: CS50 Week 4 - Memory and its computer programming role
tags: [getting_started, troubleshooting]
keywords:
summary: " Memory is used to hold both program instructions and the data manipulated by these instructions during program execution."
sidebar: mydoc_sidebar
permalink: week_4
folder: mydoc
---

**Memory**, in the context of computer programming and computer science, refers to the electronic storage space that a computer uses to store and retrieve data. It is a fundamental component of a computer system and is crucial for the execution of programs.

## Memory Management

Memory is used to hold both program instructions and the data manipulated by these instructions during program execution.

**Here's a more detailed breakdown:**

* **Program Instructions** - Memory stores the machine code instructions that make up a computer program. These instructions are executed sequentially by the computer's central processing unit (CPU).

* **Data Storage** - Memory is used to store data that programs work with. This data can include variables, arrays, structures, and other types of information necessary for program execution.

* **Variable Storage** - Variables in a program are allocated memory to hold their values. The type of variable (int, char, float, etc.) determines the size of the allocated memory.

* **Dynamic Memory Allocation** - In languages like C, memory can be dynamically allocated at runtime using functions like malloc. This allows programs to request and release memory as needed during execution.

* **Memory Addresses** - Each byte of memory has a unique address, which is used to identify and access that specific location. Memory addresses are essential for working with pointers and dynamic memory allocation.

* **Pointers and Memory Access** - Pointers are variables that store memory addresses. They allow direct manipulation of memory contents, enabling dynamic memory allocation and efficient data access.

* **Memory Management** - Proper memory management involves allocating memory when needed and releasing it when it's no longer required. In languages like C, the responsibility for memory management lies with the programmer.

* **Memory Safety** - Ensuring memory safety involves preventing common issues like buffer overflows, dangling pointers, and memory leaks. These issues can lead to program crashes or security vulnerabilities.

* **Memory Layout** - The layout of memory is crucial for understanding how data is stored. Arrays, structures, and other data types have specific memory layouts that impact program efficiency and performance.

* **Stack and Heap** - Memory is often divided into the stack and heap. The stack is used for function calls, local variables, and managing program flow. The heap is used for dynamic memory allocation.

## Hexadecimal Representation in Programming

**Hexadecimal**, a base-16 number system, plays a crucial role in computer programming, providing a concise and human-readable representation of binary data and memory addresses. Understanding hexadecimal is essential for efficient memory management and manipulation.
- It uses digits 0-9 and additional characters a-f (or A-F) to represent values from 0 to 15.

**Key Points**
- **Correspondence with Binary**: Hexadecimal has a direct correspondence with binary, with each hexadecimal digit representing a unique arrangement of 4 binary digits. This simplifies the representation of binary data, making it more readable for programmers.    

- **Place Values and Prefixing**: Similar to decimal and binary, hexadecimal has place values, but these are powers of 16. Hexadecimal numbers are often prefixed with "0x" to distinguish them from decimal numbers.
- **Memory Address Representation**: Memory addresses in computer systems are commonly expressed in hexadecimal. Programmers need to interpret and manipulate these addresses efficiently.
- **Binary to Hexadecimal Conversion**: A practical skill involves converting binary numbers to hexadecimal. Grouping binary digits into sets of 4 and translating each group to hexadecimal simplifies the process.
- **Practical Use in Programming**: Hexadecimal is extensively used in programming, especially for representing memory addresses and binary data. Its concise nature makes it valuable for expressing otherwise cumbersome binary information.

**Example Code:**
```c
    #include <stdio.h>

    int main() {
        // Binary to Hexadecimal Conversion
        unsigned int binaryNumber = 0b1101101010110101;  // Binary literal in C
        printf("Binary: %X\n", binaryNumber);  // %X format specifier for hexadecimal output

        // Memory Address Representation
        int *ptr = malloc(sizeof(int));
        printf("Memory Address: %p\n", (void *)ptr);  // %p format specifier for memory address

        free(ptr);  // Free dynamically allocated memory
        return 0;
    }
```
{% include note.html content="Mastering **hexadecimal** is crucial for efficient memory management, understanding memory addresses, and representing binary data concisely." %}

## Pointers in C

**Pointers** are a powerful but potentially challenging concept in C programming. They allow direct manipulation of memory addresses, providing a unique way to work with variables and data.

### Pointer Basics

1. **What Are Pointers?**
- Pointers are memory addresses, indicating the location where variables or data reside.
- Syntax: `int *p;` declares a pointer `p` to an integer.

2. **Null Pointer**
- The null pointer (`NULL`) points to nothing.
- It's essential to initialize pointers, and if not set to a meaningful value, set them to `NULL` to avoid unintended consequences.

3. **Address Extraction**
- The `&` operator extracts the address of a variable.
- Example: `int *px = &x;` assigns the address of the integer variable `x` to the pointer `px`.

### Arrays and Pointers

1. **Arrays as Pointers**
- The name of an array is essentially a pointer to its first element.
- Example: `int arr[5]; int *pArr = arr;` where `pArr` is a pointer to the first element of arr.

2. **Pointer Arithmetic**
- Pointer arithmetic allows navigation through array elements using addition and subtraction.
- Example: `*(pArr + 2)` refers to the third element of the array.

### Dereferencing

1. **Dereference Operator (*)**
- The `*` operator is used for dereferencing, accessing the data at the memory location pointed to by a pointer.
- Example: `*p = 35;` changes the value at the address pointed to by `p`.

2. **Changing Variable Values**
- Dereferencing allows direct manipulation of the data at a specific memory address.
- Example: `*pk = 35;` is equivalent to `k = 35;` if `pk` points to the address of `k`.

### Memory Basics

1. **RAM and Storage**
- Computer memory includes RAM and storage.
- RAM is volatile, and data is lost when the system is powered off.

2. **Memory Addresses**
- Memory is viewed as an array of byte-sized cells, each with a unique address.
- Variables are stored in specific memory locations.

3. **Variable Creation and Memory Allocation**
- Variables are assigned memory addresses upon creation.
- Memory is allocated based on the size of the data type.

### Practical Use of Pointers

1. **Passing Data Between Functions**
- Pointers enable passing variables between functions without creating copies.
- Changes made through pointers affect the original variables.

2. **Pointer Discipline**
- Emphasizes responsible use of pointers to avoid unintended consequences.
- Setting pointers to `NULL` when not immediately assigned meaningful values is good practice.

{% include note.html content="While syntax of **Pointers** may be challenging, the benefits of efficient memory management and direct data manipulation make them essential for experienced programmers." %}

## Typedef - Defining Custom Types

**Structures** allow us to create custom data types, but their usage can sometimes be cumbersome due to the need for the `struct` keyword. To address this, C provides a solution called `typedef`, enabling the creation of shorter, more convenient names for data types.

### Basics of Typedef
The basic syntax of `typedef` is simple: `typedef old_type new_type;`. This means we can create an alias (`new_type`) for an existing data type (`old_type`), making our code more readable and concise.

**Example Code**

```c
    typedef unsigned char byte;
    byte myByte = 0xFF;
```
In this example, `byte` becomes a stand-in for `unsigned char`, allowing us to use the more straightforward `byte` in our code.

### CS50 Library Example
Consider CS50's library, where `typedef char* string;` is used. This simplifies the complex concept of strings, which are essentially arrays of characters represented by pointers. Now, instead of dealing with `char*`, we can use the more intuitive `string`.

### Typedef with Structures
Structures often have long type names, making variable declarations verbose. typedef becomes especially useful when working with structures.

**Typedef after Structure Definition**
```c
    struct car {
        // Fields
    };
    typedef struct car car_t;
```
Here, we define a structure named `car` and then create a shorter alias (`car_t`) using `typedef`. Now, whenever we want to declare a variable of this structure, we can use `car_t` instead of `struct car`.

**Typedef within Structure Definition**
```c
    typedef struct car {
        // Fields
    } car_t;
```
Alternatively, we can define and name the structure simultaneously using `typedef`. This creates a more concise alias (`car_t`), reducing the length of our code.

### Putting it All Together

```c
    typedef unsigned char byte;
    typedef int age_t;

    typedef struct {
        int hours;
        int minutes;
    } time_t;

    typedef struct car {
        char make[20];
        int year;
    } car_t;

    int main() {
        // Using typedef for basic types
        byte data = 0xFF;
        age_t myAge = 25;

        // Using typedef with structures
        time_t currentTime = {12, 30};
        car_t myCar = {"Toyota", 2022};

        return 0;
    }
```

{% include note.html content="**`typedef`** in C is a powerful tool that simplifies code by providing more convenient names for both basic and custom data types. Its usage is particularly beneficial when working with structures, as it reduces the verbosity of variable declarations." %}

## Dynamic Memory Allocation

**Dynamic memory allocation** is a crucial concept for managing memory during program execution. Unlike static memory allocation, which is determined at compile time, dynamic memory allocation allows us to allocate memory at runtime. This is particularly useful when the size of memory needed is not known until the program is running.

**A solid understanding of pointers is essential to understand dynamic memory allocation better.*

### Memory Regions: Stack vs. Heap
- Memory in C is managed through two primary regions: the **stack** and the **heap**.
- The **stack** is used for statically allocated memory (e.g., variables with fixed sizes), 
- While the **heap** facilitates dynamic memory allocation.

### The 'malloc' Function
- To allocate memory from the heap, we use the `malloc` function, which is part of the `<stdlib.h>` library.
- Syntax: `malloc(size)`, where `size` represents the number of bytes to allocate.
- It returns a pointer to the allocated memory.
- **Example: Allocating an Integer**

```c
    int* ptr = (int*)malloc(sizeof(int)); // Allocates memory for an integer
```

### Checking for NULL
- The `malloc` function may return `NULL` if it fails to allocate memory.
- Always check for `NULL` to avoid dereferencing a null pointer.
- **Example: Checking for Allocation Failure**

```c
    int* ptr = (int*)malloc(sizeof(int));
    if (ptr == NULL) {
        // Handle allocation failure
        exit(1);
    }
```

### Dynamic Array Allocation
- Allocating an array of floats on the heap.
- **Example: Allocating an Array of Floats**

```c
    float* floatArray = (float*)malloc(50 * sizeof(float));
```
### Memory Deallocation: The 'free' Function
- Dynamically allocated memory must be freed to prevent memory leaks.
- Use the free function to release memory back to the system.
- **Example: Freeing Dynamically Allocated Memory**

```c
    float* floatArray = (float*)malloc(50 * sizeof(float));
    // Use floatArray
    free(floatArray); // Release memory when done
```

**Three Important Rules**
1. Free All Allocated Memory: Dynamically allocated memory must be explicitly freed before the program terminates.
2. Only Free Dynamically Allocated Memory: Memory allocated with malloc should be freed; statically allocated memory is handled by the system.
3. Avoid Double Free: Ensure that the same block of memory is not freed more than once to prevent errors.

### Visualizing Dynamic Memory Allocation

Let's illustrate dynamic memory allocation through a simple example.
```c
    int m;            // Statically declared integer
    int* a;           // Statically declared pointer
    int* b = malloc(sizeof(int));  // Dynamically allocated integer
    a = &m;           // a points to m
    a = b;            // a and b point to the same location
    *m = 10;          // Assigning a value to m
    *b = *m + 2;      // Modifying the dynamically allocated memory
    free(b);          // Freeing dynamically allocated memory
    *a = 11;          // Accessing freed memory (undefined behavior)
```



{% include note.html content="**Dynamic memory allocation** in C provides flexibility for handling varying memory needs during program execution. However, it requires careful management to avoid memory leaks and undefined behavior. Adhering to the rules of allocating and freeing memory is essential." %}

## Call Stacks

The **call stack** is a mechanism in programming that manages the flow of function calls. It keeps track of the functions that are currently being executed and the order in which they were called.

### How Call Stack Works

1. **Function Call:** When a function is called, a stack frame (also known as a function frame) is created, allocating memory for local variables and bookkeeping information.
2. **Stack Structure:** These frames are organized in a stack structure, with the most recently called function at the top (active frame).
3. **Function Execution:** The function at the top of the stack (active frame) is the one currently executing, while the others are in a waiting state.
4. **New Function Call:** If a function calls another function, a new frame is pushed onto the top of the stack, becoming the new active frame.
5. **Return from Function:** When a function completes its execution, either by reaching the end or encountering a return statement, its frame is popped off the stack.
6. **Resumption:** The function frame below (if any) becomes the new active frame, and execution resumes from where it left off.

### Visualization with Factorial Example

Let's use the factorial function as an example to illustrate the call stack:

```c
    #include <stdio.h>

    int fact(int n) {
        if (n == 1) {
            return 1;
        } else {
            return n * fact(n - 1);
        }
    }

    int main() {
        printf("%d\n", fact(5));
        return 0;
    }
```

### Call Stack Steps
1. **main Function Call:** `main` is called and prints the result of `fact(5)`.
2. **fact(5) Frame:** A frame for `fact(5)` is pushed onto the stack, leading to subsequent function calls.
3. **Recursive Calls:** `fact(5)` calls `fact(4)`, which calls `fact(3)`, and so on, each pushing a new frame onto the stack.
4. **Base Case Reached:** When `fact(1)` is reached, it returns 1, leading to the destruction of its frame.
5. **Return Values Propagate:** Each function frame returns a value, leading to the destruction of its frame and the resumption of the calling frame.
6. **printf Execution:** Finally, the result of `fact(5)` is printed by printf.

This process continues until all frames are popped off the stack, and the program completes its execution.

{% include note.html content="Understanding the **call stack** is crucial for comprehending how functions interact and how recursion operates in programming. It provides a clear structure for managing function calls and their associated data." %}

## File Pointers in C: Understanding File Input/Output

Most programs are ephemeral, leaving no evidence after execution. It means that most programs, after execution, do not leave a lasting trace or evidence. Once the program completes its task and exits, its impact is temporary, and there might be no visible evidence or persistence of its execution on the system.
 
**C provides file structures** to store persistent data—information that exists after program execution.
**File pointers** are crucial for file I/O operations, allowing interaction with files.

### Basic File Operations

#### fopen: Opening a File
- **FILE* fopen(const char* filename, const char* mode);**
- Opens a file and returns a file pointer.
- The mode parameter specifies the file operation (e.g., read, write, append).
- Example: FILE* filePtr = fopen("file.txt", "r");
- Common modes:
    * "r": Read
    * "w": Write (creates a new file or truncates an existing file)
    * "a": Append (write to the end of the file)

#### fclose: Closing a File
- **int fclose(FILE* stream);**
- Closes the file associated with the given file pointer.
- Ensures no further I/O operations on the closed file.
- Example: fclose(filePtr);

### Reading Characters from a File

#### fgetc: Reading a Character
- **int fgetc(FILE* stream);**
- Reads the next character from the file.
- Returns the character read or EOF (End of File) if the end is reached.
- Example: char ch = fgetc(filePtr);

#### Looping Through Characters
- By looping through fgetc calls until EOF, entire file content can be read.
- Example:
    ```c
        while ((ch = fgetc(filePtr)) != EOF) {
        printf("%c", ch);
        }
    ```

### Writing Characters to a File

#### **fputc: Writing a Character**
- **int fputc(int character, FILE* stream);**
- Writes the character to the file.
- Example: fputc('A', filePtr);

#### Copying Files (cp Command)
- Combining fgetc and fputc to replicate the Linux cp command.
- Reading from one file and writing to another until EOF is reached.

### Advanced File I/O: fread and fwrite

#### fread: Reading Arbitrary Data
- size_t fread(void* ptr, size_t size, size_t count, FILE* stream);
- Reads a specified amount of data from the file.
- Example: fread(arr, sizeof(int), 10, filePtr);
- Parameters:
    * ptr: Pointer to the memory location where data will be stored.
    * size: Size of each unit of data to be read.
    * count: Number of units to be read.
    * stream: File pointer.

#### fwrite: Writing Arbitrary Data
- size_t fwrite(const void* ptr, size_t size, size_t count, FILE* stream);
- Writes a specified amount of data to the file.
- Example: fwrite(arr, sizeof(int), 10, filePtr);

#### Handling Dynamic Memory
- Dynamic allocation of memory using malloc to read/write larger chunks of data.
- Example: fread(arr, sizeof(double), 80, filePtr);

### Additional File I/O Functions
#### Other Useful Functions
- fgets and fputs: Reading/writing strings from/to a file.
- fprintf: Using printf-style formatting to write to a file.
- fseek and ftell: Moving to a specific position and getting the current position in a file.
- feof: Detecting the end of a file.
- ferror: Checking for errors during file operations.

### Handling Errors and Seeking
#### Error Handling: ferror
- int ferror(FILE* stream);
- Checks if an error has occurred during file operations.
- Returns a non-zero value if an error is detected.
- Example: if (ferror(filePtr)) { /* handle error */ }

#### Moving File Position: fseek and ftell
- int fseek(FILE* stream, long int offset, int origin);
- Moves the file position indicator to a specified location.
- Example: fseek(filePtr, 0, SEEK_SET); (Sets the position to the beginning of the file)
- long int ftell(FILE* stream);
- Returns the current position of the file position indicator.
- Example: long int currentPosition = ftell(filePtr);

