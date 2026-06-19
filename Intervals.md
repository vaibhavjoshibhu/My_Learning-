# 📊 Intervals Master Sheet (Interview Revision Guide)

Intervals are one of the most **high-frequency interview patterns**.
They combine **sorting + greedy + sometimes heap**.

---

# 0. When to Use Intervals?

```text id="in0"
Ask:

✔ Given ranges [start, end]?
✔ Overlapping intervals?
✔ Scheduling problems?
✔ Merging / inserting intervals?
✔ Minimum rooms / resources needed?
```

If YES → Intervals.

---

# 1. Core Idea ⭐

```text id="in1"
Sort intervals → process in order → merge / assign / count conflicts
```

---

# 2. Standard Interval Structure

```cpp id="in2"
struct Interval {
    int start;
    int end;
};
```

---

# 3. Always First Step ⭐⭐⭐

```text id="in3"
SORT by:
→ start time OR end time (depends on problem)
```

---

# 4. Core Interval Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Merge Intervals ⭐⭐⭐⭐

---

## Problem: Merge overlapping intervals

### Idea:

Merge if overlap exists.

```cpp id="in4"
sort(intervals.begin(), intervals.end());

vector<vector<int>> ans;

for(auto &it : intervals){

    if(ans.empty() || ans.back()[1] < it[0]){
        ans.push_back(it);
    }
    else{
        ans.back()[1] = max(ans.back()[1], it[1]);
    }
}
```

---

## Condition for overlap:

```text id="in5"
current.start <= previous.end
```

---

# Pattern 2: Insert Interval ⭐⭐⭐

```text id="in6"
Insert + merge in sorted list
```

Steps:

1. Add all before
2. Merge overlapping
3. Add remaining

---

# Pattern 3: Non-overlapping Intervals ⭐⭐⭐

```text id="in7"
Remove minimum intervals to avoid overlap
```

---

## Greedy logic:

```text id="in8"
Sort by end time → keep earliest finishing
```

---

# Pattern 4: Minimum Meeting Rooms ⭐⭐⭐⭐

---

## Idea:

```text id="in9"
Use Min Heap (end times)
```

---

## Algorithm:

```cpp id="in10"
sort by start time

priority_queue<int, vector<int>, greater<int>> pq;

for(interval : intervals){

    if(!pq.empty() && pq.top() <= interval.start)
        pq.pop();

    pq.push(interval.end);
}
```

---

## Result:

```text id="in11"
heap size = number of rooms needed
```

---

# Pattern 5: Meeting Rooms II ⭐⭐⭐⭐

Same as above.

---

# Pattern 6: Meeting Rooms I ⭐⭐⭐

```text id="in12"
Check if any overlap exists
```

---

# Pattern 7: Interval Scheduling (Greedy) ⭐⭐⭐⭐

---

## Idea:

```text id="in13"
Sort by end time → pick max non-overlapping
```

---

## Template:

```cpp id="in14"
sort by end;

int count = 0, lastEnd = -1;

for(interval : intervals){

    if(interval.start >= lastEnd){
        count++;
        lastEnd = interval.end;
    }
}
```

---

# Pattern 8: Interval Intersection ⭐⭐⭐

---

## Idea:

```text id="in15"
Two pointers
```

---

## Template:

```cpp id="in16"
while(i < n && j < m){

    start = max(a[i].start, b[j].start);
    end   = min(a[i].end, b[j].end);

    if(start <= end)
        add intersection;

    move smaller end pointer;
}
```

---

# Pattern 9: Sweep Line ⭐⭐⭐⭐

---

## Idea:

```text id="in17"
Convert intervals → events (start/end)
```

---

## Use cases:

* maximum overlap
* room requirements
* booking systems

---

# Pattern 10: Minimum Platforms (Classic) ⭐⭐⭐⭐

```text id="in18"
Sort arrivals & departures separately
```

---

# 5. Interval Patterns Summary

---

## Pattern A: Merge

```text id="in19"
Sort + combine overlapping
```

---

## Pattern B: Greedy Selection

```text id="in20"
Sort by end time
```

---

## Pattern C: Resource Allocation

```text id="in21"
Use heap for active intervals
```

---

## Pattern D: Two Pointer

```text id="in22"
Used in intersection problems
```

---

## Pattern E: Sweep Line

```text id="in23"
Convert to events
```

---

# 6. Complexity

```text id="in24"
Sorting → O(n log n)
Processing → O(n)
Heap → O(n log n)
```

---

# 7. Problem → Pattern Mapping

| Problem                   | Pattern       |
| ------------------------- | ------------- |
| Merge Intervals           | Merge         |
| Insert Interval           | Merge         |
| Non-overlapping intervals | Greedy        |
| Meeting Rooms I           | Overlap check |
| Meeting Rooms II          | Heap          |
| Interval Intersection     | Two pointers  |
| Minimum Platforms         | Sweep line    |
| Employee Free Time        | Merge + heap  |

---

# 8. Decision Rules ⭐⭐⭐

```text id="in25"
Intervals present?
→ Sort first ALWAYS

Need merging?
→ Merge pattern

Need minimum resources?
→ Heap

Need max overlap?
→ Sweep line

Need selection?
→ Greedy by end time
```

---

# 9. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="in26"
Interval problems = Sorting + Smart processing of ranges
```

---

# 10. ONE-LINE SUMMARY

```text id="in27"
Intervals = sorted range processing with greedy / heap / sweep-line logic
```

---
