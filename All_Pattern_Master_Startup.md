# 🧠🔥 ALL DSA PATTERNS — ONE PAGE MASTER CHEAT SHEET (Ultimate Revision Map)

This is your **interview survival sheet**: when you see a problem → you should instantly map it to a pattern.

---

# 🚀 0. UNIVERSAL THINKING FRAME

```text id="core0"
Problem → Identify:

1. Data type? (array / string / tree / graph)
2. Need ordering? (sort / heap / stack)
3. Need search? (binary / hashmap / trie)
4. Need optimization? (DP / greedy)
5. Need structure? (graph / tree / DSU)
```

---

# 📊 1. ARRAY PATTERNS

```text id="p1"
✔ Prefix Sum → range sum, subarray sum
✔ Two Pointers → sorted array, pair problems
✔ Sliding Window → subarray with constraint
✔ Hashing → frequency, duplicates
✔ Difference Array → range updates
```

---

# 🪟 Sliding Window

```text id="p2"
Use when:
✔ contiguous subarray
✔ fixed or variable size window
```

---

# ⚡ Two Pointers

```text id="p3"
Use when:
✔ sorted array
✔ pair / triplet
✔ shrink-expand logic
```

---

# 🔢 Prefix Sum

```text id="p4"
Use when:
✔ range sum queries
✔ subarray sum = K
```

---

# 🧮 Hashing

```text id="p5"
Use when:
✔ frequency counting
✔ fast lookup
✔ duplicates / grouping
```

---

# 🔍 Binary Search

```text id="p6"
Use when:
✔ sorted / monotonic answer
✔ "minimum / maximum possible"
✔ search in answer space
```

---

# 🔁 BACKTRACKING

```text id="p7"
Use when:
✔ all combinations / permutations
✔ constraint-based exploration
```

---

# 🧠 DP

```text id="p8"
Use when:
✔ overlapping subproblems
✔ optimal substructure
```

---

## DP TYPES:

* 1D DP → house robber, fibonacci
* 2D DP → grid, knapsack
* DP on strings → LCS, edit distance
* DP on trees → subtree optimization
* Bitmask DP → subsets, TSP

---

# ⚡ GREEDY

```text id="p9"
Use when:
✔ local best → global best
✔ sorting helps decision
```

Examples:

* interval scheduling
* Huffman coding
* minimum platforms

---

# 🏔 HEAP

```text id="p10"
Use when:
✔ top K elements
✔ dynamic min/max
✔ streaming data
```

---

# 🔗 LINKED LIST

```text id="p11"
Patterns:
✔ fast/slow pointer
✔ reverse list
✔ merge lists
✔ cycle detection
✔ LRU cache
```

---

# 🌲 TREE PATTERNS

```text id="p12"
✔ DFS traversal
✔ BFS level order
✔ LCA
✔ subtree DP
✔ root-to-leaf paths
```

---

# 🌐 GRAPH PATTERNS

```text id="p13"
✔ BFS/DFS traversal
✔ Dijkstra → shortest path
✔ Bellman-Ford → negative weights
✔ Floyd → all pairs
✔ DSU → connectivity
✔ Topo sort → DAG ordering
✔ MST → Kruskal / Prim
```

---

# 🌲 TRIE

```text id="p14"
Use when:
✔ prefix search
✔ dictionary problems
✔ autocomplete
```

---

# 🧱 STACK / MONOTONIC STACK

```text id="p15"
Use when:
✔ next greater/smaller
✔ histogram
✔ span problems
✔ parentheses
```

---

# 📊 INTERVALS

```text id="p16"
✔ merge intervals
✔ scheduling
✔ overlap detection
✔ heap for rooms
```

---

# 🧮 BIT MANIPULATION

```text id="p17"
✔ XOR tricks
✔ subsets (bitmask)
✔ power of 2
✔ single number
```

---

# 📊 SEGMENT TREE / BIT

```text id="p18"
✔ range queries + updates
✔ prefix sums with updates
✔ min/max range queries
```

---

# 🧮 NUMBER THEORY

```text id="p19"
✔ gcd / lcm
✔ prime check
✔ sieve
✔ fast exponentiation
✔ modular arithmetic
```

---

# 🧠 SYSTEM DESIGN (DSA LEVEL)

```text id="p20"
✔ LRU → HashMap + DLL
✔ LFU → frequency maps
✔ queue/stack design
✔ rate limiter (queue)
```

---

# 🚀 FAST PATTERN DECISION FLOW

```text id="flow"
Array/String?
   ↓
Need subarray? → Sliding Window
Need range? → Prefix Sum
Need pair? → Two pointers
Need frequency? → Hashing

Sorted? → Binary Search / Greedy

Need best/top? → Heap

Need recursion? → Backtracking

Need optimal? → DP

Need structure? → Tree/Graph

Need prefix? → Trie

Need next greater? → Stack

Need intervals? → Sort + Merge/Heap

Need binary tricks? → Bit Manipulation

Need math? → Number Theory

Need updates + queries? → Segment Tree / BIT
```

---

# 🧠 FINAL INTERVIEW TRUTH

```text id="truth"
Every DSA problem is just:

👉 choose correct pattern
👉 apply template
👉 handle edge cases
```

---

# 🏁 ONE-LINE MASTER SUMMARY

```text id="final"
DSA = Pattern Recognition + Correct Data Structure + Standard Template
```

---

# 🚀 IF YOU WANT NEXT LEVEL

Here’s a **clean, structured roadmap (in correct learning sequence)** + **LeetCode problems for each stage** so you can actually master everything you covered.

---

# 🧭 COMPLETE DSA ROADMAP (LEETCODE-BASED)

## 🎯 Phase 0 — Foundation (Arrays + Strings Thinking)

### Learn:

* Loops, basic arrays
* Complexity (O, log n, etc.)
* Basic recursion idea

### Practice:

* 1. Two Sum — [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
* 217. Contains Duplicate — [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)
* 88. Merge Sorted Array — [https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)
* 283. Move Zeroes — [https://leetcode.com/problems/move-zeroes/](https://leetcode.com/problems/move-zeroes/)

---

# 🟢 Phase 1 — Core Array Patterns

## 1. Hashing

* 242. Valid Anagram — [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)
* 1. Two Sum (again but optimized)
* 49. Group Anagrams — [https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

---

## 2. Two Pointers

* 125. Valid Palindrome — [https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)
* 167. Two Sum II — [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
* 15. 3Sum — [https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)

---

## 3. Sliding Window

* 121. Best Time to Buy/Sell Stock — [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
* 3. Longest Substring Without Repeating Characters — [https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
* 209. Minimum Size Subarray Sum — [https://leetcode.com/problems/minimum-size-subarray-sum/](https://leetcode.com/problems/minimum-size-subarray-sum/)
* 239. Sliding Window Maximum — [https://leetcode.com/problems/sliding-window-maximum/](https://leetcode.com/problems/sliding-window-maximum/)

---

## 4. Prefix Sum

* 560. Subarray Sum Equals K — [https://leetcode.com/problems/subarray-sum-equals-k/](https://leetcode.com/problems/subarray-sum-equals-k/)
* 238. Product of Array Except Self — [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

---

# 🟡 Phase 2 — Searching + Sorting Logic

## Binary Search

* 704. Binary Search — [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)
* 33. Search in Rotated Sorted Array — [https://leetcode.com/problems/search-in-rotated-sorted-array/](https://leetcode.com/problems/search-in-rotated-sorted-array/)
* 875. Koko Eating Bananas — [https://leetcode.com/problems/koko-eating-bananas/](https://leetcode.com/problems/koko-eating-bananas/)
* 1011. Capacity To Ship Packages — [https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

---

## Greedy

* 55. Jump Game — [https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)
* 45. Jump Game II — [https://leetcode.com/problems/jump-game-ii/](https://leetcode.com/problems/jump-game-ii/)
* 435. Non-overlapping Intervals — [https://leetcode.com/problems/non-overlapping-intervals/](https://leetcode.com/problems/non-overlapping-intervals/)
* 452. Minimum Number of Arrows — [https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

---

# 🟠 Phase 3 — Stack + Heap + Intervals

## Stack / Monotonic Stack

* 20. Valid Parentheses — [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
* 155. Min Stack — [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)
* 739. Daily Temperatures — [https://leetcode.com/problems/daily-temperatures/](https://leetcode.com/problems/daily-temperatures/)
* 84. Largest Rectangle in Histogram — [https://leetcode.com/problems/largest-rectangle-in-histogram/](https://leetcode.com/problems/largest-rectangle-in-histogram/)

---

## Heap

* 215. Kth Largest Element — [https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)
* 347. Top K Frequent Elements — [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)
* 295. Find Median from Data Stream — [https://leetcode.com/problems/find-median-from-data-stream/](https://leetcode.com/problems/find-median-from-data-stream/)
* 23. Merge k Sorted Lists — [https://leetcode.com/problems/merge-k-sorted-lists/](https://leetcode.com/problems/merge-k-sorted-lists/)

---

## Intervals

* 56. Merge Intervals — [https://leetcode.com/problems/merge-intervals/](https://leetcode.com/problems/merge-intervals/)
* 57. Insert Interval — [https://leetcode.com/problems/insert-interval/](https://leetcode.com/problems/insert-interval/)
* 253. Meeting Rooms II — [https://leetcode.com/problems/meeting-rooms-ii/](https://leetcode.com/problems/meeting-rooms-ii/)

---

# 🔵 Phase 4 — Recursion + Backtracking

* 46. Permutations — [https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)
* 78. Subsets — [https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)
* 39. Combination Sum — [https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)
* 79. Word Search — [https://leetcode.com/problems/word-search/](https://leetcode.com/problems/word-search/)

---

# 🟣 Phase 5 — Linked List

* 206. Reverse Linked List — [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
* 141. Linked List Cycle — [https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)
* 19. Remove Nth Node — [https://leetcode.com/problems/remove-nth-node-from-end-of-list/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
* 143. Reorder List — [https://leetcode.com/problems/reorder-list/](https://leetcode.com/problems/reorder-list/)
* 146. LRU Cache — [https://leetcode.com/problems/lru-cache/](https://leetcode.com/problems/lru-cache/)

---

# 🌲 Phase 6 — Trees

* 104. Maximum Depth — [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
* 226. Invert Binary Tree — [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)
* 102. Level Order Traversal — [https://leetcode.com/problems/binary-tree-level-order-traversal/](https://leetcode.com/problems/binary-tree-level-order-traversal/)
* 236. Lowest Common Ancestor — [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
* 124. Binary Tree Maximum Path Sum — [https://leetcode.com/problems/binary-tree-maximum-path-sum/](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

---

# 🌐 Phase 7 — Graphs

* 200. Number of Islands — [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)
* 133. Clone Graph — [https://leetcode.com/problems/clone-graph/](https://leetcode.com/problems/clone-graph/)
* 207. Course Schedule — [https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)
* 994. Rotting Oranges — [https://leetcode.com/problems/rotting-oranges/](https://leetcode.com/problems/rotting-oranges/)

---

## Shortest Path / Advanced:

* 743. Network Delay Time — [https://leetcode.com/problems/network-delay-time/](https://leetcode.com/problems/network-delay-time/)
* 1631. Path With Minimum Effort — [https://leetcode.com/problems/path-with-minimum-effort/](https://leetcode.com/problems/path-with-minimum-effort/)

---

# 🧠 Phase 8 — Trie

* 208. Implement Trie — [https://leetcode.com/problems/implement-trie-prefix-tree/](https://leetcode.com/problems/implement-trie-prefix-tree/)
* 211. Design Add and Search Words — [https://leetcode.com/problems/design-add-and-search-words-data-structure/](https://leetcode.com/problems/design-add-and-search-words-data-structure/)
* 212. Word Search II — [https://leetcode.com/problems/word-search-ii/](https://leetcode.com/problems/word-search-ii/)

---

# 🧮 Phase 9 — Bit Manipulation

* 136. Single Number — [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
* 191. Number of 1 Bits — [https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)
* 338. Counting Bits — [https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)
* 78. Subsets (bit version)

---

# 📊 Phase 10 — Segment Tree / BIT (Advanced)

* 307. Range Sum Query Mutable — [https://leetcode.com/problems/range-sum-query-mutable/](https://leetcode.com/problems/range-sum-query-mutable/)
* 315. Count of Smaller Numbers After Self — [https://leetcode.com/problems/count-of-smaller-numbers-after-self/](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)

---

# 🧮 Phase 11 — Number Theory

* 204. Count Primes — [https://leetcode.com/problems/count-primes/](https://leetcode.com/problems/count-primes/)
* 50. Pow(x, n) — [https://leetcode.com/problems/powx-n/](https://leetcode.com/problems/powx-n/)
* 1492. The kth Factor of n — [https://leetcode.com/problems/the-kth-factor-of-n/](https://leetcode.com/problems/the-kth-factor-of-n/)

---

# 🏗 Phase 12 — System Design (DSA Level)

* 146. LRU Cache (again — MUST MASTER)
* 155. Min Stack
* 232. Implement Queue using Stacks
* 362. Design Hit Counter

---

# 🧭 FINAL LEARNING ORDER (IMPORTANT)

```text
1. Arrays + Hashing
2. Two pointers
3. Sliding window
4. Prefix sum
5. Binary search
6. Stack
7. Heap
8. Linked list
9. Trees
10. Graphs
11. Backtracking
12. DP
13. Trie
14. Bit manipulation
15. Intervals
16. Segment tree / BIT
17. Number theory
18. System design basics
```

---

# 🧠 REAL SUCCESS STRATEGY

```text
DO NOT learn randomly.

DO THIS:

1 topic → 10–15 problems → revisit templates → repeat
```

---

# 🧠🔥 INTERVIEW DAY REVISION CHEAT SHEET (DSA MASTER)

This is a **last-minute memory sheet** — you read this before interview to instantly recall patterns + templates.

---

# 🚀 0. GOLDEN RULE (MOST IMPORTANT)

```text id="iv0"
1. Identify pattern first
2. Recall template
3. Handle edge cases
4. Then code
```

---

# 📊 1. ARRAY + STRING CORE

## ✔ Hashing

```text id="iv1"
Use: frequency / duplicates / grouping
Tool: unordered_map
```

---

## ✔ Two Pointers

```text id="iv2"
Use: sorted array, pairs, palindrome

l = 0, r = n-1
move inward
```

---

## ✔ Sliding Window

```text id="iv3"
Use: subarray / substring problems

expand → contract
```

Template:

```text
while(r < n):
    add r
    while(invalid):
        remove l
```

---

## ✔ Prefix Sum

```text id="iv4"
Use: range sum / subarray sum

prefix[i] = sum(0..i)
```

---

# 🔍 2. SEARCHING + SORTING

## ✔ Binary Search

```text id="iv5"
Use:
- sorted array
- answer space (min/max)

l=0, r=n-1
mid = (l+r)/2
```

---

## ✔ Binary Search on Answer

```text id="iv6"
If asked:
"min possible / max possible"

→ check(mid)
→ shrink range
```

---

# 🧱 3. STACK PATTERN

## ✔ When to use

```text id="iv7"
Next greater / smaller
Parentheses
Histogram
```

---

## ✔ Monotonic Stack

```text id="iv8"
increasing → next smaller
decreasing → next greater
```

---

# 🏔 4. HEAP PATTERN

```text id="iv9"
Use for:
✔ top K
✔ kth element
✔ streaming
```

Template:

```text
min heap size K
push → pop if overflow
```

---

# 🔗 5. LINKED LIST

```text id="iv10"
Fast/slow pointer:
→ cycle
→ middle

Reverse:
prev, curr, next
```

---

# 🌲 6. TREE PATTERNS

## DFS Template

```text id="iv11"
if null return

left
right
process
```

---

## BFS Level Order

```text id="iv12"
queue
while not empty:
    process level
```

---

## LCA Idea

```text id="iv13"
search left + right
return root if both sides found
```

---

# 🌐 7. GRAPH CHEAT SHEET

## ✔ BFS / DFS

```text id="iv14"
visited array + queue/recursion
```

---

## ✔ Dijkstra

```text id="iv15"
priority_queue (min heap)
relax edges
```

---

## ✔ Topo Sort

```text id="iv16"
indegree + queue
```

---

## ✔ DSU

```text id="iv17"
find + union
cycle detection
```

---

# 🧠 8. BACKTRACKING

```text id="iv18"
choose → explore → unchoose
```

Used for:

* permutations
* subsets
* combinations

---

# 🧠 9. DP QUICK IDENTIFICATION

```text id="iv19"
If:
✔ overlapping subproblems
✔ choice at each step

→ DP
```

---

## DP types:

```text
1D → house robber
2D → grid / knapsack
string → LCS
tree → subtree DP
```

---

# ⚡ 10. GREEDY

```text id="iv20"
If local best leads to global best → greedy
```

Common clue:

```text
sorting helps decision
```

---

# 🧮 11. BIT MANIPULATION

```text id="iv21"
XOR trick:
a ^ a = 0

power of 2:
n & (n-1) == 0
```

---

# 📊 12. INTERVALS

```text id="iv22"
STEP 1: SORT

merge / heap / greedy
```

---

# 🌲 13. TRIE

```text id="iv23"
prefix search / dictionary
```

---

# 🧱 14. SEGMENT TREE / BIT

```text id="iv24"
Use when:
✔ range query + updates
```

---

# 🧮 15. NUMBER THEORY

```text id="iv25"
GCD → Euclid
Prime → sieve / sqrt
Power → fast exponentiation
Modulo → (a % m)
```

---

# 🚨 16. FAST PATTERN RECOGNITION

```text id="iv26"
Array → sliding window / prefix
Sorted → binary search / two pointers
Top K → heap
Parentheses → stack
Tree → DFS/BFS
Graph → BFS/DFS/Dijkstra
Substring → sliding window / trie
Subsequence → DP
Range query → segment tree / BIT
```

---

# 🧠 17. EDGE CASE CHECKLIST

```text id="iv27"
✔ empty input
✔ 1 element
✔ duplicates
✔ negative numbers
✔ overflow
✔ null pointers
```

---

# 🏁 18. INTERVIEW FLOW (VERY IMPORTANT)

```text id="flow"
Read problem →
    identify pattern →
        write brute force →
            optimize using DS/pattern →
                code clean →
                    test edge cases
```

---

# 🔥 19. FINAL 10-SECOND MEMORY TRICK

```text id="iv28"
SEE PROBLEM → THINK:

1. ARRAY?
2. SEARCH?
3. SUBARRAY?
4. TOP K?
5. ORDER?
6. GRAPH?
7. TREE?
```

---

# 🧠 ONE-LINE FINAL SUMMARY

```text id="final"
Interview success = pattern recognition + correct template + clean execution
```

---

👍 Good.

If you want to actually make this useful now, the next best step is simple:

* pick **1 topic per day**
* solve **5–10 problems from the roadmap**
* revise the **pattern sheet before sleeping**

