# Stacks and Queues

## Stacks
- First in Last Out: First item is last to be popped out
- Last in First Out: Last item to be added is first to be popped out
- Pushing a node is a `O(1)` operation
- Popping a node is a `O(1)` operation
- Peaking a node is a `O(1)` operation

### Push
1. Have node wanting to push a `next` to the top node of the stack
2. Reassign added node as `top`

### Pop
Check if stack `isEmpty` first
1. To remove the top node of a stack create a `temp` reference that points to the top
2. Reassign the `top` value to the `next` of the original top node
3. Pop original top node -> Clear out the `next` property in current `temp` reference

### Peek
Inspecting the top node of the stack

## Queue
- Enqueue : Nodes or items that are added to the queue.
- Dequeue : Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
- Front : This is the front/first Node of the queue.
- Rear : This is the rear/last Node of the queue.
- Peek : When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
- IsEmpty : returns true when queue is empty otherwise returns false.
- First in First Out
- Last in Last Out

### Enqueue O(1)
1. Set rear node's `next` to newly added noded. Referenc last node as `rear`. ==> Change `rear.next` to new node
2. Set new node as `rear
```
   node = new Node(value)
   rear.next <-- node
   rear <-- node
```
### Dequeue O(1)
1. Create `temp` to reference the `front`.
2. Reassign `front` to the `next` value of the front node.
3. Set the `temp.next` as null to disconnect the node from the queue

### Peek O(1)
`return front.value`
