# BTH004 Final Review

## Topic 1 Algorithm Design

### Overview

- An algorithm can be described as a step-by-step set of operations to be performed in order to accomplish some task.

- Optimization problem

  - aim
    - to find an optimal (or at least "good enough") solution among all possible solutions
  - model
    - Parameters
    - Decision variables
    - Objective function
    - Constraint
  - e.g shortest path, knapsack problem

- Heuristics algorithm

  - Does not guarantee to find the optimal solution A heuristics usually generates a “good” solution within a reasonable

    amount of time.

### Greedy Algorithm

- A natural, and common type of constructive heuristics is greedy algorithms.

#### Huffman's algorithm

- Huffman coding

### Improving Search Algorithm

#### Neighborhood search

- The choice of an appropriate neighborhood is problem specific and is often a trade-off between solution quality and solving time.

#### The knapsack problem

#### Meta heuristics

- Tabu search
- Simulated annealing

### Divide-and-conquer

#### Recursion

#### Divide-and-conquer

#### Mergesort

### Dynamic Programming (Concept needed in Exam)

## Topic 2 Graph Algorithm

### Definitions

- What is a graph?
  - A graph is a set of objects that are connected to each other through links.
- Degree
  - Indegree
  - Outdegree
- Path, simple path
  - A path which not contains a same vertex more than once
- DAG (Directed acyclic graph)
  - Contains no cycles
- Connected undirected graph （连通图）
- Strongly connected directed graph （强连通图）（judge by two times DFS iteration)
- Weakly connected directed graph （弱连通图）
- Complete graph （完全图）

### Minimum Spanning Tree

- Tree
- Forest
- Spanning Tree, MST
  - Kruskal: choose edge
  - Prim: choose node

### Representations of Graphs

- Adjacency matrix, Adjacency list

### Shortest Path

- Dijkstra's algorithm

### Topological Sort

- There is no topological ordering of a cyclic graph! (Why?)
  - There is no node can be considered as a previous node of other nodes

## Topic 3 Complexity Analysis

- Analysis - correctness and performance

### Complexity Analysis

- The complexity of an algorithm is usually described as a function f (n) of the input size n.
- Average-case, Worst-case
- Amortized Analysis
- O(f ), Ω(f ), and Θ(f )
  - The O(f ), Ω(f ), and Θ(f ) notations are used to present the complexity of an algorithm. They take into account the input size, and are independent on the algorithm imprecision, programming language, computer used, etc

### Complexity Classes

![img](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628150649.jpeg)

- P problem
- NP problem
- How to show that a problem is N P complete
  1. Since P1 is NP complete, all other problems R in NP can be polynomially reduced to P1.
  2. Show that P1 can be polynomially reduced to P2.
  3. By transitity, all problems R in NP can be polynomially reduced to P2. Because R can be reduced to P1, and P1 can be reduced to P2.
  4. Hence P2 is NP complete

### Amotized Analysis

## Topic 4 Advanced Data Structures

### BST

### AVL tree

### Splay tree

### RB tree

### Suffix arrays and suffix trees

![Screen Shot 2021-01-14 at 1.33.27 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628150654.png)

![Screen Shot 2021-01-14 at 1.33.41 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628150658.png)