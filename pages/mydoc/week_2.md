---
title: CS50 Week 2 - Arrays and the Fundamentals of C
tags: [getting_started, troubleshooting]
keywords:
summary: ""
sidebar: mydoc_sidebar
permalink: week_2
folder: mydoc
---

## Functions in C

**Functions** are like black boxes with inputs and a single output. They help manage complexity and enable code organization. Functions can be synonymous with procedures or methods in other languages.

A `function` processes inputs to produce a single output. For example, "add" takes integers a, b, and c, producing the sum (a+b+c). Functions act as black boxes, and we often don't need to know their internal workings.
- Organization: Functions break down complex problems into manageable parts.
- Simplification: Easier debugging and coding with smaller, focused functions.
- Reuse: Functions can be recycled and used across different programs.

### Function Declaration

In a program, function declarations inform the compiler about the existence and structure of the function before its actual definition. It allows the compiler to understand how the function should be used.

Here is the usual syntax:
```c
    return_type function_name(data_type parameter1, data_type parameter2, ...);
``` 
Breaking down the syntax, examine each pieces of codes.
- **return_type**: Specifies the type of data that the function will return.
- **function_name**: A unique identifier for the function.
- **data_type parameter1, data_type parameter2, ...**: Input parameters with their data types.

A sample code to understand better:

```c
    int add(int a, int b);
``` 
Typically in C programming, **function declarations** are placed before the `main` function. This allows the compiler to be aware of the existence and signature of the functions before they are actually used in the main function or other parts of the program.

### Function Definition

**Function Definition** provides the actual implementation of the function. It includes the function body, where the logic is written, and a return statement specifying what the function will output.

Here is the usual syntax:
```c
    return_type function_name(data_type parameter1, data_type parameter2, ...) {
        // Function body - implementation of the function
        // Return statement to specify the output
    }
``` 
A sample code to understand better:
```c
    int add(int a, int b) {
        return a + b;
    }
``` 

### Calling Functions

In the `main` program, **functions are called** by providing the required arguments. The return value can be stored in a variable for further use or directly used in expressions. These concepts form the basis for structuring and organizing code in C. They help in creating modular and reusable components, promoting better code maintenance and readability. 

Here is the usual syntax:
```c
    return_type result = function_name(argument1, argument2, ...);
```

- return_type: The data type expected as the output of the function.
- result: A variable to store the output.
- function_name: The name of the function to be called.
- argument1, argument2, ...: Values passed to the function as inputs.

A sample code to understand better:

```c
    int sum = add(3, 5);
``` 

{% include note.html content="Give functions clear, meaningful names for better understanding. Document functions well for yourself and others using them" %}

### Parameters and Return Types:

Functions often work with data, both taking inputs **(parameters)** and producing outputs **(return types)**. Let's explore the concepts of parameters and return types in more detail:

**Parameters** are the inputs that a function receives and utilizes during its execution. They are declared in the function declaration and used in the function definition.

Here is the usual syntax:
```c
    return_type function_name(data_type parameter1, data_type parameter2, ...) {
    // Function body using parameters
    // ...
    }
``` 
A sample code to understand better:
```c
    void printSum(int a, int b) {
        printf("Sum: %d\n", a + b);
    }
``` 
In this example, `int a` and `int b` are parameters, and the function `printSum` takes two integers as inputs.

**Return Type** specifies the data type of the value that a function will produce as output. It is declared in the function declaration and used in the function definition.

Here is the usual syntax:
```c
    return_type function_name(data_type parameter1, data_type parameter2, ...) {
        // Function body
        // ...
        return result; // Returning a value of type 'return_type'
    }
``` 
A sample code to understand better:
```c
    int add(int a, int b) {
        return a + b;
    }
``` 
Here, `int` is the return type, indicating that the `add` function will produce an integer result.

### Practice Problem: Valid Triangle

Consider the valid_triangle function that determines if three given side lengths can form a valid triangle:
```c
    bool valid_triangle(float x, float y, float z) {
        if (x <= 0 || y <= 0 || z <= 0) {
            return false; // sides must be positive
        }
        if (x + y <= z || x + z <= y || y + z <= x) {
            return false; // sum of any two sides must be greater than the third
        }
        return true;
    }
``` 
- The function takes three parameters of type float representing side lengths.
- It returns a boolean value (bool), indicating whether the given sides can form a valid triangle.
- The logic inside the function checks two conditions: sides must be positive, and the sum of any two sides must be greater than the third.

This practice problem demonstrates the use of parameters (x, y, and z) and a return type (bool) in a function to solve a specific task. Understanding these concepts is crucial for effective function implementation and usage in C programming.

## Variable Scope

As we learn more about functions in C programming, understanding variable scope becomes crucial. Scope refers to the characteristic of a variable that defines from which functions that variable can be accessed. There are primarily two types of variable scopes in C: **local variables** and **global variables**.

### Local Variables

**Local variables** can only be accessed within the functions in which they are created. Limited to the function where they are declared; other functions in the program cannot access them.
- Local variables are typically "passed by value" when used in function calls.
- When a function is called, it receives its own copy of the variable, not the actual variable itself.
- Changes made to the local variable within the function do not affect the original variable in the calling function.

Local Variables Example:
```c
    #include <stdio.h>

    // Function declaration
    void triple(int x);

    int main() {
        // Local variable x in main
        int x = 5;

        // Call function triple with local variable x
        triple(x);

        // Print the value of x in main
        printf("Value of x in main: %d\n", x);

        return 0;
    }

    // Function definition
    void triple(int x) {
        // Local variable x in triple
        x = x * 3;
        printf("Value of x in triple: %d\n", x);
    }
``` 
**Output**
- Value of x in triple: 15
- Value of x in main: 5

In this example, the local variable `x` in the `main` function is not affected by the changes made to the local variable `x` in the `triple` function. Each function works with its own copy of the variable.

### Global Variables

**Global variables** can be accessed by any function in the program. They are declared outside of any particular function.
- Global variables provide flexibility for information sharing among functions.
- However, caution is needed, as changes to a global variable by one function can have unintended consequences for other functions.
- Collaborative coding efforts may introduce naming conflicts when multiple functions use the same variable names.

Global Variables Example:
```c
    #include <stdio.h>

    // Global variable
    float global = 0.5050;

    // Function declaration
    void tripleGlobal();

    int main() {
        // Call function tripleGlobal
        tripleGlobal();

        // Print the value of global in main
        printf("Value of global in main: %.2f\n", global);

        return 0;
    }

    // Function definition
    void tripleGlobal() {
        // Access and modify the global variable
        global = global * 3;
        printf("Value of global in tripleGlobal: %.2f\n", global);
    }

```
**Output**
- Value of global in tripleGlobal: 1.52
- Value of global in main: 1.52

In this example, the global variable global is accessible and modifiable by both the main function and the tripleGlobal function. Changes made to global in one function affect its value for other functions.

## Debugging C Programs

**Debugging** is the process of identifying, isolating, and fixing errors or bugs within a computer program. It is a crucial and iterative part of software development that aims to ensure the correct functionality of the code. Debugging involves investigating the program's behavior, identifying discrepancies between expected and actual outcomes, and resolving issues to produce a reliable and error-free application.

### Key Components of Debugging

1. **Bug Identification**: The first step in debugging is recognizing the existence of a bug or error in the code. Bugs can manifest as unexpected behavior, program crashes, or incorrect output.

2. **Error Isolation**: Once a bug is identified, the next step is to isolate the error. This involves determining the specific section of code or the sequence of operations that leads to the undesired behavior.

3. **Root Cause Analysis**: Understanding the root cause of the bug is essential. It involves tracing the execution flow, inspecting variable values, and analyzing the code logic to identify why the error occurs.

4. **Code Modification**: After identifying the root cause, developers modify the code to correct the error. This may involve fixing syntax errors, adjusting logic, or addressing issues related to data flow or memory management.

5. **Testing and Verification**: After making changes, the program is tested again to ensure that the bug has been successfully addressed. Testing involves running the program with various inputs to validate its correctness.

6. **Iterative Process**: Debugging is often an iterative process. Developers may need to go through multiple cycles of identification, isolation, and modification to address all bugs in the code.

### Debugging Tools

- **Print Statements**: Inserting print statements (e.g., printf in C) at strategic points in the code to output variable values and messages for diagnostic purposes.
- **Interactive Debuggers**: Using interactive debuggers, such as `gdb` (GNU Debugger) in C, that allow developers to pause program execution, inspect variables, and step through code line by line.
- **Logging**: Incorporating logging mechanisms to record program events, errors, and variable values during runtime.
- **Memory Analyzers**: Tools like Valgrind help identify memory-related issues, such as memory leaks or invalid memory access.
- **Version Control**: Regularly commit your code using version control systems like Git. This allows you to revert to a working state if needed.
- **Read Documentation**: Understand the functions and libraries you are using. Misuse or misunderstanding of functions can lead to subtle bugs.
- **Peer Review**: Have colleagues or peers review your code. Fresh eyes may catch issues that you've overlooked.
- **Rubber Duck Debugging**: Explaining your code or problem to someone else (or even an inanimate object) can help you see the issue from a different perspective.
- **debug50 (CS50 Debugger)**: debug50 is a debugger specifically designed for the CS50 IDE, an environment used in the CS50 course. IDEs often provide debugging features, allowing developers to set breakpoints, inspect variables, and navigate through the code seamlessly.

### How to use debug50?

The CS50 IDE provides a helpful tool called `debug50`, it is tailored for the CS50 environment. Here are different techniques to use.

1. **Conditional Breakpoints** - sometimes, you may want to break execution only when a certain condition is met. In `debug50`, you can set conditional breakpoints to pause the program when a specific variable reaches a particular value.
<i>How to Use:</i> Right-click on a breakpoint, choose "Edit Breakpoint," and set the condition.
2. **Watchpoints** are useful for tracking changes to a variable. If the value of the watched variable changes, the program pauses.
<i>How to Use:</i> In `debug50`, right-click on a variable, choose "Watch Variable," and observe its behavior during execution.
3. **Backtrace (Call Stack)** - when dealing with complex programs or function calls, understanding the call stack is crucial. It helps identify the sequence of function calls that led to the current point in the code.
<i>How to Use:</i> In `debug50`, use the backtrace command to see the call stack. Type bt or backtrace in the debugger prompt.
4. **Memory Inspection** - inspecting memory content can be helpful for identifying issues like buffer overflows or memory corruption.
<i>How to Use:</i> In `debug50`, use commands like x or examine to inspect memory. For example, x/10x &variable shows ten hexadecimal words starting from the address of the variable.
5. **Breakpoint Commands** - Associate commands with breakpoints to automate actions when the program pauses.
<i>How to Use:</i> In `debug50`, right-click on a breakpoint, choose "Edit Breakpoint," and add commands in the command field.
6. **Interactive Debugging** modify variable values or execute specific code while the program is paused to experiment with potential fixes.
<i>How to Use:</i> In `debug50`, use the set variable command to change variable values interactively.
7. **Core Dumps** - when a program crashes, generating a core dump allows post-mortem analysis. It provides a snapshot of the program's memory at the time of the crash.
<i>How to Use:</i> Enable core dumps (ulimit -c unlimited) and use a debugger like `gdb` to analyze the core dump file.

    ```bash
        $ ulimit -c unlimited
        $ ./your_program
        # Analyze the core dump using gdb
        $ gdb ./your_program core
    ```
{% include note.html content="💡Regularly Update Dependencies:
Ensure that your development environment, compilers, and libraries are up-to-date to benefit from bug fixes and improvements."
%}

## Arrays in C

**Arrays** are fundamental data structures in programming languages. They allow grouping values of the same data type at contiguous memory locations. Arrays provide a way to manage multiple variables of the same kind without having individual names for each.

### Array Declaration
Array declaration consists of three parts: **type**, **name**, and **size**.

Syntax: `type arrayName[size];` 
* `type` : Data type of the array elements (e.g., int, char, double).
* `arrayName` : Name of the array.
* `size` : Number of elements in the array.

### Indexing in C Arrays
In C, array elements are indexed **starting from 0**. If an array has `n` elements, the first element is at index 0, and the last element is at index n - 1.

Here is an example of an Array Declaration:
```c
    int studentGrades[40];       // Array of 40 integers (index 0 to 39)
    double menuPrices[8];        // Array of 8 doubles (index 0 to 7)
    bool truthTable[10];         // Array of 10 Booleans (index 0 to 9)
```
So, for an array of 40 integers, the valid indices are from 0 to 39, for an array of 8 doubles, the valid indices are from 0 to 7, and for an array of 10 Booleans, the valid indices are from 0 to 9.

### Initializing Arrays

Arrays can be initialized during declaration using the special instantiation syntax.

Example: `bool truthTable3[] = {false, true, true};`

### Multidimensional Arrays

Arrays are not restricted to a single dimension. Multidimensional arrays use multiple size specifiers.

Example: `bool battleship[10][10];` represents a 10x10 grid.

### Manipulating Array Elements

Individual array elements can be treated as variables. Access elements using the syntax: `arrayName[index]`.

Example: `truthTable[2] = false;`

### Copying Arrays
Arrays cannot be assigned to each other directly. Copying elements requires using a loop to iterate through each element.

Example:
```c
    for (int j = 0; j < 5; j++) {
        bar[j] = foo[j];
    }
```
### Passing Arrays to Functions

When passing arrays to functions in C, it's important to note that arrays are passed by reference. Functions receive the actual array, not a local copy, allowing them to manipulate array elements directly. Professor David will explore this topic further in the upcoming weeks.

