---
title: CS50 Week 3 - Algorithms
tags: [getting_started, troubleshooting]
keywords:
summary: "In the context of computer science, an algorithm is a precise and unambiguous set of instructions or rules designed to perform a specific task or solve a particular problem."
sidebar: mydoc_sidebar
permalink: week_3
folder: mydoc
---

## Understanding Algorithms

Algorithms are a sets of instructions designed to perform a specific task. It's essentially a step-by-step procedure that, when followed, guarantees the completion of a task or the solution to a problem. Algorithms are fundamental to computer science, as they serve as the building blocks for writing computer programs.

### Key Characteristics of Algorithms
1. **Input and Output**: Every algorithm takes some input, processes it through a series of well-defined steps, and produces an output.
2. **Finiteness**: An algorithm must terminate after a finite number of steps. It cannot run indefinitely.
3. **Definiteness**: Each step of the algorithm must be precisely defined, leaving no room for ambiguity or interpretation.
4. **Effectiveness**: The steps of an algorithm must be executable and practical, meaning that they can be carried out within the constraints of time and resources.

### Importance of Algorithms in Computer Science
Algorithms are crucial for breaking down complex problems into manageable steps, making problem-solving more structured and feasible. Well-designed algorithms can significantly impact the efficiency of a program. They help in optimizing resource usage, minimizing execution time, and improving overall performance.

Algorithms can be reused in different contexts and applications. Once a problem is solved algorithmically, the solution can be applied to similar problems. They allow programmers to abstract away complex details, focusing on high-level steps and logic. This abstraction facilitates collaboration and code maintenance.

## Searching Algorithms
Searching algorithms are fundamental procedures in computer science designed to locate a specific target within a collection of data. These algorithms play a crucial role in various applications, from databases to sorting large datasets. Two primary types of searching algorithms are Linear Search and Binary Search.

### Linear Search

**Linear search** is a straightforward algorithm that iterates through each element in a collection until it finds the target or exhausts the entire dataset.

**Workflow:**

1. Start from the first element and move sequentially through the collection.
2. If the target is found, the search is successful.
3. If the entire collection is traversed without finding the target, the search is unsuccessful.

**Complexity:**

- **Worst Case: O(n)** - Linear time complexity, where n is the size of the collection.
- **Best Case: Ω(1)** - Constant time if the target is found immediately.

**Pseudocode Overview:**
```c
    For each element in the array:
        If the element is the target:
            Stop the search
        Else:
            Move to the next element
```

### Binary Search