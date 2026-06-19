# 🧠 Graphs Interview Master Sheet (Complete Revision Guide)

Graphs look scary, but almost every problem is just:

* DFS
* BFS
* Union-Find (DSU)
* Shortest Path (Dijkstra / Bellman-Ford)

---

# 0. Graph Representation

## Adjacency List (MOST COMMON)

```cpp id="g1"
vector<int> adj[N];
```

## Weighted Graph

```cpp id="g2"
vector<pair<int,int>> adj[N]; // {node, weight}
```

## Matrix Graph (Grid Problems)

```cpp id="g3"
int grid[n][m];
```

---

# 1. DFS Template ⭐

```cpp id="gdfs"
void dfs(int node, vector<int> adj[], vector<int>& vis){

    vis[node] = 1;

    for(int neigh : adj[node]){

        if(!vis[neigh]){
            dfs(neigh, adj, vis);
        }
    }
}
```

---

## Complexity

```text id="gc1"
Time  : O(V + E)
Space : O(V)
```

---

# 2. BFS Template ⭐ (Shortest in Unweighted Graph)

```cpp id="gbfs"
vector<int> bfs(int start, vector<int> adj[], int n){

    vector<int> vis(n,0);
    queue<int> q;

    q.push(start);
    vis[start] = 1;

    vector<int> order;

    while(!q.empty()){

        int node = q.front();
        q.pop();

        order.push_back(node);

        for(int neigh : adj[node]){

            if(!vis[neigh]){
                vis[neigh] = 1;
                q.push(neigh);
            }
        }
    }

    return order;
}
```

---

## Complexity

```text id="gc2"
Time  : O(V + E)
Space : O(V)
```

---

# 3. DFS vs BFS Use Cases

| DFS                  | BFS                        |
| -------------------- | -------------------------- |
| Connected components | Shortest path (unweighted) |
| Cycle detection      | Level order traversal      |
| Backtracking         | Multi-source expansion     |

---

# 4. Connected Components ⭐

```cpp id="gcomp"
int countComponents(int n, vector<int> adj[]){

    vector<int> vis(n,0);
    int cnt = 0;

    for(int i=0;i<n;i++){

        if(!vis[i]){
            cnt++;
            dfs(i, adj, vis);
        }
    }

    return cnt;
}
```

---

# 5. Cycle Detection (Undirected Graph)

```cpp id="gcycleu"
bool dfs(int node, int parent,
         vector<int> adj[],
         vector<int>& vis){

    vis[node] = 1;

    for(int neigh : adj[node]){

        if(!vis[neigh]){
            if(dfs(neigh, node, adj, vis))
                return true;
        }
        else if(neigh != parent){
            return true;
        }
    }

    return false;
}
```

---

# 6. Cycle Detection (Directed Graph) ⭐

```cpp id="gcycled"

bool dfs(int node,
         vector<int> adj[],
         vector<int>& vis,
         vector<int>& path){

    vis[node] = 1;
    path[node] = 1;

    for(int neigh : adj[node]){

        if(!vis[neigh]){
            if(dfs(neigh, adj, vis, path))
                return true;
        }
        else if(path[neigh]){
            return true;
        }
    }

    path[node] = 0;
    return false;
}
```

---

# 7. Topological Sort (Kahn BFS) ⭐

```cpp id="gtopo"
vector<int> topo(int n, vector<int> adj[]){

    vector<int> indeg(n,0);

    for(int i=0;i<n;i++){
        for(int x : adj[i])
            indeg[x]++;
    }

    queue<int> q;

    for(int i=0;i<n;i++){
        if(indeg[i]==0)
            q.push(i);
    }

    vector<int> order;

    while(!q.empty()){

        int node = q.front();
        q.pop();

        order.push_back(node);

        for(int neigh : adj[node]){

            indeg[neigh]--;

            if(indeg[neigh]==0)
                q.push(neigh);
        }
    }

    return order;
}
```

---

# 8. DSU (Disjoint Set Union) ⭐⭐⭐

```cpp id="gdsu"

class DSU{

public:

    vector<int> parent, rank;

    DSU(int n){
        parent.resize(n);
        rank.resize(n,0);

        for(int i=0;i<n;i++)
            parent[i]=i;
    }

    int find(int x){

        if(parent[x]==x)
            return x;

        return parent[x]=find(parent[x]);
    }

    void unite(int a, int b){

        a = find(a);
        b = find(b);

        if(a != b){

            if(rank[a] < rank[b])
                swap(a,b);

            parent[b]=a;

            if(rank[a]==rank[b])
                rank[a]++;
        }
    }
};
```

---

## Complexity

```text id="gdsuc"
Almost O(1) (inverse Ackermann)
```

---

# 9. Dijkstra Algorithm ⭐

```cpp id="gdij"
vector<int> dijkstra(int src, vector<pair<int,int>> adj[], int n){

    vector<int> dist(n,1e9);
    priority_queue<pair<int,int>,
                   vector<pair<int,int>>,
                   greater<pair<int,int>>> pq;

    dist[src]=0;
    pq.push({0,src});

    while(!pq.empty()){

        int d = pq.top().first;
        int node = pq.top().second;
        pq.pop();

        for(auto it : adj[node]){

            int neigh = it.first;
            int w = it.second;

            if(d + w < dist[neigh]){

                dist[neigh] = d + w;

                pq.push({dist[neigh], neigh});
            }
        }
    }

    return dist;
}
```

---

## Complexity

```text id="gdi"
Time  : O((V+E) log V)
Space : O(V)
```

---

# 10. Bellman-Ford (Negative Weights)

```cpp id="gbf"
vector<int> bellman(int n, vector<vector<int>>& edges, int src){

    vector<int> dist(n,1e9);
    dist[src]=0;

    for(int i=0;i<n-1;i++){

        for(auto e : edges){

            int u=e[0], v=e[1], w=e[2];

            if(dist[u]!=1e9 &&
               dist[u]+w < dist[v]){
                dist[v]=dist[u]+w;
            }
        }
    }

    return dist;
}
```

---

## Complexity

```text id="gbfc"
Time  : O(V * E)
Space : O(V)
```

---

# 11. Floyd Warshall (All Pairs Shortest Path)

```cpp id="gfw"

for(int k=0;k<n;k++){
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){

            dist[i][j] =
            min(dist[i][j],
                dist[i][k] + dist[k][j]);
        }
    }
}
```

---

## Complexity

```text id="gfwc"
Time  : O(n^3)
Space : O(n^2)
```

---

# 12. Grid BFS (VERY IMPORTANT)

```cpp id="gg1"
int dx[4] = {1,-1,0,0};
int dy[4] = {0,0,1,-1};

queue<pair<int,int>> q;
```

```cpp id="gg2"
while(!q.empty()){

    auto [x,y] = q.front();
    q.pop();

    for(int i=0;i<4;i++){

        int nx = x + dx[i];
        int ny = y + dy[i];

        if(valid(nx,ny) && !vis[nx][ny]){
            vis[nx][ny]=1;
            q.push({nx,ny});
        }
    }
}
```

---

# 13. Multi-Source BFS ⭐

```cpp id="gmulti"
queue<pair<int,int>> q;

for(all sources){
    q.push(source);
    vis[source]=1;
}
```

---

# 14. Graph Patterns Cheat Sheet

| Problem Type               | Pattern          |
| -------------------------- | ---------------- |
| Traversal                  | DFS / BFS        |
| Shortest path (unweighted) | BFS              |
| Shortest path (weighted)   | Dijkstra         |
| Negative weights           | Bellman-Ford     |
| All pairs shortest path    | Floyd Warshall   |
| Cycle detection            | DFS / DSU        |
| Connected components       | DFS              |
| Ordering problems          | Topological sort |
| Dynamic grouping           | DSU              |
| Grid problems              | BFS / DFS        |
| Multi-source spread        | BFS              |

---

# 15. Problem → Pattern Mapping

| Problem                   | Pattern               |
| ------------------------- | --------------------- |
| Number of Islands         | DFS/BFS               |
| Rotten Oranges            | Multi-source BFS      |
| Word Ladder               | BFS                   |
| Course Schedule           | Topo Sort             |
| Detect Cycle (directed)   | DFS + recursion stack |
| Detect Cycle (undirected) | DFS / DSU             |
| Shortest Path             | Dijkstra              |
| Cheapest Flights          | Dijkstra / Bellman    |
| Pacific Atlantic Water    | DFS                   |
| Clone Graph               | DFS/BFS               |
| Bipartite Graph           | BFS/DFS coloring      |
| Alien Dictionary          | Topo Sort             |

---

# 16. Ultimate Graph Decision Tree

```text id="gdt"
Is graph weighted?
    ├── NO → BFS
    └── YES
         ├── negative edges? → Bellman-Ford
         └── no → Dijkstra

Need ordering?
    → Topological Sort

Need grouping?
    → DSU

Need connected components?
    → DFS/BFS

Need grid movement?
    → BFS/DFS

Need shortest path?
    → BFS / Dijkstra
```

---

# 17. Final Insight ⭐⭐⭐

```text id="gfinal"
Graphs are NOT about memorizing problems.

They are about recognizing 6 patterns:

1. DFS
2. BFS
3. Dijkstra
4. Bellman-Ford
5. Topological Sort
6. DSU
```

---
