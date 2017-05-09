# Trees

## Tree Terminology

- Path: sequence of nodes along the edges of a tree
- Root: node at the top of the tree
- Parent: any node except the root node has one edge upward to a node called parent.
- Child: the node below a given node connected by its edge downward is called its child node.
- Siblings: nodes that share the same parent.
- Leaf: node without any child node.
- Subtree: descendants of a node.
- Depth: length of the path from the root.
- Height: maximum depth of the tree.

## Types of Trees

- Binary: Each node has zero, one, or two children. This assertion makes many tree operations simple and efficient.
- Binary Search: A binary tree where any left child node has a value less than its parent node, and any right child node has a value greater than or equal to that of its parent node.

## Tree Traversal

Three different methods are possible for binary trees: preorder, postorder, and in-order, which all do the same three things: recursively traverse both the left and right subtrees and visit the current node. The difference is when the algorithm visits the current node:

- Preorder: Current node, left subtree, right subtree
- Postorder: Left subtree, right subtree, current node
- In-order: Left subtree, current node, right subtree

## Balancing

- Red-Black Trees
- B Trees
- B+ Trees