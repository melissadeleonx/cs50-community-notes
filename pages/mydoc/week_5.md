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

## Key Concepts of Data Structures
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

## Structures
**Structures**, often referred to as structs, are a powerful feature in C that allows the grouping of variables of different types under a single user-defined data type. This enables the creation of more complex and meaningful data structures by combining various data elements into a cohesive unit.

## Arrays
An **array** is a fixed-size, contiguous memory structure that stores elements of the same data type. Elements are accessed using indices, allowing for constant-time random access.

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
- **Random Access:** Constant time lookup with direct indexing.
- **Efficient Sorting:** Relatively easy to sort compared to other data structures.
-**Compact:** Minimal wasted space as the size is fixed.

**Cons**
- **Fixed Size:** Lack flexibility for dynamic resizing.
- **Inefficient Insertion and Deletion:** Inserting or deleting elements in the middle involves shifting elements, making these operations inefficient.

## Linked Lists
A **linked list** is a dynamic data structure where elements, called nodes, are connected using pointers. Each node contains data and a pointer to the next node, forming a chain-like structure.

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
- **Dynamic Size:** Easily grow or shrink by adding or removing nodes.
- **Efficient Insertion and Deletion at the Front:** Adding or removing from the front is straightforward.

**Cons**
- **Linear Search:** No random access; searching involves traversing the list.
- **Inefficient Sorting:** Sorting during construction hampers quick insertions.
- **Slightly Larger Size:** Contains pointers, slightly less space-efficient than arrays.

## Hash Tables
A **hash table** is a data structure that maps keys to values using a hash function. It provides efficient insertion, deletion, and lookup operations, but collisions must be handled, either through chaining or probing.

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
**Pros**
- **Fast Insertion and Deletion:** Using hash codes and proper data distribution.
- **Reasonable Lookup Speed:** Average case better than linked lists due to smaller linked lists in chaining.
- **Variable Size:** Can accommodate different amounts of data.
**Cons**
- **Complexity:** Insertion and deletion may be complex, especially with collisions.
- **Not Suitable for Sorting:** If sorting is a primary concern, arrays are more efficient.
- **Variable Size:** Size is hard to define and may lead to inefficient use of space.

## Tries

A **trie** is a tree-like data structure that stores a dynamic set of keys where each node represents a character in the key. It is particularly useful for quick lookups and efficient insertion and deletion of keys.

```c
    #include <stdio.h>
    #include <stdlib.h>

    // Trie node structure
    struct TrieNode {
        struct TrieNode* children[26]; // Assuming lowercase English letters
        int isEndOfWord;
    };

    // Initialize a new trie node
    struct TrieNode* createNode() {
        struct TrieNode* node = (struct TrieNode*)malloc(sizeof(struct TrieNode));
        for (int i = 0; i < 26; i++) {
            node->children[i] = NULL;
        }
        node->isEndOfWord = 0;
        return node;
    }

    // Insert a key into the trie
    void insert(struct TrieNode* root, char* key) {
        struct TrieNode* current = root;
        for (int i = 0; key[i] != '\0'; i++) {
            int index = key[i] - 'a';
            if (!current->children[index]) {
                current->children[index] = createNode();
            }
            current = current->children[index];
        }
        current->isEndOfWord = 1;
    }

    // Search for a key in the trie
    int search(struct TrieNode* root, char* key) {
        struct TrieNode* current = root;
        for (int i = 0; key[i] != '\0'; i++) {
            int index = key[i] - 'a';
            if (!current->children[index]) {
                return 0; // Key not found
            }
            current = current->children[index];
        }
        return (current != NULL && current->isEndOfWord);
    }

    int main() {
        struct TrieNode* root = createNode();

        // Insert and search examples
        insert(root, "apple");
        insert(root, "banana");
        printf("Search 'apple': %s\n", search(root, "apple") ? "Found" : "Not Found");
        printf("Search 'orange': %s\n", search(root, "orange") ? "Found" : "Not Found");

        // Cleanup: free allocated memory

        return 0;
    }
```

**Pros**
- **Constant Time Insertion, Deletion, and Lookup:** Once hurdles of dynamic memory allocation are overcome.
- **Inherent Sorting:** Elements are effectively sorted as the trie is built.

**Cons**
- **Large Size:** Nodes can be sizable, leading to a potentially large overall trie.
- **Complex Insertion:** Initial dynamic memory allocation might be challenging.
- **Not Space-Efficient:** Consumes more space compared to arrays and linked lists.

{% include note.html content="The choice of a data structure depends on the specific requirements of the task at hand. Arrays offer quick random access but lack flexibility, linked lists are dynamic but suffer from linear search, hash tables provide fast insertion and deletion with some compromise on space, and tries offer constant time operations at the cost of increased space usage. Consider the trade-offs and choose the structure that best aligns with your application's needs." %}
