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

Would you like me to modify the code to print this kind of visualization? 😃