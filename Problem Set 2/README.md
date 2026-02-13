# Constrained Campus Pathfinding

A graph-based shortest-path system for navigating the MIT campus. Implements a directed graph with weighted edges and a depth-first search with branch-and-bound pruning that finds the shortest route subject to a maximum outdoor distance constraint.

## Implementation

### Graph Module (`graph.py`)

- `Node` — campus building with name-based equality and hashing
- `Edge` — directed connection between two nodes
- `WeightedEdge(Edge)` — adds total distance and outdoor distance weights
- `Digraph` — directed graph with node and edge management, validation, and string representation. Includes `__eq__`, `__hash__`, and `__str__` dunder methods. Contains its own unit tests (`TestGraph` class)

### Pathfinding (`ps2.py`)

- `load_map()` — parses a campus map file into a Digraph
- `get_best_path()` — recursive depth-first search with branch-and-bound pruning. Prunes branches where the current distance exceeds the best known distance, and checks the outdoor distance constraint at each step
- `directed_dfs()` — wrapper that validates inputs and initializes the search

Includes 8 unit tests covering normal paths, no-path scenarios, and constraint-violation cases.
