# 🔁 Backtracking Master Sheet (Interview Revision Guide)

Backtracking is the pattern for **“try all possibilities with constraints”**, where you:
👉 explore choices
👉 build a solution step-by-step
👉 undo (backtrack) when invalid or after exploring

---

# 0. When to Use Backtracking?

```text id="bt0"
Ask:

✔ Need all possible answers?
✔ Need combinations / permutations / subsets?
✔ Decision tree / explore choices?
✔ Constraints + multiple paths?
✔ "Find all ways" type problems?
```

If YES → Backtracking.

---

# 1. Core Idea ⭐

```text id="bt1"
Choose → Explore → Unchoose
```

---

# 2. Standard Backtracking Template ⭐⭐⭐

```cpp id="bt2"
void backtrack(state){

    if(base_case){
        save_answer();
        return;
    }

    for(choice in choices){

        if(valid(choice)){

            make_choice(choice);

            backtrack(new_state);

            undo_choice(choice); // BACKTRACK
        }
    }
}
```

---

# 3. Key Components

```text id="bt3"
1. State (current path)
2. Choices (options available)
3. Constraints (valid or not)
4. Base case (when solution complete)
```

---

# 4. Backtracking Flow

```text id="bt4"
Start → Pick → Go deeper → Undo → Try next
```

---

# 5. Core Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Subsets ⭐

### Idea:

At each element → take / not take

```cpp id="bt5"
void solve(int i, vector<int>& nums,
           vector<int>& temp,
           vector<vector<int>>& ans){

    if(i == nums.size()){
        ans.push_back(temp);
        return;
    }

    // include
    temp.push_back(nums[i]);
    solve(i+1, nums, temp, ans);

    // exclude
    temp.pop_back();
    solve(i+1, nums, temp, ans);
}
```

---

### Complexity

```text id="bt6"
O(2^n)
```

---

# Pattern 2: Permutations ⭐⭐⭐

### Idea:

Try every unused element

```cpp id="bt7"
void solve(vector<int>& nums,
           vector<int>& temp,
           vector<int>& vis,
           vector<vector<int>>& ans){

    if(temp.size() == nums.size()){
        ans.push_back(temp);
        return;
    }

    for(int i = 0; i < nums.size(); i++){

        if(!vis[i]){

            vis[i] = 1;
            temp.push_back(nums[i]);

            solve(nums, temp, vis, ans);

            temp.pop_back();
            vis[i] = 0;
        }
    }
}
```

---

### Complexity

```text id="bt8"
O(n!)
```

---

# Pattern 3: Combinations ⭐

### Idea:

Pick elements in increasing order

```cpp id="bt9"
void solve(int start, vector<int>& temp){

    if(condition){
        ans.push_back(temp);
        return;
    }

    for(int i = start; i < n; i++){

        temp.push_back(i);

        solve(i + 1, temp);

        temp.pop_back();
    }
}
```

---

# Pattern 4: N-Queens ⭐⭐⭐⭐

### Idea:

Place queen row by row

```cpp id="bt10"
bool safe(row, col){

    check column
    check diagonal
    check anti-diagonal
}
```

---

### Template

```cpp id="bt11"
void solve(int row){

    if(row == n){
        ans.push_back(board);
        return;
    }

    for(int col = 0; col < n; col++){

        if(isSafe(row, col)){

            placeQueen(row, col);

            solve(row + 1);

            removeQueen(row, col);
        }
    }
}
```

---

# Pattern 5: Sudoku Solver ⭐⭐⭐⭐

### Idea:

Fill empty cells one by one

```cpp id="bt12"
for each empty cell:

    try 1 to 9

    if valid:
        place
        recurse
        undo
```

---

# Pattern 6: Word Search ⭐⭐⭐

### Idea:

DFS + backtracking in grid

```cpp id="bt13"
dfs(i, j, index){

    if(index == word.size())
        return true;

    mark visited

    explore 4 directions

    unmark visited
}
```

---

# Pattern 7: Combination Sum ⭐⭐

```cpp id="bt14"
void solve(int start, int target){

    if(target == 0){
        ans.push_back(temp);
        return;
    }

    for(int i = start; i < n; i++){

        if(nums[i] <= target){

            temp.push_back(nums[i]);

            solve(i, target - nums[i]);

            temp.pop_back();
        }
    }
}
```

---

# 6. Backtracking vs Recursion

| Recursion        | Backtracking        |
| ---------------- | ------------------- |
| Solve subproblem | Explore all choices |
| One path         | Many paths          |
| Return value     | Build solutions     |
| Tree-like DP     | Decision tree       |

---

# 7. Time Complexity Pattern

```text id="bt15"
Subsets        → O(2^n)
Permutations   → O(n!)
Combinations   → O(2^n)
N-Queens       → O(n!)
Sudoku         → exponential
```

---

# 8. Pruning ⭐ (VERY IMPORTANT)

```text id="bt16"
Stop early if:
- invalid state
- constraint violated
- no point exploring further
```

---

# 9. Backtracking Decision Tree

```text id="bt17"
Need all solutions?
→ YES → Backtracking

Choices depend on order?
→ YES → Permutations

Pick subset?
→ YES → Subsets

Grid + path?
→ YES → DFS Backtracking

Fill constraints?
→ YES → Sudoku / N-Queens
```

---

# 10. Problem → Pattern Mapping

| Problem                 | Pattern                 |
| ----------------------- | ----------------------- |
| Subsets                 | Backtracking            |
| Permutations            | Backtracking            |
| Combinations            | Backtracking            |
| N-Queens                | Backtracking            |
| Sudoku                  | Constraint Backtracking |
| Word Search             | Grid DFS                |
| Combination Sum         | Backtracking            |
| Palindrome Partitioning | Backtracking            |

---

# 11. Core Mental Model ⭐⭐⭐

```text id="bt18"
Backtracking =

Try → Explore → Undo → Try Next
```

---

# 12. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="bt19"
If a problem says:

"Find ALL ways / ALL combinations / ALL arrangements"

→ It is ALWAYS Backtracking
```

---
