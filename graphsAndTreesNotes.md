# A **tree** is a hierarchical data structure composed of **nodes**

## **Root**: the top-most node (trees in CS go downwards). Every (non-empty) tree has one.
## **Parent**: the node connected directly above the current one. Every node (except for the root) has one.
## **Child**: a node connected below the current one. Each node can have zero or more.
## **Leaf**: a node that has no children.
## **Depth/Level**: the length of the path (edges) from the root to a node (depth/level of the root is 0).
## **Tree Height**: the maximum depth from from, of any node, in the tree.

# A tree commonly used in computing is a *binary tree*
## A binary tree consists of nodes that have at *most* two children.
## Commonly used in: data compression, file storage, game trees.

----
# Binary Tree Example

https://www.kosbie.net/cmu/fall-18/15-110/notes/trees-and-graphs.pdf

Check page 3:
Which node is the root? - The top-most one, node with value 84
Which nodes are the leaves? - 48, 37, 50, 53
Which nodes are *internal nodes*? - 84, 65, 96, 24
What is the height of this tree? - 3, consider the root is height 0, *the length of the longest path from root to a leaf is 3.*
----

# In general, Binary Trees can be:
## Empty
## A root node with:
	-a left binary tree
	-a right binary tree

## A common implementation of binary trees uses nodes
### Each node has a "left" node and a right "node"

## How to represent these nodes and pointers? With a class like *Struct...*

----

# Binary Search Tree (BST)

## A binary search tree is a binary tree with no duplicate nodes that imposes an *ordering* on it's nodes

## BST ordering invariant:
### all values of nodes in the left subtree of n are strictly *less than k*
### all values of nodes in the right subtree of n are strictlly *greater than k*

## BST ordering invariant: At *any* node with value k,
	all values of elements in the left subtree are strictly less than k AND
	all values of elements in the right subtree are strictly greater than k
(Assuming there are no duplicates in the tree)

--
# Insertion in a BST

## For each data value that you wish to insert into the binary search tree:
	-If you reach an empty tree (must test this first, why?), create a new leaf node with your value at that location
	-Recursively search the BST for your value until you either find it or reach an empty tree
	-If you find the value, throw an exception, **no duplicates allowed**

Insert: 84, 41, 96, 24, 37, 50, 13, 98
(page 12 for diagram!)
https://www.kosbie.net/cmu/fall-18/15-110/notes/trees-and-graphs.pdf 
--

# Graphs

## A graph is a data structure that contains a set of vertices and a set of edges which connect pairs of the vertices.
	-A vertex (or node) can be connected to any number of other vertices using edges
	-An edge may be bidirectional or direct (one-way)
	-An edge may have weight on it that indicates a cost for travelling over that edge in the graph

## Unlike trees, graphs can contain cycles
	-in fact, a tree is an **acyclic graph** (a graph without a cycle)

## Applications of Graphs: computer networks, transportation systems, social networks

*Graphs can be directed or undirected, a vertex is the labelled "point" and edges are the lines connected the vertices!*
--

# Graph implementation

## We usually represent graphs using a table (2D-list) where each clumn and row is associated with a specific vertex. This is called an *adjacency matrix.*

## A separate list of vertices shows that which vertex name (city, person, etc.) is associated with each index

## The values of the 2D list are the weights of the edges between the row vertices and column vertices
	-If there is not an edge between two vertices, use infinity of none to represent that!
--

# Graph Algorithms

## There are algorithms to search graphs efficiently for a value
-- Breadth-first Search
-- Depth-first Search

## There are algos to compute the shortest path between a start vertex and all the others:
-- Dijkstra's algorithm

## There are algos for *operations research*, which can be used to solve *network flow* problems
-- eg, how to efficiently distribute water through a system of pipes
--


# Shortest Path aka Dijkstra's algorithm
## Assign every node an initial distance (0 to the source, infinity for all others); mark all nodes as unvisited

## While there are unvisited nodes:
-- Select unvisited nodes with smallest distance (current)
-- consider all unvisited neighbors of current node
--- compute distance to each neighbor from current node
--- if less than current distance, replace with new distance
-- mark current node as visited (and never evaluate again)

