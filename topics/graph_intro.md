
# Introduction to Graph / Network Theory

What is a graph?
* A collection of interconnected nodes

Toy Example of Karate Club
```python

import numpy as np
import random
import networkx as nx
from IPython.display import Image
import matplotlib.pyplot as plt

# Load the graph
G_karate = nx.karate_club_graph()
# Find key-values for the graph
pos = nx.spring_layout(G_karate)
# Plot the graph
nx.draw(G_karate, cmap = plt.get_cmap('rainbow'), with_labels=True, pos=pos)
```

### Terminology
* `Nodes`
* `Edges`
* `Neighbors`
* `Degree` - number of neighbors
* A graph is `complete` if all nodes have (n-1) neighbors
* A `path` is from i to j is a sequence of edges that goes from i to j.
* The `diameter` of a graph is the longest path of all the shortest paths that link any 2 nodes.
* The geodesic path is the shortest path between 2 nodes
* A graph is `connected` if all nodes can be reached by a given path.
* A graph is `directed` if edges are directional
* A graph is `cyclic` if you can return to a given node, but `acyclyic` if this isn't true for at least one node.
* A graph can be weighted, either on nodes or Edges
* A graph is sparse if the number of edges is large compared to the number of nodes, but dense if there are many more Edges
