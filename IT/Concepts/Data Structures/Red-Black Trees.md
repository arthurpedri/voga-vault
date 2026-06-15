A _kind_ of binary search tree that solves the "balancing" problem. It contains a bit of extra logic to ensure that as nodes are inserted and deleted, the tree remains relatively balanced.
# Rules

In addition to all the rules of a Binary Search Tree, a red-black tree must follow some additional ones:

1. Each node is either red or black
2. The root is black. This rule is sometimes omitted. Since the root can always be changed from red to black, but not necessarily vice versa, this rule has little effect on analysis.
3. All `Nil` leaf nodes are black.
4. If a node is red, then both its children are black.
5. All paths from a single node go through the same number of black nodes to reach any of its descendant `NIL` nodes.
# Rotation

"Rotations" are what actually _keep a red-black tree balanced_. Every time one branch of the tree starts to get too long, we will "rotate" those branches to keep the tree shallow. A shallow tree is a healthy (fast) tree!

- A properly-ordered tree pre-rotation remains a properly-ordered tree post-rotation
- Rotations are `O(1)` operations
- When rotating left:
    - The "pivot" node's initial parent becomes its left child
    - The "pivot" node's old left child becomes its initial parent's new right child

Here's the process of a "left rotation":
![[leftrotationRBT.png]]