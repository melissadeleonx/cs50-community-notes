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

### Global Variables
**Global variables** can be accessed by any function in the program. They are declared outside of any particular function.
- Global variables provide flexibility for information sharing among functions.
- However, caution is needed, as changes to a global variable by one function can have unintended consequences for other functions.
- Collaborative coding efforts may introduce naming conflicts when multiple functions use the same variable names.