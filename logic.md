# Stepping through algorithm

## Find the shortest path from source to destination

Given a chessboard, find the shortest distance (minimum number of steps) taken by a knight 
to reach a given destination from a given source.

Input:
 
N = 8 (8 × 8 board)
Source = (7, 0)
Destination = (0, 7)
 
Output: Minimum number of steps required is 6

1. How would you like to describe the chessboard? Here it seems a square and so a graph.
  - Each square on the chessboard represents a node in the graph.
  - Two nodes are connected if a knight can move from one square to the other in one move.
Recall BFS,
```cpp
BFSTraversal(start_node):
  visited := a set to store references to all visited nodes

  queue := a queue to store references to nodes we should visit later
  queue.enqueue(start_node)
  visited.add(start_node)

  while queue is not empty:
    current_node := queue.dequeue()

    process current_node
    # for example, print(current_node.value)

    for neighbor in current_node.neighbors:
      if neighbor is not in visited:
        queue.enqueue(neighbor)
        visited.add(neighbor)
```
2. Initialize a queue for BFS traversal and a visited set to keep track of visited nodes.
3. Start from the source square, enqueue it into the queue, and mark it as visited.
4. Perform BFS (`min_knight_moves`):
  - Pop the front node from the queue.
  - Generate all possible moves from the current node (knight moves).
  - For each valid move, check if the destination is the target square. If yes, return the number of moves taken to reach that square.
  - If the destination is not reached, enqueue the valid moves into the queue (if they haven't been visited) and mark them as visited.

5. Repeat step 4 until you find the destination or the queue becomes empty.
   If the queue becomes empty and the destination is not reached, there is no valid path.
   
https://godbolt.org/z/397anfcnT

# Reference

https://www.educative.io/courses/mastering-algorithms-for-problem-solving-in-cpp
https://www.educative.io/answers/what-is-breadth-first-search
https://courses.engr.illinois.edu/cs225/sp2023/resources/bfs-dfs/
https://www.coursera.org/learn/programming-fundamentals#modules
