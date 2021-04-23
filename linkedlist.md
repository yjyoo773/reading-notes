# Linked List
A data structure that contains nodes that links/points to the next node in the list.

### Singly
The numbeer of references the node has. `singly` linked list means that there is only one reference mad the reference points it the `next` node.

### Doubly
Doubly refers to there being two references within the node. A `doubly` linked list means that there is a reference to both the `next` and `previous` node.

### Head
The first node in the list.

### Current
The current node that the user is looking at. When traversing, setting the current at head allows to make sure user starts at the start of the list.

## Travsering a Linked List
Best approach is to traverse using a `while` loop such as until there is no next for the current node. 

### Traversal Big O
The time complexity for a linked list to check if a node exists in the linked list O(n). This is because the worst case to see if the node does not include the searching item
is *n* steps.  
The spacce complexity for a linked list to check if a node exists is O(1). This is due that no space is being added.

## Linked List Memory
Linked lists do not need to take up a single block of memory but can be scattered throughout and is a dynamic data structure. Meaning it can shrink and grow in memory.
