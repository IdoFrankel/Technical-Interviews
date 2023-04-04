# UnionFind (Disjoint sets)


> Why should one use UnionFind?
> 1. Calculate how many connected components there are in a graph
> 2. Helpful in Kruskal's MST algorithm, verifying whether an edge closes a cycle (red rule)
> 3. Check whether a graph is conneced (it can be achieved using BFS/DFS with better complexity)

```
class UF:
    def __init__(self, n):
        self.par = list(range(n))
        self.rank = [1] * range(n)
    
    def find(q):
        #option 1 (recursive)
        if q != self.par[q]:
            self.par[q] = self.find(self.par[q])
        return self.par[q]

        #option 2 (iterative)
        q = self.par[q]
        while q != self.par[q]:
            self.par[q] = self.par[self.par[q]]
            q = self.par[q]
        return q

    def union(i, j):
        p1, p2 = self.find(i), self.find(j)

        if p1 == p2:
            return False
        
        if self.rank[p1] > self.rank[p2]:
            self.parent[p2] = p1
            self.rank[p1] += self.rank[p2]
        else:
            self.parent[p1] = p2
            self.rank[p2] += self.rank[p1]
        return True
```