# Graphs

### Terminology
#### Vertex
A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
#### Edge
An edge is a connection between two nodes.
#### Neighbor
The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
#### Degree
The degree of a vertex is the number of edges connected to that vertex.

### Undirected Graphs
Undirected Graph is a graph where each edges is either undirected or bi-directional. => The undirected graph does not move in any direction.  

### Directed Graphs
Also known as Digraph, every edge is directed. Each node is directed at another node with a specific requirement of what node should be referenced next.

### Complete Graph
A complete graph is one which all nodes are connected to all other nodes.

### Connected Graph
Where all nodes have at least one edge.

### Disconnected Graph
Where some nodes do not have edges.

### Acyclic Graph
A directed graph that does not have cycles. Or when traversing does not return to itself. => Can be represented as a `tree`

### Cyclic Graph
Graph that cycles. A cycle is defined as a path of a positive length that starts and ends at the same vertex/node.

## Graph Representation

### Adjacency Matrix
An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix.

Each Row and column represents each vertex of the data structure. The elements of both the column and the row must add up to 1 if there is an edge that connects the two, 
or zero if there isn’t a connection.

### Adjacency List
An adjacency list is the most common way to represent graphs.

An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

Adjacency lists make it easy to view if one vertices connects to another.

### Weighted Graphs
A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights.
When representing a weighted graph in a matrix, you set the element in the 2D array to represent the actual weight between the two paths. If there is not a connection between 
the two vertices, you can put a 0, although it is known for some people to put the infinity sign instead.

## Traversing 

### Breadth First
- Start at a specific node/vertex.
- Traverse similar to traversing `tree`.
- In case of cyclic graph need a way of traveling visited nodes.

#### Algorithm
1. Enqueue the declared start node into the Queue.
2. Create a loop that will run while the node still has nodes present.
3. Dequeue the first node from the queue
4. if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.

```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)   

    return nodes;
```

### Depth First
#### Algorithm
1. Push the root node into the stack.
2. Start a while loop while the stack is not empty.
3. Peek at the top node in the stack.
4. If the top node has unvisited children, mark the top node as visited, and then Push any unvisited children back into the stack.
5. If the top node does not have any unvisited children, Pop that node off the stack.
6. Repeat until the stack is empty.

