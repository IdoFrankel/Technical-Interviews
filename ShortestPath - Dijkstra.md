
# Shortest Path
Computing Shortest Path from a single source: Dijkstra and Bellman-Ford

## Dijkstra's algorithm (option with degree of each vertex)
```
# n: Number of verices
# src = origin of path
# edges a list of travel times as directed edges times[i] = (ui, vi, wi)
def networkDelayTime(self, edges: List[List[int]], n: int, src: int) -> int:

    graph = collections.defaultdict(list)
    for u,v,w in edges:
        # remember: This is directed edge graph,
        if it was undirected, there was also the opposite edge
        graph[u].append((w,v))


    d = [float("inf")] * (n+1)
    d[src] = 0
    minHeap = [(0,src)]
    visited = set()

    while minHeap:
        g , u = heapq.heappop(minHeap)
        visited.add(u)

        for w2, v in graph[u]:
            if v in visited: continue

            if d[v] > g + w2:
                d[v] = g + w2
                heapq.heappush((d[v], v))

    res = max(d[1:]) #usually there isnt a 0 vertex
    return res if res != float("inf) else -1
```

# Bellman-Ford
```
#n: number of vertices (from 1 to n)
def Bellman_Ford(n):
    d = [float("inf)] * (n+1) # zero vertex is not in the graph

    for i in range(1, n):
        for u,v,w in edges:
            if d[v] > d[u] + w:
                d[v] = d[u] + w

```
