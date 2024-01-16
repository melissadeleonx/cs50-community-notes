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
{% include note.html content="This Markdown file provides an organized summary of the content from the provided transcript for Week 1 Shorts of CS50. The information is structured for easy reference and review."
%}

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

### 5. 'Void' Type
The `void` in C is used to indicate that a function doesn't return any value. While void itself isn't a data type for variables, it serves as a return type for functions.

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


### CS50 Library Data Types

CS50 provides additional data types through its library, including `bool` and `string`.

### 1. Bool ('bool') Data Type
The `bool` data type is used for variables storing Boolean values (true or false). Booleans are fundamental in programming logic, enabling the representation of conditions and decision-making in code.

```vbnet
    #include <cs50.h>
    bool isTrue = true;    // Declaration and Initialization
```
### 2. String ('string') Data Type
The `string` data type is used for variables storing sequences of characters, representing words or text. Strings are crucial for handling textual information in programs.

```vbnet
    #include <cs50.h>
    string greeting = "Hello";  // Declaration and Initialization
```
{% include note.html content="💡Understanding these data types and how to declare, assign, and initialize variables is fundamental in C programming. Practice and hands-on coding will enhance your proficiency in working with these concepts"
%}


## CS50 Library and other Libraries

A **library in C** is a collection of pre-compiled routines, functions, and data types that can be reused in different programs. These libraries simplify programming by providing ready-made solutions for common tasks. Libraries typically contain functions and data types that extend the capabilities of the base programming language.

In C, the `#include` directive is used to include libraries in your program. When you include a library, you gain access to the functions and data types it provides, allowing you to use them in your code.

### CS50 Library

The CS50 library is a specific library provided by the CS50 course. It extends the capabilities of C by introducing additional data types, such as bool and string, and providing functions that simplify certain tasks. To use the CS50 library in your program, you include the following line at the beginning:

```vbnet
    #include <cs50.h>
```
This line tells the compiler to include the CS50 library, making its features available for use in your code. For more information on the CS50 library, you can visit [CS50 Library Documentation](https://manual.cs50.io/){:target="_blank"}.

### Various Libraries

As you continue your programming journey, you'll encounter various other libraries. These could be standard libraries that come with the programming language (like `<stdio.h>` in C) or third-party libraries that provide specialized functionalities.

Additionally, you'll have opportunities to create your own libraries. Creating a library involves grouping related functions and data types into a separate file that can be reused across different programs. This modular approach to programming enhances code organization and reusability.

## Declaration and Initialization

**Declaration** and **Initialization** are two distinct concepts related to the creation and use of variables.

### Declaration
Declaration is the process of announcing the existence and characteristics of a variable to the compiler. When you declare a variable, you are essentially telling the compiler what type of data the variable will store, and you're providing a name for that variable.

In C, a variable declaration typically includes two main parts: the data type and the variable name.

```vbnet
    int number;  // Declaration of an integer variable named 'number'
```
In this example, int is the data type, and number is the variable name. This line informs the compiler that a variable named number of type int (integer) will be used in the program.

### Initialization
Initialization is the process of assigning an initial value to a variable at the time of declaration or later in the program. When you initialize a variable, you provide it with an initial value.

```vbnet
    int anotherNumber = 42;  // Declaration and Initialization of an integer variable
```
In this example, the variable anotherNumber is not only declared but also initialized with the value 42 at the same time. Initialization is optional, and you can declare a variable first and assign a value to it later in your program.

```vbnet
    int yetAnotherNumber;  // Declaration
    yetAnotherNumber = 99;  // Initialization (at a later point)
```
Here, the variable yetAnotherNumber is declared first and initialized with the value 99 later in the program.

## Operators
**Operators** in C are used to perform various operations on operands, which can be variables, constants, or expressions. These operations range from basic arithmetic calculations to logical comparisons.

### Assignment Operator (=)

The assignment operator (=) is used to assign a value to a variable in C.

```vbnet
    int x = 10; // Declare an integer variable x and assign the value 10 to it
```

{% include note.html content="Equality (==) vs. Assignment (=): Be cautious about using the correct operator. == is used for comparison, while = is used for assignment."
%}

### Arithmetic Operators (+, -, *, /, %)

Arithmetic operators perform basic mathematical operations on numeric values.

```vbnet
    int x = y + 1;  // Addition
    x = x * 5;      // Multiplication
    int m = 13 % 4; // Modulus (gives the remainder of division)
```

### Shorthand Assignment Operators (+=, -=, *=, /=, %=)

Shorthand assignment operators combine an arithmetic operation with assignment in a more concise form.

```vbnet
    x += 5; // Equivalent to x = x + 5
```
{% include note.html content="Shorthand Assignment Operators: They provide a concise way to update variable values and can make your code more readable." %}


### Increment and Decrement Operators (++ and --)

Increment (++) adds 1 to a variable, and decrement (--) subtracts 1 from a variable.

```vbnet
    x++; // Equivalent to x = x + 1
```

### Modulus Operator (%)

The modulus operator (%) calculates the remainder when dividing two numbers.

```vbnet
    int m = 13 % 4; // m will be 1 (remainder of 13 divided by 4)
```

### Boolean Expressions and Logical Operators (&&, ||, !)

Boolean expressions evaluate to true or false. Logical operators perform operations on Boolean values.

```vbnet
    int x = 10, y = 5;
    if (x > y && y != 0) {
        // Code to execute if both conditions are true
    }

    if (x < y || y == 0) {
        // Code to execute if at least one condition is true
    }

    if (!(x == y)) {
        // Code to execute if the condition is false
    }
```

{% include note.html content="Logical Operators (&&, ||, !): These are commonly used in conditional statements and loops to control program flow based on conditions."
%}

### Relational Operators (<, >, <=, >=, ==, !=)

Relational operators compare values and return true or false based on the comparison.

```vbnet
    if (x < y) {
    // Code to execute if x is less than y
    }

    if (x >= y) {
        // Code to execute if x is greater than or equal to y
    }

    if (x == y) {
        // Code to execute if x is equal to y
    }

    if (x != y) {
        // Code to execute if x is not equal to y
    }
```

## Conditional Statements

Conditional statements are essential in programming because they enable your code to make decisions and respond dynamically to different situations. They provide the logic and structure necessary for creating programs that can adapt, respond to user input, handle errors, and execute different actions based on changing circumstances. They are a fundamental building block in programming that enhances the versatility and functionality of your software.

### If Statements

The `if`statement in C allows your program to make decisions based on the evaluation of a Boolean expression. If the expression is true, the code inside the curly braces is executed; otherwise, it is skipped.

```vbnet
    int x = 10;
    if (x < 20) {
    // Code to execute if x is less than 20
    }
```

### If-Else Statements

The `if-else` statement extends the if statement by providing an alternative branch of code to execute when the Boolean expression is false.

```vbnet
    int x = 25;
    if (x < 20) {
        // Code to execute if x is less than 20
    } else {
        // Code to execute if x is 20 or greater
    }
```
### If-Else If-Else Chain

An extension of if-else where multiple conditions are checked in a sequence. The code block associated with the first true condition is executed.

```vbnet
    int x = 15;
    if (x < 10) {
        // Code to execute if x is less than 10
    } else if (x < 20) {
        // Code to execute if x is between 10 and 19
    } else {
        // Code to execute if x is 20 or greater
    }
```

### Switch Statement

The switch statement in C allows you to specify distinct cases based on the value of an expression. It is an alternative to multiple if-else if-else statements.

```vbnet
    int x = 3;
    switch (x) {
        case 1:
            // Code to execute if x is 1
            break;
        case 2:
            // Code to execute if x is 2
            break;
        case 3:
            // Code to execute if x is 3
            break;
        default:
            // Code to execute if x doesn't match any case
    }
```
### Ternary Operator (?:)

The ternary operator (?:) is a shorthand way to express simple if-else statements in a single line. It is used for making decisions where there are only two possible outcomes.

```vbnet
    int x = (condition) ? 5 : 6;
```
In this example, if the condition is true, x will be assigned the value 5; otherwise, it will be assigned the value 6.

{% include note.html content="Switch Statement vs. If-Else Chain - While both can be used for similar purposes, the choice between switch and if-else depends on the specific scenario and the values being tested.
" %}

## Loops
A **loop** is a control flow structure that allows a set of statements to be executed repeatedly as long as a specified condition is true. Loops provide a concise way to perform repetitive tasks without duplicating code.  They help improve code efficiency and readability by avoiding redundant code. Here are the types of Loops in C.

### while Loop

The `while` Loop executes a block of code repeatedly as long as the specified boolean expression evaluates to true.  Suitable for scenarios where the number of iterations is uncertain.
```vbnet
    #include <stdio.h>
    int main() {
        int i = 0;
        while (i < 5) {
            printf("%d ", i);
            i++;
        }
        return 0;
    }
```
**Output**: `0 1 2 3 4`

### do while Loop

The `do while`Loop is similar to the while loop, but guarantees the execution of the loop's body at least once. It checks the condition after the first iteration. Useful when you want to ensure the loop body executes at least once.

```vbnet
    #include <stdio.h>

    int main() {
        int i = 0;
        do {
            printf("%d ", i);
            i++;
        } while (i < 5);
        return 0;
    }
``` 
**Output**: `0 1 2 3 4`

### for Loop

`for` Loop is designed for iterating a specific number of times. It has three parts within the parentheses: initialization, condition, and increment/decrement. Suited for situations where the number of iterations is known beforehand.

```vbnet
    #include <stdio.h>

    int main() {
        for (int i = 0; i < 5; i++) {
            printf("%d ", i);
        }
        return 0;
    }
``` 

**Output**: `0 1 2 3 4`

{% include note.html content="Be cautious of unintentional infinite loops, which execute indefinitely. Ensure there's a mechanism to exit the loop (e.g., using break). Statements like break and continue can be used to control loop execution. "
%}

## Command Line

The **CS50 IDE** (Integrated Development Environment) and older versions of CS50 appliances run on **Ubuntu**, which is a flavor of the Linux operating system. 

**Linux** is favored by programmers, and even though graphical user interfaces (GUIs) are available, the command line (terminal) is frequently used by programmers.

### Basic Linux Commands
* `ls` (list): Used to display the files and folders in the current directory.
* `cd` (change directory): Navigates between directories.
* `pwd` (present working directory): Displays the current directory path.
* `mkdir` (make directory): Creates a new folder or directory.
* `cp ` (copy): Copies files or directories.
* `rm` (remove): Deletes files or directories.
* `mv` (move): Moves or renames files or directories.

### Additional Tips:
* `ls -a`: Lists all files, including hidden ones.
* `cd ..`: Moves up one level in the directory structure.
* `cp -r`: Copies directories and their contents recursively.
* `rm -r`: Removes directories and their contents recursively.
* `mv file.txt /path/to/new/location`: Moves a file to a different directory.

These commands are fundamental for navigating and managing files and directories in a Linux environment. Understanding and mastering them provides a strong foundation for working with the command line in various contexts.