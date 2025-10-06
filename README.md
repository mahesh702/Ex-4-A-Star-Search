<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Mahesh N </h3>
<h3>Register Number: 2305001017        </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


1. **Start:** Input the graph `g` with edges (node1, node2, cost) and define heuristic values `h` for each node.
2. **Initialize:** Create a priority queue `q` containing a tuple `(f, g_cost, node, path)` starting with `(h[start], 0, start, [])`.
3. **Repeat until the queue is empty:**

   * Remove the node `u` with the smallest `f` value.
   * If `u` is the goal node, return the complete path.
   * If `u` is not visited, mark it as visited.
   * For each neighbor `x` of `u` with cost `c`:

     * If `x` is unvisited, calculate:

       * `g_cost_new = gc + c`
       * `f_new = g_cost_new + h[x]`
       * Push `(f_new, g_cost_new, x, path + [u])` into the queue.
4. **If the queue becomes empty and the goal is not found,** return “No path found.”
5. **End.**





## PROGRAM
```python

import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")

```

<hr>
<h2> Graph II</h2>
<hr>
<img width="370" height="397" alt="image" src="https://github.com/user-attachments/assets/16bca95a-b28d-440b-bd5d-d3d5fac658cf" />


<hr>
<h2> Input</h2>
<hr>
A B 3 <br>
A D 5 <br>
B C 4 <br>
C E 6 <br>
D F 1 <br>
E F 2 <br>
<hr>

OUTPUT

<img width="800" height="603" alt="496956715-957a9dc7-a3b0-4ab6-9833-5f72ef6d66af" src="https://github.com/user-attachments/assets/d4fd3537-e4c6-4bb5-9e7e-35dc1ba3fe06" />

## RESULT
Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.

