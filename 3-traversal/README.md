# 3 Traversal

Traversal in a Graph describes the process of traversing through all nodes beginning at a certain Node.

Since there is no Root-Node like in a Tree, the Node where we start traversing needs to picked.
- Usually, it's some node of interest, e.g. the Node that the User is located at
- But you may also pick the first node in the Node-List
- Or pick a Random Node

Traversal is used for several reasons:
- Either, you just want to traverse all nodes
- Or you want to find a certain Node from where you started

There are two major ways of traversing a Graph. But before we look at them, I'd like to mention, what they have in common and make an interesting observation.

## Don't Go There Twice

Graph Traversal Algorithms visit every Node only once. To make sure that they don't get trapped in endless cycles. Also, they don't want to waste resources or return Nodes twice.

## It's a Tree!

Look at the following two Traversal Algorithms that we will look at next:

<img src="https://www.tutorialspoint.com/data_structures_algorithms/images/breadth_first_traversal.jpg"><img src="https://www.tutorialspoint.com/data_structures_algorithms/images/depth_first_traversal.jpg">

- The continuous lines are connections between the Graph Nodes.
- The dotted lines are the lines showing, how the Graph was traversed.

Can you see, how the dotted lines shape a tree beginning at the Start-Node?

In other words: If you Traverse a Graph, you receive a Tree (Mind Blown!)

## Depth-First-Traversal

<img src="https://www.tutorialspoint.com/data_structures_algorithms/images/depth_first_traversal.jpg">

With this method of Traversal, we always pick the first adjacent neighbor that's available and follow that strategy deeper and deeper until we hit a Node that we have already visited. (That's why it's called Depth-First: we just keep on walking until we hit a dead-end)

If we do, then we don't visit that node, but instead visit the next adjacent neighbor.

If we have no more neighbors to visit, we go back one step and continue with that node's neighbors again.

```
visited_nodes = [start_node]
path = [start_node]

while path not empty
   found_next_node = false
   for each neighbor in path.peek().getNeighbors()
      if(neighbor in visited_nodes)
         continue
      else
         visited_nodes.add(neighbor)
         path.push(neighbor)
         found_next_node = true
         break
      end if
   end for
   if(not found_next_node)
      path.pop()
   end if
end while
```

- This is basically the same as Preorder-Traversal in a Binary Tree

Applications: Detecting Cycles in a Graph (Circular Dependencies), Some Search Algorithms, Topological Ordering, Solving Puzzles with only one Solution (With a variation, it can also find all Solutions)

## Breadth-First-Traversal

<img src="https://www.tutorialspoint.com/data_structures_algorithms/images/breadth_first_traversal.jpg">


With this method, we first look at all neighbors of the current node and then all (unvisited) neighbours of the previously visited neighbors and so on. We basically go Layer by Layer from inside to outside farther and farther away. First, we visit all Nodes with a Distance of 1. Then, all Nodes with a Distance of 2, etc.

```
visited_nodes = [start_node]
todo_nodes = [start_node]

while path not empty
   for each neighbor in todo_nodes.dequeue().getNeighbors()
      if(neighbor in visited_nodes)
         continue
      else
         visited_nodes.add(neighbor)
         todo_nodes.enqueue(neighbor)
      end if
   end for
end while
```

If you think of the Graph as a Tree, we're going Level by Level. Which is also, why:
- This is basically the same as Levelorder-Traversal in a Binary Tree

Applications: Shortest Path and Minimum Spanning Tree (Pathfinding), Torrent (P2P Networks), Google Crawler, Garbage Collection, GPS, Closest Connection on Linkedin, and many more

So, quite obviously, Breadth-First-Traversal seems to be the more important one.
