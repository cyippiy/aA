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
* What are the steps for DFS on a graph?
    * For each vertex that you visit, you push on stack and keep searching until there's no new vertex that's been visited, then you pop off stack
* What supporting data structure might you use for BFS and DFS, respectively?
    * DFS
        * Stack
    * BFS
        * Queue
* What are the steps for BFS on a graph?
    * make a boolean array for each vertice in graph to represent visited. have a queue. check current node and push into queue, and change the boolean to true.
    while queue isn't empty, you print the front of the queue and then remove it, then check adjacent nodes. if adjacent node was not visited, mark it visited and put in queue.
* Give an example of a use-case for Topological Sort
    * builds. you can't run certain vertices without the dependancies first
* What is a difference between Topological Sort and DFS?
    * DFS looks for a node with no children. Topological doesn't care for order, but as long as there's no dependancies
* On which types of Graphs can we do a topological sort?
    * directional graphs
* What data structure do we use to assist with the topological sort algorithm?
    * stack
* Explain the steps of Djikstra shortest-path algorithm.
    * take source code, then check neighbors for path. you update map heap with the distance. you check if the path is shorter than current value and not null...then you update. otherwise ignore. , then update parent array with the value. then you update distance from source. once you're done, pop off the map heap and repeat
* What is the time complexity of Djikstra's algorithm?
    * O(Elog(V))
* What is a base case in recursion? Why do we need one? Do we always need one?
    * Base case solves the big problem in a smaller setting. recursion often calls itself so you don't want an infinite loop
* What exactly is a Stack Overflow?
    * stack overflow is when the stack is filled because the base case isn't addressed or solved
* Describe direct and indirect recursion
    * Direct is when the function calls itself
    * Indirect is when it calls another function directly or indirectly
* What is tail call recursion? Why is it helpful, if at all?
    * when the last thing executed is the recusive call
* Discuss advantages/disadvantages of recursion
    * Advantages
        * cleaner code
        * simpler
        * some problems are inherently 
    * Disadvantages
        * greater space requirement
        * greater time requirement
* How is memory allocated during recursive function calls?
    * when a function is called on main, it allocates memory on the stack and will pop off when the function finishes executing.
* What is the difference between Memoization and Tabulation?
    * Bottom up for solving DP vs memoization is top down 
    * avoids multiple lookups for tabulation
* Why is memoization helpful?
    * Can start from top and compare values of states until we get to the bottom most base state
    * avoids computing solutions to subproblems that are not needed, more inutitive to write
* What is an optimal substructure? When might a problem have one?
    * optimal substructure is when an optimal solution can be obtained by getting optimal solution of its subproblem
    * shortest path problem
        * from x to v is shortest path such as a combination of pathes from u to x and x to v are shortest
* What are the constraints of (any type of) Heap?
    * must be a complete biniary tree
        * all levels of tree must be completely filled
        * last level must have left-most nodes filled, always
    * root node must have all of its children either greater or equal to its children (min-heap) or less than or equal to its children (max-heap)
* What type of Data Structure might we use to implement a heap?
* What is the formula for getting the left child of a Heap root node? Right child?
    * 2i+1 for left child, 2i+2 for right child
* What is a Priority Queue?
    * queue data struture with additional properties. higher priority is dequeued before lower. otherwise removed based on their location in array