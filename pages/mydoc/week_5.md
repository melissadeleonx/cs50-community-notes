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

**Sample Code**
```c
    // Define a structure for a car
    struct car {
        int year;           // Integer field
        char model[50];     // Character array (string) field
        char plate[10];     // Character array (string) field
        double odometer;    // Double field
    };

    int main() {
        // Create a variable of type struct car
        struct car myCar;

        // Access and assign values to the fields of myCar
        myCar.year = 2011;
        strcpy(myCar.model, "SomeModel");
        strcpy(myCar.plate, "CS50");
        myCar.odometer = 50505.0;

        // Accessing the fields using the arrow operator
        struct car *ptrToCar = &myCar;
        ptrToCar->year = 2012;  // Equivalent to (*ptrToCar).year = 2012;

        // Dynamically allocate a struct car
        struct car *dynamicCar = (struct car *)malloc(sizeof(struct car));

        if (dynamicCar != NULL) {
            dynamicCar->year = 2020;
            strcpy(dynamicCar->model, "DynamicModel");
            strcpy(dynamicCar->plate, "XYZ123");
            dynamicCar->odometer = 10000.0;

            // Don't forget to free the memory when done
            free(dynamicCar);
        }

        return 0;
    }
```
- The `struct car` definition creates a new data type named `car`, which contains various fields (year, model, plate, odometer).
- In the `main` function, an instance of `struct car` named myCar is created, and its fields are accessed and modified using the dot operator `(.)`.
- The arrow operator `(->)` is used when dealing with pointers to structures. It first dereferences the pointer and then accesses the field.
- Dynamic memory allocation is demonstrated with `malloc` to create a new `struct car`. The arrow operator is used to access and modify its fields. Don't forget to free the allocated memory using `free`.


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

**Pros**
- **Dynamic Size:** Easily grow or shrink by adding or removing nodes.
- **Efficient Insertion and Deletion at the Front:** Adding or removing from the front is straightforward.

**Cons**
- **Linear Search:** No random access; searching involves traversing the list.
- **Inefficient Sorting:** Sorting during construction hampers quick insertions.
- **Slightly Larger Size:** Contains pointers, slightly less space-efficient than arrays.

### Singly-Linked List

A **singly linked list** is a data structure that consists of a sequence of elements, each containing a data field and a reference (or link) to the next element in the sequence. Unlike arrays, linked lists do not have a fixed size, and their elements are not stored in contiguous memory locations.

**Sample Code**
```c
    #include <stdio.h>
    #include <stdlib.h>

    // Node structure for singly linked list
    typedef struct Node {
        int data;
        struct Node* next;
    } Node;

    // Function to create a new node
    Node* createNode(int value) {
        Node* newNode = (Node*)malloc(sizeof(Node));
        if (newNode != NULL) {
            newNode->data = value;
            newNode->next = NULL;
        }
        return newNode;
    }

    // Function to insert a new node at the beginning of the list
    Node* insertAtBeginning(Node* head, int value) {
        Node* newNode = createNode(value);
        if (newNode != NULL) {
            newNode->next = head;
            head = newNode;
        }
        return head;
    }

    // Function to traverse and print the linked list
    void printList(Node* head) {
        while (head != NULL) {
            printf("%d -> ", head->data);
            head = head->next;
        }
        printf("NULL\n");
    }

    // Function to delete the entire linked list
    void deleteList(Node* head) {
        Node* current = head;
        Node* nextNode;

        while (current != NULL) {
            nextNode = current->next;
            free(current);
            current = nextNode;
        }
    }

    int main() {
        // Example usage
        Node* myList = NULL;

        myList = insertAtBeginning(myList, 10);
        myList = insertAtBeginning(myList, 20);
        myList = insertAtBeginning(myList, 30);

        printf("Linked List: ");
        printList(myList);

        // Deleting the entire list
        deleteList(myList);

        return 0;
    }
```

This code defines a simple singly linked list with functions to create a node, insert at the beginning, print the list, and delete the entire list. The `main` function demonstrates how to use these functions to create, display, and delete a linked list.

### Doubly-Linked List

A **doubly linked list** is a type of linked list in which each node contains a data field and two references (or links) to the next and previous nodes in the sequence. Unlike a singly linked list, where movement is unidirectional, a doubly linked list allows for movement in both forward and backward directions.

```c
#include <stdio.h>
#include <stdlib.h>

// Node structure for a doubly linked list
struct Node {
    int data;
    struct Node* next;
    struct Node* prev;
};

// Function to insert a new node at the beginning of a doubly linked list
struct Node* insertAtBeginning(struct Node* head, int newData) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = newData;
    newNode->next = head;
    newNode->prev = NULL;

    if (head != NULL) {
        head->prev = newNode;
    }

    return newNode;
}

// Function to delete a node from a doubly linked list
void deleteNode(struct Node* head, struct Node* deleteMe) {
    if (deleteMe->prev != NULL) {
        deleteMe->prev->next = deleteMe->next;
    } else {
        head = deleteMe->next;
    }

    if (deleteMe->next != NULL) {
        deleteMe->next->prev = deleteMe->prev;
    }

    free(deleteMe);
}

int main() {
    struct Node* head = NULL;

    // Insert nodes at the beginning
    head = insertAtBeginning(head, 15);
    head = insertAtBeginning(head, 10);
    head = insertAtBeginning(head, 5);

    // Delete a node (e.g., node with data 10)
    struct Node* nodeToDelete = head->next;
    deleteNode(head, nodeToDelete);

    // Perform other operations as needed

    return 0;
}
```
This code demonstrates the basic operations of inserting a node at the beginning of a doubly linked list and deleting a node from it. The `struct Node` has both `next` and `prev` pointers to maintain the doubly linked nature of the list.

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

## Queues

A **queue** is a data structure that follows the **First-In-First-Out (FIFO)** principle. Items are added to the end (enqueue) and removed from the front (dequeue). Queues can be implemented using arrays or linked lists. Let's go through the details of array-based and linked-list-based implementations.

### Array-Based Queue

An **array-based queue** is a data structure that stores elements in a linear manner, adhering to the First-In-First-Out (FIFO) principle. It consists of an array with a fixed capacity to hold elements. Key components include the array itself, a front pointer indicating the position of the oldest element, and a size variable representing the number of elements in the queue.

```c
    #define CAPACITY 10

    typedef struct {
        int arr[CAPACITY];  // Array to store queue elements
        int front;          // Index pointing to the front element
        int size;           // Current number of elements in the queue
    } ArrayQueue;

```

### Linked-List-Based Queue

A **linked-list-based** queue is a data structure designed to store elements following the First-In-First-Out (FIFO) principle. It utilizes a linked list, where each element (node) holds data and a pointer to the next node. This queue has two essential pointers: a front pointer pointing to the oldest element and a rear pointer indicating the newest element. These pointers facilitate efficient enqueueing at the rear and dequeueing from the front.

```c
    typedef struct Node {
        int data;            // Data of the node
        struct Node* next;   // Pointer to the next node
    } Node;

    typedef struct {
        Node* front;         // Pointer to the front (oldest) node
        Node* rear;          // Pointer to the rear (newest) node
    } LinkedListQueue;
```

## Stacks

A **stack** is a specialized data structure that organizes and manages elements based on the Last-In-First-Out (LIFO) principle. In a stack, only the most recently added element can be removed, making it akin to a stack of objects where you can add or remove items only from the top. There are two common ways to implement stacks: using arrays or linked lists.

### Array-Based Stack

In an array-based implementation, a stack is typically defined as a structure containing an array and a top variable. The array has a fixed capacity, limiting the number of elements that can be stored. The top variable indicates the position of the most recently added element. The two primary operations on an array-based stack are:

- **Push:** Adding a new element to the top of the stack involves placing the element at the current top position and updating the top variable.

- **Pop:** Removing the most recently added element from the top of the stack includes retrieving the element, decrementing the top variable, and effectively "ignoring" or overwriting the element in the array.

**Sample Code**

```c
    // Stack structure definition
    struct Stack {
        int array[CAPACITY];
        int top;
    };

    // Push operation
    void push(struct Stack* s, int value) {
        s->array[s->top++] = value;
    }

    // Pop operation
    int pop(struct Stack* s) {
        return s->array[--s->top];
    }

```

### Linked-List-Based Stack:

In a linked-list-based implementation, a stack is essentially a singly linked list with certain restrictions. The stack maintains a pointer to the head of the linked list, ensuring that elements can only be inserted or removed from the front. The primary operations are similar to those in the array-based implementation:

**Push:** Adding a new element to the stack involves creating a new node, setting its data, pointing its next to the current head, and updating the head.

**Pop:** Removing the most recently added element includes updating the head pointer to the second element and freeing the memory of the removed node.

**Sample Code**
```c
    // Node structure definition
    struct Node {
        int data;
        struct Node* next;
    };

    // Stack structure definition
    struct Stack {
        struct Node* head;
    };

    // Push operation
    void push(struct Stack* stack, int value) {
        struct Node* newNode = malloc(sizeof(struct Node));
        newNode->data = value;
        newNode->next = stack->head;
        stack->head = newNode;
    }

    // Pop operation
    int pop(struct Stack* stack) {
        int poppedValue;
        struct Node* temp = stack->head;
        
        poppedValue = temp->data;
        stack->head = temp->next;
        free(temp);

        return poppedValue;
    }
```