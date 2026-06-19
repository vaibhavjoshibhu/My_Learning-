# Prefix Sum Master Sheet (Interview Revision Guide)

Prefix Sum is one of the most powerful patterns to convert:
👉 **O(n²) → O(n)**
👉 Range queries → O(1) after preprocessing

---

# 0. When to Use Prefix Sum?

```text id="ps0"
Ask:

✔ Need sum of subarray?
✔ Repeated range queries?
✔ Subarray count problems?
✔ “Equal to K / difference / XOR” type problems?
✔ Cannot afford nested loops?
```

If YES → Prefix Sum.

---

# 1. Core Idea ⭐

Instead of recomputing sums repeatedly:

```text id="ps1"
prefix[i] = sum of elements from 0 → i
```

Then:

```text id="ps2"
sum(l → r) = prefix[r] - prefix[l-1]
```

---

# 2. Basic Prefix Sum Template

```cpp id="ps3"
vector<int> prefix(n);

prefix[0] = nums[0];

for(int i = 1; i < n; i++){
    prefix[i] = prefix[i-1] + nums[i];
}
```

---

## Range Query

```cpp id="ps4"
int rangeSum(int l, int r){
    if(l == 0) return prefix[r];
    return prefix[r] - prefix[l-1];
}
```

---

# 3. Space Optimized Prefix Sum ⭐

```cpp id="ps5"
int sum = 0;

for(int i = 0; i < n; i++){
    sum += nums[i];
}
```

Used when only running sum needed.

---

# 4. Most Important Pattern: Subarray Sum = K ⭐⭐⭐

---

## Brute Force → O(n²)

Prefix Sum → O(n)

---

## HashMap + Prefix Sum Template

```cpp id="ps6"
unordered_map<int,int> mp;

mp[0] = 1;

int sum = 0, ans = 0;

for(int i = 0; i < n; i++){

    sum += nums[i];

    if(mp.count(sum - k)){
        ans += mp[sum - k];
    }

    mp[sum]++;
}
```

---

## Key Insight

```text id="ps7"
If:

prefix[j] - prefix[i] = k

Then:

prefix[i] = prefix[j] - k
```

---

# 5. Prefix Sum Patterns

---

# Pattern 1: Range Sum Queries

```text id="ps8"
precompute → answer queries in O(1)
```

---

# Pattern 2: Subarray Count

```text id="ps9"
Use hashmap of prefix frequencies
```

---

# Pattern 3: Balanced / Equal Partition

```text id="ps10"
Find equal prefix split points
```

Examples:

* Split array into equal sum
* Equilibrium index

---

# Pattern 4: XOR Prefix ⭐

```cpp id="ps11"
prefix[i] = prefix[i-1] ^ nums[i];
```

Used in:

* XOR subarray problems
* Missing number
* Odd occurrence

---

## Range XOR

```cpp id="ps12"
xor(l, r) = prefix[r] ^ prefix[l-1]
```

---

# Pattern 5: 2D Prefix Sum ⭐⭐⭐

---

## Build Matrix Prefix

```cpp id="ps13"
for(int i = 1; i < n; i++){
    for(int j = 1; j < m; j++){

        prefix[i][j] =
            grid[i][j]
          + prefix[i-1][j]
          + prefix[i][j-1]
          - prefix[i-1][j-1];
    }
}
```

---

## Query Submatrix Sum

```cpp id="ps14"
sum =
prefix[r2][c2]
- prefix[r1-1][c2]
- prefix[r2][c1-1]
+ prefix[r1-1][c1-1];
```

---

# 6. Prefix Sum Variants (VERY IMPORTANT)

---

## A) Difference Array (Range Updates)

```cpp id="ps15"
diff[l] += val;
diff[r+1] -= val;
```

Then prefix it.

Used in:

* Range increment updates
* Bookings
* Queries

---

## B) Prefix Product (rare)

```cpp id="ps16"
product[i] = product[i-1] * nums[i];
```

Used carefully (overflow issues).

---

## C) Prefix Count (frequency prefix)

```cpp id="ps17"
count[i] = count[i-1] + (nums[i] == x);
```

---

# 7. Classic Problems

---

## 1. Subarray Sum = K ⭐

```cpp id="ps18"
unordered_map<int,int> mp;
mp[0] = 1;

int sum = 0, ans = 0;

for(int x : nums){

    sum += x;

    if(mp.count(sum - k))
        ans += mp[sum - k];

    mp[sum]++;
}
```

---

## 2. Equilibrium Index

```cpp id="ps19"
if(prefix[i-1] == total - prefix[i])
```

---

## 3. Range Sum Query

```cpp id="ps20"
prefix[r] - prefix[l-1]
```

---

## 4. Continuous Subarray Sum (mod k)

```cpp id="ps21"
sum %= k;

if(mp.count(sum))
    return true;
```

---

## 5. Maximum Subarray (Kadane = Prefix idea)

```cpp id="ps22"
currentSum = max(nums[i], currentSum + nums[i]);
```

---

# 8. Prefix Sum Decision Rules

```text id="ps23"
Need sum of range?
→ Prefix array

Need subarray count?
→ Prefix + HashMap

Need XOR range?
→ XOR prefix

Need 2D query?
→ 2D prefix

Need range updates?
→ Difference array
```

---

# 9. Complexity

```text id="ps24"
Precompute: O(n)
Query: O(1)
Space: O(n)
```

For hashmap version:

```text id="ps25"
Time: O(n)
Space: O(n)
```

---

# 10. Prefix Sum Mental Model ⭐⭐⭐

```text id="ps26"
Instead of recomputing sums again and again,
store "history of sums"
```

---

# 11. Problem → Pattern Mapping

| Problem                 | Pattern              |
| ----------------------- | -------------------- |
| Subarray Sum = K        | Prefix + HashMap     |
| Range Sum Query         | Prefix Array         |
| Equilibrium Index       | Prefix               |
| Subarray XOR            | XOR Prefix           |
| Continuous Subarray Sum | Mod Prefix           |
| 2D Range Sum            | 2D Prefix            |
| Range Updates           | Difference Array     |
| Maximum Subarray        | Kadane (prefix idea) |

---

# 12. Final Cheat Insight ⭐

```text id="ps27"
Prefix Sum is NOT just an array.

It is a way to convert:

"recompute again and again"
→
"store history and reuse"
```

---
