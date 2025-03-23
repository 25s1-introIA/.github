Here’s a step-by-step visualization of how the BFS algorithm finds the shortest path.  

---

### **Example Grid:**
```
5 5
. . . # .
# # . # .
. . . . .
. # # # .
. . . . .
0 0 4 4
```
- `.` = Open space (walkable)
- `#` = Obstacle (not walkable)
- `S` = Start position `(0,0)`
- `D` = Destination `(4,4)`

---

### **Step-by-Step BFS Path Expansion:**
Each number represents the number of steps taken from the start.

```
S  1  2  #  .  
#  #  3  #  .  
5  4  3  4  .  
6  #  #  #  .  
7  8  7  6  D  
```
📌 **Path taken (Shortest Route)**  
```
(0,0) → (0,1) → (0,2) → (1,2) → (2,2) → (2,3) → (2,4) → (3,4) → (4,4)
```
✅ **Total steps:** **8**  

---

### **Final Path Representation:**
```
S  →  →  #  .  
#  #  ↓  #  .  
.  .  ↓  →  →  
.  #  #  #  ↓  
.  .  .  .  D  
```
This is how BFS expands and finds the shortest path efficiently! 🚀  

```python
import sys
from collections import deque

def bfs(grid, N, M, sx, sy, dx, dy):
    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # Up, Down, Left, Right
    queue = deque([(sx, sy, 0)])  # (x, y, distance)
    visited = set()
    visited.add((sx, sy))
    
    while queue:
        x, y, dist = queue.popleft()
        
        if (x, y) == (dx, dy):
            return dist
        
        for dx, dy in directions:
            nx, ny = x + dx, y + dy
            if 0 <= nx < N and 0 <= ny < M and grid[nx][ny] == '.' and (nx, ny) not in visited:
                visited.add((nx, ny))
                queue.append((nx, ny, dist + 1))
    
    return -1  # No path found

def main():
    # Reading input
    N, M = map(int, sys.stdin.readline().split())
     grid = [input().strip().split() for _ in range(N)]
    sx, sy, dx, dy = map(int, sys.stdin.readline().split())
    
    # Solving the problem
    result = bfs(grid, N, M, sx, sy, dx, dy)
    print(result)

if __name__ == "__main__":
    main()

```