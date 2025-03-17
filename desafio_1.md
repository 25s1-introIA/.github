Here’s a classic **Let's Code** problem involving search methods:  

---

### **Problem: Robot Pathfinding**  
#### **Description:**  
A robot is placed in an `N x M` grid where some cells contain obstacles. The robot can move **up, down, left, or right**, but cannot pass through obstacles. The goal is to find the shortest path from the **starting position** `(sx, sy)` to the **destination** `(dx, dy)` using **BFS (Breadth-First Search)**.

#### **Input:**  
- The first line contains two integers `N` and `M` (`1 ≤ N, M ≤ 1000`), the dimensions of the grid.  
- The next `N` lines contain `M` characters each:  
  - `.` represents an empty cell.  
  - `#` represents an obstacle.  
- The last line contains four integers: `sx sy dx dy`, representing the robot’s start and destination positions (`0 ≤ sx, dx < N`, `0 ≤ sy, dy < M`).  

#### **Output:**  
- Print a single integer, the length of the shortest path from `(sx, sy)` to `(dx, dy)`, or `-1` if no path exists.  

#### **Example Input:**  
```
5 5
. . . # .
# # . # .
. . . . .
. # # # .
. . . . .
0 0 4 4
```

#### **Example Output:**  
```
8
```



[Resposta - (sem implementação)](./r_desafio_1.md)