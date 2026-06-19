# 🧠 Greedy Algorithm Master Sheet (Interview Revision Guide)

Greedy is the pattern where you make the **best possible choice at every step**, hoping it leads to a global optimum.

Unlike DP, Greedy does **NOT reconsider decisions**.

---

# 0. When to Use Greedy?

```text id="gr0"
Ask:

✔ Can I make a local choice that feels optimal?
✔ Does sorting help simplify decision making?
✔ Do subproblems not depend on future states?
✔ Is there a clear “best choice” at each step?
```

If YES → Greedy might work.

---

# 1. Core Idea ⭐

```text id="gr1"
Pick the best immediate option → never go back
```

---

# 2. Greedy vs DP (VERY IMPORTANT)

| Greedy            | DP                              |
| ----------------- | ------------------------------- |
| One decision path | Many paths                      |
| No backtracking   | Stores all states               |
| Fast (O(n))       | Slower (O(n²), O(nk))           |
| Needs proof       | Always correct if state defined |

---

# 3. Greedy Template ⭐⭐⭐

```cpp id="gr2"
sort(arr.begin(), arr.end());

for(each item){

    if(is_best_choice(item)){
        take(item);
    }
}
```

---

# 4. Core Greedy Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Sorting-Based Greedy ⭐

```text id="gr3"
Sort → pick in order → eliminate conflicts
```

### Used in:

* Activity selection
* Interval scheduling
* Merge intervals

---

## Example: Activity Selection

```cpp id="gr4"
sort by end time;

int lastEnd = -1;

for(interval : intervals){

    if(interval.start > lastEnd){
        take interval;
        lastEnd = interval.end;
    }
}
```

---

# Pattern 2: Interval Greedy ⭐⭐⭐

```text id="gr5"
Sort by start or end
```

### Problems:

* Merge intervals
* Non-overlapping intervals
* Minimum rooms

---

## Merge Intervals

```cpp id="gr6"
sort(intervals);

for(each interval){

    if(ans.empty() || ans.back().end < curr.start){
        ans.push_back(curr);
    }
    else{
        ans.back().end = max(ans.back().end, curr.end);
    }
}
```

---

# Pattern 3: Jump / Reach Greedy ⭐⭐⭐

```text id="gr7"
Maintain farthest reachable point
```

### Example: Jump Game

```cpp id="gr8"
int far = 0;

for(int i = 0; i < n; i++){

    if(i > far)
        return false;

    far = max(far, i + nums[i]);
}
```

---

# Pattern 4: Heap Greedy ⭐⭐⭐⭐

```text id="gr9"
Use priority queue to always pick best option
```

### Problems:

* Huffman coding
* Top K elements
* Meeting rooms

---

# Pattern 5: Two Pointer Greedy ⭐⭐⭐

```text id="gr10"
Sort + left/right decisions
```

### Example:

* Container with most water
* Pair sum problems

---

# Pattern 6: Min/Max Greedy ⭐⭐⭐

```text id="gr11"
Always pick min or max depending on goal
```

### Examples:

* Minimum coins
* Gas station
* Candy distribution

---

# Pattern 7: Assignment Greedy ⭐⭐⭐

```text id="gr12"
Sort + assign optimally
```

### Examples:

* Assign cookies
* Job scheduling
* Classroom scheduling

---

# 5. Classic Greedy Problems

---

## 1. Activity Selection ⭐

```text id="gr13"
Sort by end time → pick non-overlapping
```

---

## 2. Jump Game ⭐

```text id="gr14"
Track farthest reachable index
```

---

## 3. Merge Intervals ⭐

```text id="gr15"
Sort + merge overlapping
```

---

## 4. Gas Station ⭐

```text id="gr16"
If total gas < cost → impossible
Track running balance
```

---

## 5. Coin Change (Greedy valid only sometimes)

```text id="gr17"
Pick largest coin first
```

⚠ Works only for canonical coin systems.

---

# 6. Greedy Decision Rules ⭐⭐⭐

```text id="gr18"
If sorting helps → Greedy

If local choice never breaks future → Greedy

If choice affects future states → DP (NOT greedy)
```

---

# 7. Greedy Proof Idea (VERY IMPORTANT)

```text id="gr19"
To justify greedy:

Show swapping property:
"Any optimal solution can be converted to greedy solution"
```

---

# 8. Complexity

```text id="gr20"
Sort: O(n log n)
Traverse: O(n)
Total: O(n log n)
```

---

# 9. Problem → Pattern Mapping

| Problem            | Pattern            |
| ------------------ | ------------------ |
| Activity Selection | Sorting + Greedy   |
| Merge Intervals    | Interval Greedy    |
| Jump Game          | Reach Greedy       |
| Gas Station        | Balance Greedy     |
| Assign Cookies     | Two pointer Greedy |
| Huffman Coding     | Heap Greedy        |
| Meeting Rooms      | Interval Greedy    |
| Min Platforms      | Heap / Sweep       |

---

# 10. Greedy Decision Tree ⭐

```text id="gr21"
Can I sort and pick locally best?
        ↓
YES → Try Greedy

Does future depend on current choice?
        ↓
YES → DP (NOT Greedy)
```

---

# 11. FINAL GREEDY INSIGHT ⭐⭐⭐⭐⭐

```text id="gr22"
Greedy works when:

"Locally best = globally best"
```

---

# 12. FINAL ONE-LINE SUMMARY

```text id="gr23"
Greedy = make the best immediate decision without looking back
```

---
