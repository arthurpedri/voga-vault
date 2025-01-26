## Definition
- A linear ordering of vertices in a directed graph, such that for every directed edge *uv* from vertex *u* to vertex *v*, *u* comes before *v* in the ordering.
## Kahn's algorithm
- Iterates over a set of nodes with no incoming edges (S) (starting with the leaf nodes) until that set is empty.
- Every loop removes one of theses nodes from the list and puts it into a list with the sorted nodes (L).
- Remove all edges in the graph that go from the removed node to any other.
- If any of these nodes that got an edge removed is now a node with no incoming edges, add it to the set (S).
- When the loop exits, if the graph still has edges in it the graph has at least one cycle.
- If the graph has no edges left, (L) is a topologically sorted list of the nodes in the graph.