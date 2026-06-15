A graph is a set of vertices and the edges that connect those vertices. _All trees are graphs, but not all graphs are trees._
## Common Use Cases

| Use Case        | Vertex   | Edge       |
| --------------- | -------- | ---------- |
| Social Networks | User     | Connection |
| Road Maps       | Location | Road       |
| Networks        | Computer | Cable      |
| Game Dev        | Tile     | Path       |
| AI Decision     | State    | Action     |

## Properties

- Graphs can have any number of vertices.
- An undirected graph can have up to `n(n - 1)/2` edges for `n` vertices.
- Vertices can exist without edges but may be disconnected (and thus kinda useless)
- Typically graphs (with the exception of multigraphs) can only have a single edge between two vertices
- Weighted graphs assign values (costs) to edges (we'll cover this in a future course)
