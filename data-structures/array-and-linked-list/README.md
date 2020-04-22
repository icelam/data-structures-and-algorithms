# Array and Linked List

Array and Linked List are similar structures that used for storing list of data. The biggst different between them is how they are stored in **memory**. 

## Linked List
With a linked list, memory is assigned during runtime (at the time data is added to the list), nodes are store anywhere in memory. This is called **dynamic memory allocation**. Each item stores the address of the next item in the list. A bunch of random memory addresses are linked together.

## Array
Array consumes contiguous memory locations allocated at compile time(at the time of declaration of array), which is also known as **static memory allocation**.

## Performance 

|           | Array    | Linked List |
|-----------|:--------:|:-----------:|
| Reading   | $$O(1)$$ | $$O(n)$$    |
| Insertion | $$O(n)$$ | $$O(1)$$    |
| Deleteion | $$O(n)$$ | $$O(1)$$    |

#### Reading
* **Array:** Reading a item from array is fast, as the item can be directly accessed using *index*
* **Linked List:** To read a certain item from linked list, you will need to read the nodes sequentially to get the address of next node

#### Insertion
* **Array:** With a array, insertion operation takes more time, as the memory locations are consecutive and fixed. If memory is not enough, the whole block is shift to another location in the memory
* **Linked List:** New element of linked list is stored at the first available memory location, with only a single overhead step of storing the address of memory location in the previous node of linked list

#### Deleteion
* **Array:** Deleteion operation in an array involves shifting blocks of items together, as elements are stored in contiguous memory locations
*  **Linked List:** To delete an element from a linked list, the only operation is to change whiich memory location previous node point to

