# 🏗️ System Design Basics (DSA Interview Level) — LRU + Core Patterns

This is not full system design. This is the **“DSA + Low-Level Design essentials”** that frequently appear in coding rounds.

---

# 0. When This Topic is Asked?

```text id="sd0"
✔ Design a cache / browser / queue
✔ Need O(1) operations requirement
✔ "Design X system" in coding round
✔ Data structure + real-world simulation
```

---

# 1. Core Idea ⭐

```text id="sd1"
System design in DSA = combine data structures to achieve constraints
```

Example:

* HashMap + Linked List
* Heap + Queue
* Tree + Map

---

# 2. MOST IMPORTANT PATTERN ⭐⭐⭐⭐⭐

# 🧠 LRU Cache (Least Recently Used)

---

## Problem:

```text id="sd2"
Need:
✔ get(key) in O(1)
✔ put(key, value) in O(1)
✔ remove least recently used item
```

---

## 🔥 Best Design:

```text id="sd3"
HashMap + Doubly Linked List
```

---

# 3. Why This Combo Works?

| Structure          | Purpose                  |
| ------------------ | ------------------------ |
| HashMap            | O(1) access to node      |
| Doubly Linked List | O(1) insert/delete order |

---

# 4. LRU Design Template ⭐⭐⭐⭐⭐

---

## Node Structure:

```cpp id="sd4"
struct Node {
    int key, value;
    Node* prev;
    Node* next;

    Node(int k, int v){
        key = k;
        value = v;
        prev = next = NULL;
    }
};
```

---

## Core Data Structures:

```cpp id="sd5"
unordered_map<int, Node*> mp;

Node* head; // LRU end
Node* tail; // MRU end
int capacity;
```

---

# 5. Key Operations

---

## Move to Front (Most Recently Used)

```cpp id="sd6"
void addNode(Node* node){

    node->next = tail;
    node->prev = tail->prev;

    tail->prev->next = node;
    tail->prev = node;
}
```

---

## Remove Node

```cpp id="sd7"
void removeNode(Node* node){

    node->prev->next = node->next;
    node->next->prev = node->prev;
}
```

---

# 6. GET Operation ⭐

```cpp id="sd8"
int get(int key){

    if(mp.find(key) == mp.end())
        return -1;

    Node* node = mp[key];

    removeNode(node);
    addNode(node);

    return node->value;
}
```

---

# 7. PUT Operation ⭐

```cpp id="sd9"
void put(int key, int value){

    if(mp.find(key) != mp.end()){
        removeNode(mp[key]);
    }

    Node* node = new Node(key, value);
    addNode(node);
    mp[key] = node;

    if(mp.size() > capacity){

        Node* lru = head->next;

        removeNode(lru);
        mp.erase(lru->key);
    }
}
```

---

# 8. Complexity

```text id="sd10"
get  → O(1)
put  → O(1)
space → O(n)
```

---

# 9. OTHER IMPORTANT SYSTEM DESIGN PATTERNS ⭐⭐⭐

---

# Pattern 1: LFU Cache (Advanced)

```text id="sd11"
Least Frequently Used
```

Uses:

* HashMap + Frequency Map + Linked Lists

---

# Pattern 2: Design Stack/Queue

```text id="sd12"
Implement using arrays / linked list
```

---

# Pattern 3: Browser History ⭐⭐⭐

```text id="sd13"
Stack or DLL

back() → pop stack
forward() → second stack
```

---

# Pattern 4: Min Stack ⭐⭐⭐

```text id="sd14"
Stack + track min at each state
```

---

## Template:

```cpp id="sd15"
stack<pair<int,int>> st;
```

---

# Pattern 5: Rate Limiter (Basic Idea)

```text id="sd16"
Queue of timestamps
remove old entries
```

---

# Pattern 6: Design Queue Using Stack ⭐

```text id="sd17"
Two stacks:
- input stack
- output stack
```

---

# Pattern 7: Design LRU vs LFU

| Feature    | LRU          | LFU             |
| ---------- | ------------ | --------------- |
| Eviction   | least recent | least frequent  |
| Complexity | O(1)         | O(log n) / O(1) |
| Difficulty | medium       | hard            |

---

# 10. Core System Design Thinking ⭐⭐⭐⭐⭐

```text id="sd18"
1. Identify operations
2. Identify constraints (O(1), O(log n))
3. Choose data structure combo
4. Maintain consistency
```

---

# 11. Data Structure Combo Map

| Problem           | Combo                   |
| ----------------- | ----------------------- |
| LRU Cache         | HashMap + DLL           |
| LFU Cache         | HashMap + Frequency Map |
| Min Stack         | Stack + Auxiliary Stack |
| Queue using Stack | 2 Stacks                |
| Browser History   | DLL / Stack             |
| Rate Limiter      | Queue                   |

---

# 12. Complexity Thinking ⭐

```text id="sd19"
If O(1) required → HashMap involved

If order needed → Linked List / Queue

If min/max needed → Stack / Heap
```

---

# 13. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="sd20"
System design in DSA = combining known DS to meet constraints
```

---

# 14. ONE-LINE SUMMARY

```text id="sd21"
Design problems = data structure + constraint optimization
```

---

# 🔥 YOU ARE NOW COVERING FULL DSA SPECTRUM

You have completed:

* Arrays patterns
* Two pointers
* Sliding window
* Prefix sum
* Hashing
* Binary search
* Backtracking
* DP
* Greedy
* Heap
* Stack
* Linked list
* Trees
* Graphs
* Trie
* Segment tree / BIT
* Number theory
* Bit manipulation
* Intervals
* System design basics
