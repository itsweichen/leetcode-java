[TOC]

# Tree and Graph

## Tree

### Basics

* length = #edges
* depth = length of the path from n to the root
* height = length of the path from n to its deepest descendent

### Traversal

* Preorder - LC144
* Postorder - LC145
* Inorder for binary tree - LC94
* level-order (BFS) - LC102

Example: SubTree.

```java
class SibTreeNode {                  |  class SibTree {    
  Object item;                       |    SibTreeNode root;
  SibTreeNode parent;                |    int size;        
  SibTreeNode firstChild;            |  }                  
  SibTreeNode nextSibling;           |
}                                    |
```

```
        +
       / \         Preorder:  + * 3 7 ^ 4 2
      /   \
     *     ^        Inorder:  3 * 7 + 4 ^ 2
    / \   / \
   3   7 4   2    Postorder:  3 7 * 4 2 ^ +
```

```java
class SibTreeNode {
    public void preorder() {
        this.visit();
        if (firstChild != null) firstChild.preorder();
        if (nextSibling != null) nextSibling.preorder();
    }
    
    public void postorder() {
        if (firstChild != null) firstChild.postorder();
        this.visit();
        if (nextSibling != null) nextSibling.postorder();
    }
}
```

## Binary Search Tree

**Binary search tree invariant**: for any node X, every key in the left subtree of X is less than or equal to X's key, and every key in the right subtree of X is greater than or equal to X's key.

* BST can be used as an implementation of an ordered dictionary.

**Operations**

* `find`
* `min` / `max`
* `insert` - follows the `find` and inserts where there is null.
* `remove` - depending on whether the node has children. If the node has two children, you should find the smallest key in the right subtree and replace it.

**Complexity**

In a perfectly balanced binary with height h, the number of nodes n is $2^{(h+1)} - 1$.

No node has depth greater than log2n, so for the operations it takes O(logn) in worst case. On the other hand, these operations can take linear time of the tree is severaly imbalanced.

## Graph

### Representation

1. Adjacency matrix

```
          1 2 3 4 5 6                           Alb Ken Eme Ber Oak Pie
        1 - - - T - -                    Albany  -   T   -   T   -   -
        2 T - - - - -                Kensington  T   -   -   T   -   -
        3 - T - - - T                Emeryville  -   -   -   T   T   -
        4 - - - - T -                  Berkeley  T   T   T   -   T   -
        5 - T - - - T                   Oakland  -   -   T   T   -   T
        6 - - T - - -                  Piedmont  -   -   -   -   T   -
```

2. Adjacency list

```
      ---   -----                       ---   ------   ------
    1 |.+-> | 4 |                Albany |.+-> |Ken.+-> |Ber*|
      ---   =====                       ===   ======   ======
    2 |.+-> | 1 |            Kensington |.+-> |Alb.+-> |Ber*|
      ---   =====----                   ===   ======   ======
    3 |.+-> | 2 | 6 |        Emeryville |.+-> |Ber.+-> |Oak*|
      ---   =====----                   ===   ======   ======   ------   ------
    4 |.+-> | 5 |              Berkeley |.+-> |Alb.+-> |Ken.+-> |Eme.+-> |Oak*|
      ---   =====----                   ===   ======   ======   ======   ------
    5 |.+-> | 2 | 6 |           Oakland |.+-> |Eme.+-> |Ber.+-> |Pie*|
      ---   =====----                   ===   ======   ------   ------
    6 |.+-> | 3 |              Piedmont |.+-> |Oak*|
      ---   -----                       ---   ------
```

Choose the right way to store it depending on whether it's a sparse graph or complete graph.



### Traversals

* BFS
* DFS

```python
# BFS
bfs(Vertex u):
    for (each vertex v in V):
        v.visited = false
    u.visit(null)
    q = new Queue()
    q.enqueue(u)
    while (q is not empty):
        v = q.dequeue()
        for (each vertex w s.t. (v, w) is an edge in E):
            if (!w.visited):
                w.visit(v)
                w.visited = true
                q.enqueue(w)

# DFS
dfs(Vertex u):
    u.visit()
    u.visited = true
    for (each vertex v such that (u, v) is an edge in E):
        if (!u.visited):
            dfs(v)
```

