# Week 10 Coding #8: Haunted Hotel Sweep

## Summary

This assignment uses a graph to represent a haunted hotel where each area is a node and hallways or doors are edges. The program includes helper functions to explore the hotel safely using graph traversal algorithms. BFS (Breadth-First Search) explores nearby rooms level by level using a queue, while DFS (Depth-First Search) explores deeply through one path at a time using a stack. A `visited` set is important because it prevents infinite loops in graphs that contain cycles and stops the program from revisiting the same area repeatedly.

---

## Approach

- Used `graph.get(area, [])` in `get_neighbors` to safely return neighbors or an empty list if the area does not exist.
- Used BFS traversal with a queue in `has_path` to check whether a target area can be reached from the start area.
- Used a `visited` set in every traversal function to avoid revisiting areas and getting stuck in cycles.
- Implemented `bfs_order` using `collections.deque` for efficient queue operations.
- Implemented `dfs_order` using a stack and `reversed()` neighbor traversal so DFS follows the required neighbor order.
- Implemented `count_reachable_areas` using BFS traversal to count all unique reachable areas.

---

## Complexity

### `get_neighbors`

- Time: O(1) average
- Space: O(1)
- Why: Dictionary lookup is constant time on average and no extra data structures are created.

### `has_path`

- Time: O(V + E)
- Space: O(V)
- Why: In the worst case, every area (vertex) and hallway (edge) is visited once. The queue and visited set can store up to all vertices.

### `bfs_order`

- Time: O(V + E)
- Space: O(V)
- Why: BFS visits each vertex and edge once. The queue and visited set may contain all vertices.

### `dfs_order`

- Time: O(V + E)
- Space: O(V)
- Why: DFS visits each vertex and edge once. The stack and visited set may contain all vertices.

### Stretch: `count_reachable_areas`

- Time: O(V + E)
- Space: O(V)
- Why: The traversal may visit every vertex and edge once, while the visited set stores reachable vertices.

---

## Edge-Case Checklist

- [x] empty graph
- [x] missing start area
- [x] missing target area
- [x] `start == target`
- [x] graph with a cycle
- [x] disconnected graph
- [x] area with no neighbors

### Notes

One tricky edge case was handling graphs with cycles. Without a `visited` set, the traversal could loop forever between connected areas. Another important case was making sure functions return empty results when the start area does not exist.

---

## Tests Added

- Added cycle graph tests for BFS and DFS
- Added isolated area tests for traversal functions
- Added disconnected component tests
- Added empty graph tests
- Added reachable area count tests

---

## Known Limitations

No known limitations.

---

## Assistance & Sources

AI used? Yes

If yes, explain what it helped with:

- explanations
- debugging
- test ideas
- syntax reminders
- README formatting

Other sources used:

- Python documentation for `collections.deque`
- Course notes and lecture examples