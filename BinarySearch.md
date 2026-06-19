# 🧠 Binary Search Master Sheet (Interview Revision Guide)

Binary Search is not just “search in sorted array” — it is a **decision-making + search-space reduction technique**.

It is one of the most important patterns in interviews.

---

# 0. When to Use Binary Search?

```text id="bs0"
Ask:

✔ Sorted array?
✔ Need O(log n) optimization?
✔ Can answer be “YES/NO” for a condition?
✔ Searching for minimum/maximum valid answer?
✔ Monotonic condition exists?
```

If YES → Binary Search applies.

---

# 1. Core Idea ⭐

```text id="bs1"
Eliminate half search space each step
based on a decision condition
```

---

# 2. Basic Binary Search Template

## A) Classic Search

```cpp id="bs2"
int l = 0, r = n - 1;

while(l <= r){

    int mid = l + (r - l) / 2;

    if(nums[mid] == target)
        return mid;

    else if(nums[mid] < target)
        l = mid + 1;

    else
        r = mid - 1;
}
```

---

## Complexity

```text id="bs3"
Time  : O(log n)
Space : O(1)
```

---

# 3. Binary Search Variants ⭐⭐⭐

---

# Pattern 1: First/Last Occurrence

---

## First Occurrence

```cpp id="bs4"
int ans = -1;
int l = 0, r = n - 1;

while(l <= r){

    int mid = l + (r - l) / 2;

    if(nums[mid] == target){
        ans = mid;
        r = mid - 1;
    }
    else if(nums[mid] < target)
        l = mid + 1;
    else
        r = mid - 1;
}
```

---

## Last Occurrence

```cpp id="bs5"
if(nums[mid] == target){
    ans = mid;
    l = mid + 1;
}
```

---

# Pattern 2: Lower Bound / Upper Bound ⭐

---

## Lower Bound (first ≥ target)

```cpp id="bs6"
while(l < r){

    int mid = (l + r) / 2;

    if(nums[mid] >= target)
        r = mid;
    else
        l = mid + 1;
}
```

---

## Upper Bound (first > target)

```cpp id="bs7"
while(l < r){

    int mid = (l + r) / 2;

    if(nums[mid] > target)
        r = mid;
    else
        l = mid + 1;
}
```

---

# Pattern 3: Binary Search on Answer ⭐⭐⭐⭐⭐

MOST IMPORTANT INTERVIEW PATTERN.

---

## Idea

```text id="bs8"
We are NOT searching array.

We are searching "answer space"
```

---

## Template

```cpp id="bs9"
int l = 0, r = MAX_ANSWER;
int ans = -1;

while(l <= r){

    int mid = l + (r - l) / 2;

    if(isValid(mid)){
        ans = mid;
        r = mid - 1;
    }
    else{
        l = mid + 1;
    }
}
```

---

## Key Function

```cpp id="bs10"
bool isValid(int mid){
    return condition;
}
```

---

## Examples:

* Minimum capacity to ship packages
* Aggressive cows
* Koko eating bananas
* Minimum max distance
* Split array largest sum

---

# Pattern 4: Search in Rotated Sorted Array ⭐

```cpp id="bs11"
if(nums[l] <= nums[mid]){

    if(target >= nums[l] && target < nums[mid])
        r = mid - 1;
    else
        l = mid + 1;
}
else{

    if(target > nums[mid] && target <= nums[r])
        l = mid + 1;
    else
        r = mid - 1;
}
```

---

# Pattern 5: Peak Element (Mountain Array)

```cpp id="bs12"
while(l < r){

    int mid = (l + r) / 2;

    if(nums[mid] < nums[mid + 1])
        l = mid + 1;
    else
        r = mid;
}
```

---

# Pattern 6: Square Root / Mathematical BS ⭐

```cpp id="bs13"
while(l <= r){

    int mid = l + (r - l) / 2;

    if(mid * mid <= x){
        ans = mid;
        l = mid + 1;
    }
    else{
        r = mid - 1;
    }
}
```

---

# Pattern 7: Binary Search on Monotonic Function

```text id="bs14"
If condition changes from:

FALSE FALSE FALSE TRUE TRUE TRUE
→ binary search works
```

---

# 4. Binary Search Decision Rules

---

```text id="bs15"
If array sorted → normal BS

If searching answer → BS on answer

If condition monotonic → BS possible

If peaks/valleys → modified BS
```

---

# 5. Complexity

```text id="bs16"
Time  : O(log n)
Space : O(1)
```

---

# 6. Common Problem Patterns

---

## 1. Search in array

```text id="bs17"
Classic binary search
```

---

## 2. First/Last position

```text id="bs18"
Boundary binary search
```

---

## 3. Minimum / Maximum feasible answer

```text id="bs19"
Binary search on answer space
```

---

## 4. Rotated array

```text id="bs20"
Two sorted halves logic
```

---

## 5. Peak finding

```text id="bs21"
Compare mid with neighbors
```

---

# 7. Problem → Pattern Mapping

| Problem                 | Pattern      |
| ----------------------- | ------------ |
| Binary Search           | Classic      |
| First/Last Occurrence   | Boundary BS  |
| Search in Rotated Array | Split logic  |
| Koko Eating Bananas     | BS on Answer |
| Aggressive Cows         | BS on Answer |
| Split Array Largest Sum | BS on Answer |
| Peak Element            | Modified BS  |
| Square Root             | Math BS      |

---

# 8. Binary Search Mental Model ⭐⭐⭐

```text id="bs22"
Binary Search =

"Repeatedly eliminate half of possibilities
based on a YES/NO condition"
```

---

# 9. MOST IMPORTANT INSIGHT ⭐⭐⭐⭐⭐

```text id="bs23"
If you can define a function:

f(x) = valid / invalid

and it is monotonic →

👉 Binary Search on Answer is possible
```

---

# 10. Final Cheat Sheet

```text id="bs24"
3 core forms:

1. Search in array
2. Boundary search
3. Search on answer space
```

---

# If you want next:

I can create:

* 🔥 Greedy Master Sheet
* 🔥 DP Master Sheet (most important)
* 🔥 Stack / Monotonic Stack Sheet
* 🔥 Complete “Pattern Recognition Cheat Sheet (ALL topics combined)”

Just tell 👍
