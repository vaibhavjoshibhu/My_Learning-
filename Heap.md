# 🏔️ Heap / Priority Queue Master Sheet (Interview Revision Guide)

Heap is used when you need to **repeatedly get the smallest or largest element efficiently**.

It turns:

* repeated max/min queries → **O(log n) insert + O(log n) delete**

---

# 0. When to Use Heap?

```text id="hp0"
Ask:

✔ Need Top K elements?
✔ Need Kth largest/smallest?
✔ Need dynamic min/max?
✔ Need “always pick best next element”?
✔ Streaming data?
✔ Merge multiple sorted lists?
```

If YES → Heap.

---

# 1. Core Idea ⭐

```text id="hp1"
Always keep the BEST element on top
(min or max depending on problem)
```

---

# 2. Heap Types

---

## Min Heap (default in C++ priority_queue is max heap)

```cpp id="hp2"
priority_queue<int, vector<int>, greater<int>> pq;
```

## Max Heap

```cpp id="hp3"
priority_queue<int> pq;
```

---

# 3. Heap Basic Operations

```cpp id="hp4"
pq.push(x);     // O(log n)
pq.top();       // O(1)
pq.pop();       // O(log n)
```

---

# 4. Core Heap Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Top K Elements ⭐⭐⭐

---

## K Largest Elements

```cpp id="hp5"
priority_queue<int, vector<int>, greater<int>> pq;

for(int x : nums){

    pq.push(x);

    if(pq.size() > k)
        pq.pop();
}
```

---

## K Smallest Elements

```cpp id="hp6"
priority_queue<int> pq;
```

---

# Pattern 2: Kth Element ⭐⭐⭐

---

## Kth Largest

```cpp id="hp7"
priority_queue<int, vector<int>, greater<int>> pq;

for(int x : nums){

    pq.push(x);

    if(pq.size() > k)
        pq.pop();
}

return pq.top();
```

---

# Pattern 3: Heap for Streaming Data ⭐⭐⭐⭐

Used when data comes continuously.

---

## Median from Data Stream

```cpp id="hp8"
maxHeap → left half
minHeap → right half
```

---

## Idea:

```text id="hp9"
Balance both heaps
median = top of heaps
```

---

# Pattern 4: Merge K Sorted Lists ⭐⭐⭐⭐

```cpp id="hp10"
push first element of each list into min heap
```

---

## Template

```cpp id="hp11"
priority_queue<Node, vector<Node>, compare> pq;

for(each list)
    pq.push(head);

while(!pq.empty()){

    Node* curr = pq.top();
    pq.pop();

    add next node
}
```

---

# Pattern 5: Interval + Heap ⭐⭐⭐⭐

Used in scheduling problems.

---

## Example: Meeting Rooms II

```cpp id="hp12"
sort by start time

minHeap → store end times
```

---

## Logic:

```text id="hp13"
If new start >= smallest end → reuse room
else → add new room
```

---

# Pattern 6: Heap + Greedy Combo ⭐⭐⭐⭐⭐

```text id="hp14"
Always pick best available option
```

Examples:

* Huffman coding
* Optimal merge pattern
* Dijkstra algorithm

---

# Pattern 7: Dijkstra (Heap usage in graphs) ⭐⭐⭐⭐⭐

```cpp id="hp15"
priority_queue<pair<int,int>,
               vector<pair<int,int>>,
               greater<pair<int,int>>> pq;
```

---

## Idea:

```text id="hp16"
Always expand smallest distance node first
```

---

# Pattern 8: Frequency Heap ⭐⭐⭐

Used for “most frequent” problems.

---

## Top K Frequent Elements

```cpp id="hp17"
unordered_map<int,int> freq;

priority_queue<pair<int,int>> pq;
```

---

# 5. Classic Heap Problems

---

## 1. Kth Largest Element ⭐

```text id="hp18"
Min heap of size K
```

---

## 2. Top K Frequent Elements ⭐

```text id="hp19"
HashMap + Heap
```

---

## 3. Merge K Sorted Lists ⭐

```text id="hp20"
Min heap of nodes
```

---

## 4. Median from Stream ⭐⭐⭐⭐

```text id="hp21"
Two heaps (max + min)
```

---

## 5. Sliding Window Maximum ⭐⭐⭐⭐

```text id="hp22"
Monotonic deque (heap alternative)
```

---

## 6. Meeting Rooms II ⭐

```text id="hp23"
Min heap of end times
```

---

# 6. Heap vs Other Structures

| Task          | Use          |
| ------------- | ------------ |
| Fast max/min  | Heap         |
| Sorted data   | Tree / sort  |
| Random access | Array        |
| Lookup        | HashMap      |
| Range queries | Segment tree |

---

# 7. Heap Decision Rules ⭐⭐⭐

```text id="hp24"
Need smallest/largest repeatedly?
→ Heap

Need top K?
→ Heap

Need dynamic ordering?
→ Heap

Need greedy best choice repeatedly?
→ Heap
```

---

# 8. Complexity

```text id="hp25"
Insert → O(log n)
Delete → O(log n)
Top → O(1)
Build → O(n)
```

---

# 9. Problem → Pattern Mapping

| Problem            | Pattern         |
| ------------------ | --------------- |
| Kth Largest        | Heap            |
| Top K Frequent     | Heap + Hash     |
| Merge K Lists      | Heap            |
| Median Stream      | Two Heaps       |
| Dijkstra           | Heap + Graph    |
| Meeting Rooms II   | Heap + Interval |
| Sliding Window Max | Deque           |

---

# 10. Heap Mental Model ⭐⭐⭐

```text id="hp26"
Heap = always keep "best candidate ready on top"
```

---

# 11. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="hp27"
If you need repeated access to min/max → use Heap
```

---
