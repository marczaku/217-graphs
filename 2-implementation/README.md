# 2 Implementation

Let's look at ways of implementing Graphs.

## Adjacency Matrix

You could use a two-dimensional Array to store an Adjacency Matrix:

<img src="https://cdncontribute.geeksforgeeks.org/wp-content/uploads/undirectedgraph.png">

<img src="https://cdncontribute.geeksforgeeks.org/wp-content/uploads/adjacencymatrix.png">

```
class Graph<T>
   Node<T>[] nodes;
   bool[,] adjacency;

class Node<T>
   T value;
```

Instead of storing each connection as a class, you could look at the adjacency-matrix. e.g. to find out, whether node 2 and 3 are connected, you check whether `adjacency[2,3] == true`

- Pro: Very high Performance
- Con: Scales badly, especially for many Nodes and few Connections; Hard-To-Read Code; Bad performance when adding or removing Nodes

## Object-Oriented, Two Piles

Graphs can be implemented in an object-oriented manner, separating Nodes and Connections:

```
class Graph<T>
   Node<T>[] nodes;
   Connection[] connections;

class Node<T>
   T value;

class Connection
   Node from;
   Node to;
```

- Pro: Very intuitive
- Con: A lot of heap allocations, hard to check for neighbors of node; Also need an efficient way of looking up connections, else you'll need LinearSearch when finding Connections from a Node

## Object-Oriented, One Pile

Graphs can be implemented in an object-oriented manner, webbing it all together:

```
class Graph<T>
   Node<T>[] nodes;

class Node<T>
   T value;
   Node[] connections;
```

- Pro: Very intuitive, easy to use
- Con: You can't have a look at Connections without traversing the Nodes. Makes removing Nodes harder.

## Bonus: Procedural

Your Graph might not be fully instantiated, but it is progressively generated as one navigates through it:

```
class Node
   Node[] GetAdjacent()
```

Look at this example in C#:

```cs
// This is a very simple game-graph, where the player can always walk either left or right
public class Node {
   public int x;

   public Node(int x) { this.x = x;}

   // all possible connections from the current state are...
   public IEnumerable<Node> GetAdjacent() {
      // either a new node, where the player has moved left:
      yield return new Node(x-1);
      // or a new node, where the player has moved right:
      yield return new Node(x+1);
   }
}
```

This generates a Graph, that arguably looks like a Linked List:

```
...--Node(-2)--Node(-1)--Node(0)--Node(1)--Node(2)--Node(3)--...
```

## 2.5 Add, Remove, Find

These are all very simple operations, because the Graph only consists of a simple collection of Nodes. Of course, when removing Nodes, you need to make sure that you don't have Nodes still having connections to this node

## 2.6 Get Neighbors

This is the most common operation: We are at one Node and want to find out, what nodes are adjacent so we can evaluate, which one we want to evaluate next.
