# 1 Graphs

<img src="https://www.tutorialspoint.com/data_structures_algorithms/images/graph_basics.jpg">

A graph is a set of two collections:
- A collection of Vertices
- A collection of Edges

In above graph, you can see:
- Vertices: a, b, c, d, e
- Edges: ab, ac, bd, cd, de

## Use-Cases
Used almost everywhere in Computing, Science, Games, AI, ...
- Street Data
- Public Transport Data
- Connections on Linkedin
- Game States
- Menu States
- Dependency Graphs
- Pathfinding
- ...

## Terms

- **Vertex** (also: Node) - Each point or state of a graph
- **Edge** (also: Connection) - A path between two vertices
- **Adjacency** (also: Neighbor) - Two vertices are adjacent if they are connected through an edge
- **Path** - A sequence of edges between two vertices.

## Directed and Undirected

Graphs can be either directed or undirected.
In an undirected Graph, all Edges can be passed in both direction.
- e.g. you can go from a to b and also from b to a.

<img src="https://www.tutorialspoint.com/graph_theory/images/directed_graph.jpg">

In a directed graph, each connection has a clear from and to Edge. You can only navigate in one direction.
- e.g. a one-way street, which you can pass from North to South, but not from South to North.