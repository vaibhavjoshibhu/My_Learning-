# 🧠 Dynamic Programming (DP) Master Sheet — Interview Revision Guide

DP is the **most important + most feared + most asked pattern** in interviews.

But the truth is:

```text id="dp0"
DP = Recursion + Memoization + Optimization of repeated work
```

---

# 0. When to Use DP?

```text id="dp1"
Ask:

✔ Overlapping subproblems?
✔ Optimal substructure?
✔ "Count ways / min / max"?
✔ Choices at each step?
✔ Recursion feels repetitive?
```

If YES → DP.

---

# 1. Core Idea ⭐⭐⭐

```text id="dp2"
Solve once → store result → reuse later
```

---

# 2. DP Steps (ALWAYS FOLLOW THIS)

```text id="dp3"
1. Define state
2. Write recurrence
3. Base case
4. Store result (memo/table)
5. Optimize (optional)
```

---

# 3. DP Types Overview

```text id="dp4"
1D DP
2D DP
Knapsack DP
String DP
Grid DP
Tree DP
Interval DP
Bitmask DP
```

---

# 4. DP Forms

---

## A) Top-Down (Memoization) ⭐

```cpp id="dp5"
int solve(int i, vector<int>& dp){

    if(i <= 1)
        return i;

    if(dp[i] != -1)
        return dp[i];

    return dp[i] =
        solve(i-1, dp) +
        solve(i-2, dp);
}
```

---

## B) Bottom-Up (Tabulation)

```cpp id="dp6"
dp[0] = 0;
dp[1] = 1;

for(int i = 2; i <= n; i++){
    dp[i] = dp[i-1] + dp[i-2];
}
```

---

## C) Space Optimization ⭐

```cpp id="dp7"
int prev2 = 0, prev1 = 1;

for(int i = 2; i <= n; i++){

    int curr = prev1 + prev2;

    prev2 = prev1;
    prev1 = curr;
}
```

---

# 5. DP Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Fibonacci / Linear DP ⭐

```text id="dp8"
dp[i] depends on dp[i-1], dp[i-2]
```

Examples:

* Climbing stairs
* House robber
* Fibonacci

---

# Pattern 2: 0/1 Knapsack ⭐⭐⭐

```text id="dp9"
Take or not take
```

---

## Template

```cpp id="dp10"
dp[i][w] = max(
    dp[i-1][w],
    value[i] + dp[i-1][w - weight[i]]
);
```

---

# Pattern 3: Subset / Partition DP ⭐⭐⭐

```text id="dp11"
Can we split array into equal sum?
```

Examples:

* Partition equal subset sum
* Subset sum

---

# Pattern 4: LCS (String DP) ⭐⭐⭐⭐

```text id="dp12"
dp[i][j] = longest common subsequence
```

---

## Template

```cpp id="dp13"
if(s1[i-1] == s2[j-1])
    dp[i][j] = 1 + dp[i-1][j-1];
else
    dp[i][j] =
        max(dp[i-1][j],
            dp[i][j-1]);
```

---

# Pattern 5: Edit Distance ⭐⭐⭐⭐

```text id="dp14"
Insert / Delete / Replace
```

---

## Template

```cpp id="dp15"
dp[i][j] = min(
    insert,
    delete,
    replace
);
```

---

# Pattern 6: Grid DP ⭐⭐⭐

```text id="dp16"
dp[i][j] = ways to reach cell
```

---

## Example

```cpp id="dp17"
dp[i][j] =
    dp[i-1][j] +
    dp[i][j-1];
```

---

# Pattern 7: House Robber ⭐⭐⭐

```text id="dp18"
Take or skip adjacent
```

---

## Template

```cpp id="dp19"
dp[i] = max(
    dp[i-1],
    nums[i] + dp[i-2]
);
```

---

# Pattern 8: Longest Increasing Subsequence (LIS) ⭐⭐⭐⭐

```text id="dp20"
dp[i] = LIS ending at i
```

---

## O(n²) DP

```cpp id="dp21"
for(int i=0;i<n;i++){
    for(int j=0;j<i;j++){

        if(nums[j] < nums[i]){
            dp[i] = max(dp[i],
                        dp[j] + 1);
        }
    }
}
```

---

# Pattern 9: Matrix Chain Multiplication ⭐⭐⭐⭐

```text id="dp22"
Try all partitions
```

---

# Pattern 10: Interval DP ⭐⭐⭐⭐

```text id="dp23"
dp[l][r] = best answer in range l to r
```

Examples:

* Burst balloons
* Palindrome partitioning

---

# Pattern 11: Tree DP ⭐⭐⭐⭐

```text id="dp24"
dp[node] = function of children
```

Examples:

* Diameter
* Max path sum
* Robber on tree

---

# Pattern 12: Bitmask DP ⭐⭐⭐⭐⭐

```text id="dp25"
dp[mask][i]
```

Examples:

* TSP
* Assignment problems

---

# 6. DP Decision Tree ⭐

```text id="dp26"
Overlapping subproblems?
→ YES → DP

Choices at each step?
→ YES → Recursion DP

Need min/max?
→ Optimization DP

String problem?
→ LCS / Edit distance

Grid problem?
→ Grid DP

Subset problem?
→ Knapsack / Bitmask
```

---

# 7. Memoization Template ⭐

```cpp id="dp27"
int solve(int i, vector<int>& dp){

    if(base_case)
        return value;

    if(dp[i] != -1)
        return dp[i];

    return dp[i] =
        transition;
}
```

---

# 8. Tabulation Template ⭐

```cpp id="dp28"
dp[base] = value;

for(...){
    dp[i] = transition;
}
```

---

# 9. Complexity

```text id="dp29"
Time  : O(states × transitions)
Space : O(states)
```

---

# 10. Problem → Pattern Mapping

| Problem                | Pattern                  |
| ---------------------- | ------------------------ |
| Fibonacci              | 1D DP                    |
| Climbing Stairs        | 1D DP                    |
| House Robber           | 1D DP                    |
| Subset Sum             | Knapsack                 |
| Partition Equal Subset | Knapsack                 |
| LCS                    | String DP                |
| Edit Distance          | String DP                |
| LIS                    | DP / Binary optimization |
| Grid Unique Paths      | Grid DP                  |
| Burst Balloons         | Interval DP              |
| TSP                    | Bitmask DP               |
| Tree Diameter          | Tree DP                  |

---

# 11. MOST IMPORTANT INSIGHT ⭐⭐⭐⭐⭐

```text id="dp30"
DP is just:

"Recursion + remembering results"
```

---

# 12. FINAL DP MINDSET

```text id="dp31"
If recursion repeats same state →
convert to DP
```

---
