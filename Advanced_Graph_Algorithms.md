# 🌐 Graph Advanced Algorithms Master Sheet (Interview Revision Guide)

This sheet covers **advanced graph patterns beyond BFS/DFS basics**, focusing on **real interview + CP-level algorithms**.

---

# 0. When to Use Advanced Graph Algorithms?

```text id="ga0"
Ask:

✔ Shortest path in weighted graph?
✔ Need MST (minimum cost connection)?
✔ Detect bridges / articulation points?
✔ Multi-source / special BFS problems?
✔ “Cheapest / fastest / optimal path”?
✔ Graph with constraints + states?
```

If YES → Advanced Graphs.

---

# 1. Core Graph Mindset ⭐

```text id="ga1"
Graph problems = Nodes + Edges + Strategy of traversal/relaxation
```

---

# 2. Advanced Graph Algorithm Map ⭐⭐⭐⭐⭐

```text id="ga2"
1. Dijkstra (shortest path)
2. Bellman-Ford (negative weights)
3. Floyd-Warshall (all pairs)
4. MST (Kruskal / Prim)
5. DSU (Union-Find)
6. Topological sort (DAG)
7. 0-1 BFS
8. Bridges / Articulation points
9. SCC (Kosaraju / Tarjan)
```

---

# 🚀 3. Dijkstra’s Algorithm (Shortest Path)

---

## When to use:

```text id="ga3"
✔ Non-negative weights
✔ Single source shortest path
```

---

## Core Idea:

```text id="ga4"
Always pick node with smallest distance first
```

---

## Template:

```cpp id="ga5"
priority_queue<pair<int,int>,
vector<pair<int,int>>,
greater<pair<int,int>>> pq;

vector<int> dist(n, INF);
dist[src] = 0;
pq.push({0, src});

while(!pq.empty()){

    auto [d, node] = pq.top();
    pq.pop();

    if(d > dist[node]) continue;

    for(auto [adj, wt] : graph[node]){

        if(dist[node] + wt < dist[adj]){
            dist[adj] = dist[node] + wt;
            pq.push({dist[adj], adj});
        }
    }
}
```

---

## Complexity:

```text id="ga6"
O((V + E) log V)
```

---

# 🚀 4. Bellman-Ford Algorithm

---

## When to use:

```text id="ga7"
✔ Negative weights allowed
✔ Detect negative cycle
```

---

## Idea:

```text id="ga8"
Relax all edges V-1 times
```

---

## Template:

```cpp id="ga9"
for(int i = 0; i < V - 1; i++){
    for(auto edge : edges){

        if(dist[u] + w < dist[v]){
            dist[v] = dist[u] + w;
        }
    }
}
```

---

## Negative cycle check:

```text id="ga10"
If one more relaxation possible → cycle exists
```

---

# 🚀 5. Floyd-Warshall (All Pairs Shortest Path)

---

## When to use:

```text id="ga11"
✔ Small graph (V ≤ 500)
✔ Need all pairs shortest path
```

---

## Template:

```cpp id="ga12"
for(k = 0; k < n; k++){
    for(i = 0; i < n; i++){
        for(j = 0; j < n; j++){

            dist[i][j] =
            min(dist[i][j],
                dist[i][k] + dist[k][j]);
        }
    }
}
```

---

## Complexity:

```text id="ga13"
O(n³)
```

---

# 🚀 6. Minimum Spanning Tree (MST)

---

# A) Kruskal’s Algorithm ⭐⭐⭐⭐

---

## Idea:

```text id="ga14"
Pick smallest edges → avoid cycles
```

---

## Uses DSU:

```cpp id="ga15"
sort edges by weight;
for(edge : edges){

    if(find(u) != find(v)){
        union(u, v);
        add to MST;
    }
}
```

---

## Complexity:

```text id="ga16"
O(E log E)
```

---

# B) Prim’s Algorithm ⭐⭐⭐⭐

---

## Idea:

```text id="ga17"
Grow MST from one node using min heap
```

---

## Template:

```cpp id="ga18"
priority_queue<pair<int,int>,
vector<pair<int,int>>,
greater<pair<int,int>>> pq;

pq.push({0, start});
```

---

## Complexity:

```text id="ga19"
O(E log V)
```

---

# 🚀 7. DSU (Disjoint Set Union) ⭐⭐⭐⭐⭐

---

## Core Idea:

```text id="ga20"
Track connected components efficiently
```

---

## Template:

```cpp id="ga21"
int find(int x){
    if(parent[x] == x) return x;
    return parent[x] = find(parent[x]);
}

void unite(int a, int b){
    a = find(a);
    b = find(b);

    if(a != b)
        parent[b] = a;
}
```

---

## Optimizations:

```text id="ga22"
✔ Path compression
✔ Union by rank
```

---

# 🚀 8. Topological Sort (DAG) ⭐⭐⭐⭐

---

## When:

```text id="ga23"
✔ Directed acyclic graph
✔ dependency order problems
```

---

## Kahn’s Algorithm:

```cpp id="ga24"
queue<int> q;

for(node)
    if(indegree[node] == 0)
        q.push(node);
```

---

## Idea:

```text id="ga25"
Remove nodes with zero indegree
```

---

# 🚀 9. 0-1 BFS ⭐⭐⭐⭐

---

## When:

```text id="ga26"
Edge weights = 0 or 1
```

---

## Idea:

```text id="ga27"
use deque instead of priority queue
```

---

## Rule:

```text id="ga28"
0 weight → push front
1 weight → push back
```

---

# 🚀 10. Bridges & Articulation Points ⭐⭐⭐⭐⭐

---

## Purpose:

```text id="ga29"
Find critical edges/nodes in graph
```

---

## Idea:

```text id="ga30"
DFS + discovery time + low time
```

---

## Key concept:

```text id="ga31"
low[u] = earliest visited node reachable
```

---

# 🚀 11. Strongly Connected Components (SCC)

---

## Kosaraju Algorithm:

```text id="ga32"
1. DFS order stack
2. Reverse graph
3. DFS in stack order
```

---

## Use:

```text id="ga33"
Find strongly connected groups in directed graph
```

---

# 12. Graph Patterns Summary ⭐⭐⭐⭐⭐

---

## Pattern 1: Shortest Path

```text id="ga34"
Dijkstra / Bellman-Ford / Floyd
```

---

## Pattern 2: Connectivity

```text id="ga35"
DSU / BFS / DFS
```

---

## Pattern 3: MST

```text id="ga36"
Kruskal / Prim
```

---

## Pattern 4: Ordering

```text id="ga37"
Topological sort
```

---

## Pattern 5: Special BFS

```text id="ga38"
0-1 BFS
```

---

## Pattern 6: Graph structure analysis

```text id="ga39"
Bridges / SCC
```

---

# 13. Complexity Cheat Sheet

```text id="ga40"
Dijkstra → O(E log V)
Bellman-Ford → O(VE)
Floyd → O(V³)
Kruskal → O(E log E)
Prim → O(E log V)
DSU → O(α(n))
Topo sort → O(V+E)
```

---

# 14. Problem → Pattern Mapping

| Problem                      | Pattern        |
| ---------------------------- | -------------- |
| Shortest path                | Dijkstra       |
| Negative weights             | Bellman-Ford   |
| All pairs shortest           | Floyd          |
| Minimum spanning tree        | Kruskal / Prim |
| Cycle detection (undirected) | DSU            |
| Course schedule              | Topo sort      |
| 0-1 weighted shortest path   | 0-1 BFS        |
| Critical connections         | Bridges        |
| SCC grouping                 | Kosaraju       |

---

# 15. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="ga41"
Graph problems = choosing correct traversal + optimization strategy
```

---

# 16. ONE-LINE SUMMARY

```text id="ga42"
Advanced graphs = shortest path + connectivity + structure + optimization techniques
```

---
