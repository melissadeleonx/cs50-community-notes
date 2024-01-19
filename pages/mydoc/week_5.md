---
title: CS50 Week 5 - Data Structures
tags: [getting_started, troubleshooting]
keywords:
summary: ""
sidebar: mydoc_sidebar
permalink: week_5
folder: mydoc
---

**Data structures** are a fundamental concept in computer science that refers to the organization, storage, and manipulation of data in a way that facilitates efficient access and modification. The choice of an appropriate data structure is crucial for optimizing algorithms and solving computational problems efficiently.

## Key Concepts
1. **Organization of Data:**
- Linear Structures: Data elements are organized sequentially, like arrays and linked lists.
- Non-linear Structures: Data elements are connected in a hierarchical or non-sequential manner, as in trees and graphs.

2. **Storage and Retrieval:**
- **Arrays:** Fixed-size, contiguous memory structures with constant-time access through indexing.
- **Linked Lists:** Dynamic structures with elements (nodes) connected by pointers, allowing for dynamic size and efficient insertions/deletions.
- **Hash Tables:** Utilize hash functions to map keys to indices, enabling quick data retrieval with proper handling of collisions.
- **Tries:** Tree structures where each node represents a character in a key, facilitating efficient search and insertion.

3. **Efficiency Considerations:**
- **Time Complexity:** Analysis of the running time of operations as a function of input size.
- **Space Complexity:** Evaluation of the memory usage of an algorithm or data structure.
- **Trade-offs:** Different data structures offer different trade-offs between time and space efficiency.

Let's break down the major data structures discussed: Arrays, Linked Lists, Hash Tables, and Tries.

### Arrays
An array is a fixed-size, contiguous memory structure that stores elements of the same data type. Elements are accessed using indices, allowing for constant-time random access.

**Sample Code**
```c
    #include <stdio.h>

    int main() {
        // Declare an array of integers
        int numbers[5] = {1, 2, 3, 4, 5};

        // Access and print elements
        for (int i = 0; i < 5; i++) {
            printf("%d ", numbers[i]);
        }

        return 0;
    }
```

**Pros**
- Random Access: Constant time lookup with direct indexing.
- Efficient Sorting: Relatively easy to sort compared to other data structures.
-Compact: Minimal wasted space as the size is fixed.
**Cons**
- Fixed Size: Lack flexibility for dynamic resizing.
- Inefficient Insertion and Deletion: Inserting or deleting elements in the middle involves shifting elements, making these operations inefficient.

### Linked Lists
A linked list is a dynamic data structure where elements, called nodes, are connected using pointers. Each node contains data and a pointer to the next node, forming a chain-like structure.

**Sample Code**
```c
    #include <stdio.h>
    #include <stdlib.h>

    // Node structure
    struct Node {
        int data;
        struct Node* next;
    };

    int main() {
        // Create nodes
        struct Node* head = NULL;
        struct Node* second = NULL;
        struct Node* third = NULL;

        head = (struct Node*)malloc(sizeof(struct Node));
        second = (struct Node*)malloc(sizeof(struct Node));
        third = (struct Node*)malloc(sizeof(struct Node));

        // Assign data and link nodes
        head->data = 1;
        head->next = second;

        second->data = 2;
        second->next = third;

        third->data = 3;
        third->next = NULL;

        // Traverse and print linked list
        struct Node* current = head;
        while (current != NULL) {
            printf("%d ", current->data);
            current = current->next;
        }

        return 0;
    }
```
**Pros**
- Dynamic Size: Easily grow or shrink by adding or removing nodes.
- Efficient Insertion and Deletion at the Front: Adding or removing from the front is straightforward.

**Cons**
- Linear Search: No random access; searching involves traversing the list.
- Inefficient Sorting: Sorting during construction hampers quick insertions.
- Slightly Larger Size: Contains pointers, slightly less space-efficient than arrays.

### Hash Tables
A hash table is a data structure that maps keys to values using a hash function. It provides efficient insertion, deletion, and lookup operations, but collisions must be handled, either through chaining or probing.

```c
    #include <stdio.h>
    #include <stdlib.h>

    // Node structure for chaining
    struct Node {
        int key;
        int value;
        struct Node* next;
    };

    // Hash table structure
    struct HashTable {
        int size;
        struct Node** array;
    };

    // Hash function example
    int hash(int key, int size) {
        return key % size;
    }

    int main() {
        // Create a hash table
        int size = 10;
        struct HashTable* hashTable = (struct HashTable*)malloc(sizeof(struct HashTable));
        hashTable->size = size;
        hashTable->array = (struct Node**)malloc(sizeof(struct Node*) * size);

        // Initialize the array with NULL
        for (int i = 0; i < size; i++) {
            hashTable->array[i] = NULL;
        }

        // Example usage of the hash function
        int hashedValue = hash(42, size);
        printf("Hashed value: %d\n", hashedValue);

        // Cleanup: free allocated memory

        return 0;
    }
```
