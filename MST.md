# MST (Minimum Spanning Tree)
Prim and Kruskal algorithms.

# Kruskal Algorithm
Algorithm:
1. sort all edges in non monotonic decreaseing order (T = empty set)
2. iterate on sorted edges:
    - 1. if e closess a circle, don't add to T.
    - 2. else, add e to T
    - 3. return T

step 3 can be determine by UF (implementation in UF.MD)

```
# points - 
def kruskal_minHeap(points):
    n = len(points)
    edges = list()

    #initialize graph's edges according to points' input.
    for i in range(n):
        for j in range(i+1, n):
            u,v = points[i], points[j]
            w = distance(u,v)
            edges.append((w,i,j))


    # sort all edges
    heapq.heapify(edges)

    T = set()
    cost = 0
    uf = UF(n)
    while len(T) < n-1 or len(edges):
        w,u,v = heapq.heappop(edges)
        if uf.union(u,v):
            T.add((u,v))
            cost +=w
    
    # return T and its cost if an MST exists, else the graph is not fully connected.
    return (T,cost) if len(T) == n-1 else (None, None)

```


# Prim Algorithm

1. Initialize graph
2. Set Tree set with node #0
3. while size(T) != n
   - 1. Use BFS to take all the current vertices' neighbours, which don't belong to the tree.
   - 2. Among all those neighbours in the heap, select the minimal edge (this edge cross the cut with minimal weight).
   - 3. Add that edge to the Tree, and again, add all its neighbours to the heap.


```
# n: number of vertices
# edges: List[List[int]] # [w,u,v]
def prim(points):
    n = len(points)

    # initialize graph
    adj = { i:[] for i in range(n)}
    for i in range(n):
        x1,y1 = points[i]
        for j in range(i+1, n):
            x2, y2 = points[j]
            # w = distance(points[i], points[j])
            w = abs(x1 - x2) + abs(y1 - y2)
            adj[i].append([w, j])
            adj[j].append([w, i])

    #prims
    
    res = 0
    T = set()
    minH = [[0,0]] #cost, point
    heapq.heapify(minH)
    while len(T) < n:
        cost, i = heapq.heappop(minH)
        if i in T:
            continue
        res += cost
        T.add(i)
        for costNei, nei in adj[i]:
            if nei not in T:
                heapq.heappush(minH, [costNei, nei])
    return res
```


