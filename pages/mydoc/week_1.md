---
title: CS50 Week 1 - Basics of C
tags: [getting_started, troubleshooting]
keywords:
summary: "C is a powerful and widely-used programming language known for its efficiency and versatility. Understanding its key components is essential for writing effective and reliable code."
sidebar: mydoc_sidebar
permalink: week_1
folder: mydoc
---

# CS50 Week 1: Understanding C Programming

## Share the Knowledge 🌟

Don't be surprised if you find yourself facing a mix of excitement and challenges. Learning a new language, especially one as powerful as C, opens up a world of possibilities in software development. The CS50 Community Notes website is a hub where knowledge is shared, questions are answered, and insights are pooled. Consider exploring this platform for additional support, tips, and a community-driven approach to learning.

## Data Types and Variables

In C programming, understanding data types and variables is crucial for effective coding. Unlike modern languages where data types are often inferred, C requires explicit declaration. Data types play a crucial role in shaping how data is stored, manipulated, and utilized in a program. Let's explore the built-in data types in C and how to work with variables.

### 1. Integer ('int') Data Type

The `int` data type is used for variables storing integer values. 
In C, integers occupy 4 bytes of memory (32 bits). The range of values for integers is from -2^31 to 2^31 - 1, accommodating both positive and negative values.
This range is split into negative and positive integers, with zero included. Approximately, this covers values from negative 2 billion to positive 2 billion.

<pre>
<code>
int number;         // Declaration
number = 17;        // Assignment
int anotherNumber = 42;  // Declaration and Initialization
</code>
</pre>

### 2. Unsigned Integer ('unsigned int')
The `unsigned int` data type is a modification of `int` that exclusively represents non-negative values. Unlike the regular int, the unsigned int excludes negative values, effectively doubling the positive range to 0 to 2^32 - 1.

When you use an unsigned int, you are declaring a variable that can only hold non-negative integers. This allows for a positive range from 0 to 4,294,967,295 (2^32 - 1), as there are no negative values included.

<pre>
<code>
unsigned int positiveNumber = 100;  // Declaration and Initialization
</code>
</pre>

### 3. Character ('char') Data Type
The `char` data type is used for variables storing single characters. Characters occupy 1 byte of memory (8 bits), and their values are defined by the ASCII standard.

<pre>
<code>
char letter;           // Declaration
letter = 'A';          // Assignment
char symbol = '$';     // Declaration and Initialization
</code>
</pre>

### 4. Floating Point (float and double) Data Types
Floating-point numbers are used to represent real numbers that have a decimal point. In C, there are two primary floating-point data types: `float` and `double`.

- **`float`:** This data type occupies 4 bytes of memory, providing a balance between precision and storage.

    <pre>
    <code>
    float pi = 3.14;       // Declaration and Initialization
    </code>
    </pre>

- **`double`:** The double data type, also known as double precision, uses 8 bytes of memory, offering increased precision compared to `float`. 

    <pre>
    <code>
    double precisePi = 3.141592653589793;  // Declaration and Initialization
    </code>
    </pre>

### 5. 'Void' Data Type
The `void` data type in C is used to indicate that a function doesn't return any value. While void itself isn't a data type for variables, it serves as a return type for functions.

<pre>
<code>
int main(void) {
    // Code for the main function
    return 0;  // Indicating successful program execution to the operating system
}
</code>
</pre>
or 

<pre>
<code>
int main() {
    // Code for the main function
    return 0;  // Indicating successful program execution to the operating system
}
</code>
</pre>

In both cases, the void inside the parentheses indicates that main takes no parameters. It's a common practice to use void in this context to explicitly state that main does not expect any 'command-line arguments'. While the int in int main is a historical convention, the void indicates the absence of parameters in the 'function' signature.

These examples showcase the use of void in the main function, emphasizing that int main(void) is a conventional declaration, and void signifies that there are no parameters.

In succeeding weeks, you'll encounter the `void` type in functions. Consider a function printMessage that prints a greeting message. Since this function doesn't return any value, it has a return type of void.

<pre>
<code>
void printMessage() {
    printf("Hello, World!\n");
}
</code>
</pre>


## CS50 Library Data Types

CS50 provides additional data types through its library, including `bool` and `string`.

### Bool ('bool') Data Type
The bool data type is used for variables storing Boolean values (true or false).

```vbnet
    #include <cs50.h>
    bool isTrue = true;    // Declaration and Initialization
```
### String ('string') Data Type
The `string` data type is used for variables storing sequences of characters, representing words or text.
