# Algorithms

## Graphs


* How do we define a graph mathematically?
    * ordered pairs. G = (V,E)
        * G: graph
        * V: vertices
            * V = { v1, v2, v3, ...}
        * E: edges
            * E = { {v1,v2}, {v1,v3}, {v1,v4} ... }
* What is the difference between directed, undirected, weighted, and unweighted?
    * directed edge
        * one way to travel, from origin to destination
    * undirected edge
        * bidirectional, origin and destination are not fixed
* Give an example of various types of graphs (Weighted Undirected, Unweighted Directed, Unweighted Undirected, etc.)
    * undirected graph
        * E = { {v1,v2}, {v1,v3}, {v1,v4} ... }
    * directed graph (digraph)
        * E = { (v1, v2), (v1, v3), (v2, v3) ... }
            * order matters, so left is origin, right is destination
    * weighted
        E = { {v1,v2,10}, {v1,v3,13} ... }
* What makes a graph a simple graph? What attributes would make it not simple?
    * graphs that do not have loops or parallel edges
        * self-loop has one edge and one vertice
        * multi-edge is another name for parallel
* What is the maximum number of edges in a directed simple graph? Undirected simple graph? Answer should be in terms of N
    * N(N-1) directed
    * (N(N-1))/2 undirected
* Describe the levels of connectivity a graph can have (strongly connected, weakly connected).
    * Strongly connected
        * there's a path from any vertex to any other vertex
* What are cycles?
    * cycle is when a vertex can travel
* What are some naive ways we can store and traverse graphs? Be able to discuss time/space complexity of these approaches, and what issues we may face.
    * have a list of vertex and edge list
    * can be simplier to have Edge list to reference the vertex list with the weight
    * O( |v| + |e| )
* Give a high level overview of an Adjacency Matrix
    * a two-axis symmetrical matrix (usually 2d array) that has a value when there's a edge for two vertices
* If we were only concerned about time complexity, is an Adjacency Matrix efficient? Why/why not?
    * lookup time is constant O(1)
    * finding adjacent nodes is O(V)
* If we were only concerned about space complexity, is an Adjacency Matrix efficient? Why/why not?
    * stores both edges and non-edges O(V^2)
    * only good for dense graphs 
* Give a high level overview of an Adjacency List
    * keeps track all connections/edges for each node. usually with linked lists
* What benefits do we get from an Adjacency List?
    * saves space with write. proportional to number of edges O(E)
    * faster lookup for adjacent nodes
        * social network is a great example for adjacency list