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

**Linear search** is a straightforward algorithm that iterates through **each element** in a collection until it finds the target or exhausts the entire dataset.

**Workflow:**

1. Start from the first element and move sequentially through the collection.
2. If the target is found, the search is successful.
3. If the entire collection is traversed without finding the target, the search is unsuccessful.

**Complexity:**

- **Worst Case: O(n)** - Linear time complexity, where n is the size of the collection.
- **Best Case: Ω(1)** - Constant time if the target is found immediately.

**Pseudocode Overview:**
```yml
    For each element in the array:
        If the element is the target:
            Stop the search
        Else:
            Move to the next element
```

### Binary Search
**Binary search** is a more efficient algorithm suitable for sorted collections. It leverages the **"divide and conquer"** strategy to narrow down the search space quickly.

**Workflow:**

1. Start with the entire sorted collection.
2. Calculate the midpoint and compare it with the target.
3. Adjust the search space based on the comparison.
4. Repeat until the target is found or the search space becomes empty.

**Complexity:**

- **Worst Case: O(log n)** - Logarithmic time complexity, where n is the size of the sorted collection.
- **Best Case: Ω(1)** - Constant time if the target is found immediately.

**Pseudocode Overview:**
```c
   BinarySearch(array, target):
    // Ensure the array is sorted beforehand
    if array is not sorted:
        Sort array

    // Initialize start and end indices
    start = 0
    end = length of array - 1

    // Repeat until the search space is empty
    while start <= end:
        // Calculate the midpoint of the current array
        mid = (start + end) / 2

        // If the target is found at the midpoint, stop the search
        if array[mid] is equal to target:
            return mid

        // If the target is less than the value at the midpoint,
        // adjust the end point to be just to the left of the midpoint
        else if target < array[mid]:
            end = mid - 1

        // If the target is greater than the value at the midpoint,
        // adjust the start point to be just to the right of the midpoint
        else:
            start = mid + 1

    // If the loop completes and the target is not found,
    // return a value indicating that the target is not in the array
    return "Target not found"
```

## Sorting Algorithms

**Sorting** is essential for efficient data retrieval in databases, allowing for faster search and retrieval times. Many search algorithms, like binary search, rely on the sorted nature of data to significantly reduce the search space and improve search times. The choice of a sorting algorithm depends on factors such as the size of the dataset, system requirements, and the specific application's needs. A well-chosen sorting algorithm can significantly impact the overall performance and responsiveness of a system.

### Bubble Sort

**Bubble sort** is a sorting algorithm designed to arrange elements in ascending or descending order. It operates on the principle of repeatedly **swapping adjacent elements** until the entire array is sorted.

**Workflow:**
1. Initialization: Start with a set of unsorted elements in an array.

2. Repeat Until Sorted:
- Set a swap counter to a non-zero value.
- Iterate through the array, comparing adjacent pairs.
- If a pair is out of order, swap the elements and increment the swap counter.
- If no swaps are made during an iteration, declare the array sorted.

3. Visualization: Imagine larger elements "bubbling" to the end (right) and smaller elements moving to the beginning (left).

**Pseudocode Overview:**

```c
    BubbleSort(array):
        // Initialize a swap counter to a non-zero value to start the process
        swapCounter = non-zero

        // Repeat until no swaps are made in an iteration
        while swapCounter is not 0:
            // Reset swap counter for the new iteration
            swapCounter = 0
            
            // Iterate through adjacent pairs
            for i from 0 to length of array - 2:
                // Compare and swap if out of order
                if array[i] > array[i + 1]:
                    swap(array[i], array[i + 1])
                    swapCounter = swapCounter + 1

        // Array is now sorted
```
**Example** - Consider an unsorted array: `[5, 2, 1, 3, 6, 4]`. 
1. Initial pass: Swaps are made, moving the largest element (6) to the end.
2. Subsequent passes: More swaps occur until no swaps are needed, indicating the array is sorted.

**Complexity:**

- **Worst Case: O(n^2)** - Occurs when the array is in reverse order, requiring multiple passes of swapping.

- **Best Case: Ω(n)** - Occurs when the array is already sorted, and no swaps are needed in the first pass.

{% include note.html content="**Bubble sort** is relatively simple but less efficient compared to other sorting algorithms, especially for large datasets. It's a useful educational tool to understand the basics of sorting algorithms." %}

### Selection Sort

**Selection sort** is a straightforward sorting algorithm designed to build a **sorted list** by iteratively selecting the smallest unsorted element and placing it at the end of the sorted part.

**Workflow:**

1. Initialization:
- Start with an unsorted array, indicated by red-colored elements.
- Define the unsorted part as the entire array initially.

2. Repeat Until Sorted:
- Search through the unsorted part to find the smallest value.
- Swap the smallest value with the first element of the unsorted part.
- Mark the swapped element as sorted (color it blue).

3. Visualization:
- Visualize the array transition from completely unsorted (red) to completely sorted (blue) by iteratively selecting and placing the smallest unsorted element.

**Pseudocode Overview:**

```c
SelectionSort(array):
    // Repeat until no unsorted elements remain
    for i from 0 to length of array - 1:
        // Find the index of the smallest value in the unsorted part
        minIndex = i
        for j from i + 1 to length of array - 1:
            if array[j] < array[minIndex]:
                minIndex = j

        // Swap the smallest value with the first element of the unsorted part
        swap(array[i], array[minIndex])
        
        // Mark the swapped element as sorted (color it blue)
        markAsSorted(array[i])
```

**Example** - Consider an unsorted array: `[5, 2, 1, 3, 6, 4]`.
1. Initial pass: The smallest element (1) is swapped with the first element, marking it as sorted.
2. Subsequent passes: Smallest unsorted elements are selected and placed at the end of the sorted part.

**Complexity:**

**Worst Case: O(n^2)** - Occurs when, in each iteration, we have to search through the entire unsorted part to find the smallest element.

**Best Case: Ω(n^2)** - Similar to the worst case, as we need to iterate through the entire array in every pass.

{% include note.html content="**Selection sort**, though not the most efficient sorting algorithm, has simplicity and ease of implementation. It is suitable for small datasets or situations where simplicity is preferred over optimization." %}

### Merge Sort

**Merge sort** is a sorting algorithm that employs a **divide-and-conquer** strategy to sort an array. The primary idea is to break down the array into smaller sub-arrays, sort those sub-arrays, and then merge them together to obtain the final sorted array.

**Workflow:**
1. Divide: Split the original array into two halves.
2. Conquer: Recursively sort the left and right halves of the array.
3. Merge: Combine the two sorted halves back into a single sorted array.

{% include note.html content="While both **Merge Sort** and **Binary Search** algorithms involve dividing a problem into smaller sub-problems, their goals and applications are distinct. Merge sort is focused on sorting, whereas binary search is focused on efficient searching within a sorted structure." %}

**Pseudocode Overview:**

```c
    function mergeSort(arr):
        if length of arr <= 1:
            return arr
        
        // Divide
        mid = length of arr / 2
        left_half = mergeSort(arr[0:mid])
        right_half = mergeSort(arr[mid:end])

        // Conquer and Merge
        return merge(left_half, right_half)

    function merge(left, right):
        result = empty array
        left_index = right_index = 0

        while left_index < length of left and right_index < length of right:
            if left[left_index] <= right[right_index]:
                add left[left_index] to result
                left_index++
            else:
                add right[right_index] to result
                right_index++

        // Add remaining elements
        append remaining elements of left to result
        append remaining elements of right to result

        return result

```
**Example** - Let's consider an array: `[5, 2, 1, 3, 6, 4]`

1. Initial call: `mergeSort([5, 2, 1, 6, 4, 3])`
- Divide: `[5, 2, 1]` and `[6, 4, 3]`
- Recursively apply mergeSort to both halves.
2. For the left half: `mergeSort([5, 2, 1])`
- Divide: `[5]` and `[2, 1]`
- Recursively apply mergeSort.
3. Merging `[5]` and `[1, 2]` gives a sorted left half: `[1, 2, 5]`
4. For the right half: `mergeSort([6, 4, 3])`
- Divide: `[6]` and `[4, 3]`
- Recursively apply mergeSort.
5. Merging `[6]` and `[3, 4]` gives a sorted right half: `[3, 4, 6]`
6. Merging the overall left and right halves: `[1, 2, 3, 4, 5, 6]`

**Complexity:**

- **Worst Case: O(n log n)** - The array is consistently divided and merged log n times.
- **Best Case: O(n log n)** - Even if partially sorted, the recursive division still occurs.

{% include note.html content="**Merge sort** is known for its consistent performance, especially in scenarios where stability and a guaranteed O(n log n) time complexity are crucial." %}

## Recursion

**Recursion** is a programming technique where a function calls itself during its execution. The process involves breaking a complex problem into simpler subproblems and solving each subproblem.

### Key Components

1. **Base Case:**
- A condition that stops the recursion.
- Provides the simplest form of the problem that can be directly solved.

2. **Recursive Case:**
- Describes how to break down the current problem into smaller subproblems.
- Involves calling the function itself with a modified input.

### Characteristics
- **Elegance:** Recursive solutions often result in concise and elegant code.
- **Visualization:** Recursion allows for a clear and intuitive representation of certain problems.
- **Powerful Tool:** Recursion is a powerful technique for solving problems that exhibit a divide-and-conquer nature.

**Workflow:**

1. Identify Base Case. Define a condition where the problem is simple enough to be solved directly.
2. Define Recursive Case. Break down the problem into smaller subproblems. Modify the input and call the function recursively.
3. Ensure that each recursive path leads towards the base case. Avoid infinite recursion.

**Example**
- **Factorial Function**
1. Mathematical Definition: `n! = n * (n-1) * (n-2) * ... * 2 * 1`
2. Base Case: If `n equals 1, return 1`.
3. Recursive Case: `Return n * factorial(n-1)`.

- **Collatz Conjecture**
1. Conjecture Steps: If n is even, divide it by 2; if odd, multiply it by 3 and add 1.
2. Base Case: If n equals 1, return 0 (no more steps needed).
3. Recursive Cases: If n is even, return 1 + collatz(n/2). If n is odd, return 1 + collatz(3n + 1).

### Pseudocode Overview
Here's a pseudocode template for a recursive **Collatz function**:

```c
    function collatz(n):
        // Base case: check if n has reached 1
        if n == 1:
            // Return 0, as it takes 0 steps to reach 1 from 1
            return 0

        // Recursive cases
        if n is even:
            // If n is even, halve it and make a recursive call
            return 1 + collatz(n / 2)
        else:
            // If n is odd, apply the Collatz rule and make a recursive call
            return 1 + collatz(3 * n + 1)
```
* The base case checks if n has reached 1. If true, it returns 0, as it takes 0 steps to reach 1 from 1.

* For recursive cases, it checks if n is even or odd. If even, it halves n and makes a recursive call. If odd, it applies the Collatz rule (3n + 1) and makes a recursive call.

* The 1 + before the recursive call represents the step taken in each recursive call.

{% include note.html content="**Recursion** is effective for solving certain problems due to its elegant and concise nature, but it's essential to consider efficiency and potential stack overflow in specific scenarios." %}

Besides **factorial** and the **Collatz conjecture** examples, other classic examples of recursion include computing **Fibonacci numbers**, traversing a tree data structure, and solving problems like the **Tower of Hanoi**.

**Complexity:**
- The time complexity of recursive algorithms depends on the number of recursive calls and the time complexity within each call.
- Space complexity involves the size of the call stack, and excessive recursion may lead to stack overflow.

## Other Algorithmic Techniques

There are other algorithmic techniques and paradigms in addition to recursion. Some of them include:

* **Divide and Conquer:** Similar to recursion, it involves breaking a problem into subproblems and solving them independently. Merge sort and quicksort are examples of divide and conquer algorithms.

* **Dynamic Programming:** It involves solving a problem by breaking it down into simpler overlapping subproblems. Memoization is often used to store and reuse solutions to subproblems to avoid redundant computations.

* **Greedy Algorithms:** These algorithms make locally optimal choices at each stage with the hope of finding a global optimum. Examples include Dijkstra's algorithm for finding the shortest path and Huffman coding for data compression.

* **Backtracking:** It is a technique used to solve problems through a trial-and-error approach. The algorithm incrementally builds a solution and abandons the solution (backtracks) when it determines that the current path cannot lead to a valid solution.

* **Brute Force:** A straightforward approach that involves trying all possible solutions and selecting the best one. While it may not be efficient for large problems, it guarantees correctness.

Each of these techniques has its own strengths and weaknesses, and the choice of which one to use depends on the nature of the problem at hand.