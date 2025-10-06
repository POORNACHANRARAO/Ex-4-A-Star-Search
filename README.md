<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:kunam poorna chandra rao      </h3>
<h3>Register Number: 2305001012          </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
 
 1.Initialize the open list
 
 Open list ← priority queue (min-heap)

 Closed list ← empty set

 Insert the start node into the open list with:

g = 0

h = heuristic(start)

f = g + h

2.While Open list is not empty:

.Remove the node q with the lowest f from the open list.

.If q is the goal node, return the path (reconstruct from parents).

.If q is already in the Closed list, skip it.

.Add q to the Closed list.

3.For each neighbor n of q:

.Compute:

g(n) = g(q) + cost(q, n)

h(n) = heuristic(n)

f(n) = g(n) + h(n)

.If n is not in Closed list:

Insert (f(n), g(n), n, path_so_far) into Open list.

4.If goal is never reached and Open list becomes empty:

Return "No path found".

## PROGRAM


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





SAMPLE GRAPH I

 <img width="529" height="553" alt="Screenshot 2025-10-06 142500" src="https://github.com/user-attachments/assets/3837cd34-223d-4030-b118-94378774cb76" />



INPUT

A B 3

A D 5

B C 4

C E 6

D F 1

E F 2


<hr>


Sample Output

<img width="779" height="451" alt="Screenshot 2025-10-06 142824" src="https://github.com/user-attachments/assets/92e68148-ba34-4fa8-aca0-48605388e470" />






<hr>


## RESULT

Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.
