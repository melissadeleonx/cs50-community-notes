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
```vbnet
    return_type function_name(data_type parameter1, data_type parameter2, ...);
``` 
Breaking down the syntax, examine each pieces of codes.
- **return_type**: Specifies the type of data that the function will return.
- **function_name**: A unique identifier for the function.
- **data_type parameter1, data_type parameter2, ...**: Input parameters with their data types.

A sample code to understand better:

```vbnet
    int add(int a, int b) {
    return a + b;
    }
``` 
The function definition provides the actual implementation of the function. It includes the function body, where the logic is written, and a return statement specifying what the function will output.






```vbnet
CODE WITH ME!
``` 