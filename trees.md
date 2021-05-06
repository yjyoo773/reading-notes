# Trees

## Terminology
- _Node_ - A Tree node is a component which may contain it’s own values, and references to other nodes
- _Root_ - The root is the node at the beginning of the tree
- _K_ - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
- _Left_ - A reference to one child node, in a binary tree
- _Right_ - A reference to the other child node, in a binary tree
- _Edge_ - The edge in a tree is the link between a parent and child node
- _Leaf_ - A leaf is a node that does not have any children
- _Height_ - The height of a tree is the number of edges from the root to the furthest leaf

## Traversing
### Depth First
prioritize going through the depth (height) of the tree first.
- Pre-order: root -> left -> right
- In-order: left -> root -> right
- Post-order: left -> right -> root

#### Pre-order
```
// INPUT <-- root node
// OUTPUT <-- pre-order output of tree node's values
  OUTPUT <-- root.value

  if root.left is not NULL
      preOrder(root.left)

  if root.right is not NULL
      preOrder(root.right)
```
#### In-order
```
// INPUT <-- root node
// OUTPUT <-- in-order output of tree node's values

    if root.left is not NULL
        inOrder(root.left)

    OUTPUT <-- root.value

    if root.right is not NULL
        inOrder(root.right)
```
#### Post-order
```
// INPUT <-- root node
// OUTPUT <-- post-order output of tree node's values

    if root.left is not NULL
        postOrder(root.left)

    if root.right is not NULL
        postOrder(root.right)

    OUTPUT <-- root.value
```

### Breadth First
Traversing the tree going through each level of the tree node-by-node.
```
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while breadth.peek()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    if front.left is not NULL
      breadth.enqueue(front.left)

    if front.right is not NULL
      breadth.enqueue(front.right)
```

### K-ary Tress
Trees that have more than 2 child nodes.  
==> Breadth First Travel    
Similar to binary but pushing nodes into a queue with a list of children length of `k`

### Binary Search Tree
All values smaller than the `root` is placed to the left and those greater are placed on the right. Big O is `O(h)` where h is the hieght. Space
complexity is `O(1)`.
