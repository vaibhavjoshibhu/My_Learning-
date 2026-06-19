# 🧠 Sliding Window Master Sheet (Interview Revision)

Sliding Window is used for **subarray / substring problems where you want to optimize brute force O(n²) → O(n)**.

---

# 0. When to Use Sliding Window?

```text id="sw0"
Ask yourself:

✔ Subarray / substring?
✔ Contiguous elements?
✔ Need max/min/longest/shortest?
✔ Constraints involve “at most / at least / exactly”
```

If YES → Sliding Window.

---

# 1. Two Types of Sliding Window

---

# A) Fixed Size Window ⭐

Used when window size is given (k).

---

## Template

```cpp id="sw1"
int sum = 0;

// first window
for(int i = 0; i < k; i++)
    sum += nums[i];

int ans = sum;

// slide window
for(int i = k; i < n; i++){

    sum += nums[i];       // add new
    sum -= nums[i-k];     // remove old

    ans = max(ans, sum);
}
```

---

## Problems

* Maximum sum subarray of size K
* Average of subarrays
* First negative in window
* Sliding window maximum (with deque)

---

## Complexity

```text id="sw2"
Time  : O(n)
Space : O(1)
```

---

# B) Variable Size Window ⭐⭐⭐

Used when window size is NOT fixed.

---

## Master Template

```cpp id="sw3"
int left = 0;

for(int right = 0; right < n; right++){

    add(nums[right]);

    while(window_invalid){

        remove(nums[left]);
        left++;
    }

    update_answer();
}
```

---

## Key Idea

```text id="sw4"
Expand right pointer → include element
Shrink left pointer → fix constraint
```

---

# 2. Core Sliding Window Patterns

---

# Pattern 1: Longest Subarray / Substring

```cpp id="sw5"
ans = max(ans, right - left + 1);
```

### Example Problems:

* Longest substring without repeating
* Longest subarray with K distinct
* Longest ones after replacement

---

# Pattern 2: Minimum Window

```cpp id="sw6"
while(valid){

    ans = min(ans, window_size);

    shrink left
}
```

### Example:

* Minimum window substring

---

# Pattern 3: Count Subarrays

```cpp id="sw7"
ans += (right - left + 1);
```

### Example:

* Subarrays with product < k
* Binary subarray sum

---

# Pattern 4: Frequency Map Window

```cpp id="sw8"
unordered_map<int,int> mp;
```

Used when:

* duplicates matter
* distinct elements constraint

---

# 3. Classic Sliding Window Problems

---

## 1. Longest Substring Without Repeating Characters

```cpp id="sw9"
unordered_set<char> st;
int left = 0;

for(int right = 0; right < n; right++){

    while(st.count(s[right])){
        st.erase(s[left]);
        left++;
    }

    st.insert(s[right]);

    ans = max(ans, right - left + 1);
}
```

---

## 2. Fruits Into Basket

```cpp id="sw10"
unordered_map<int,int> mp;

for(int right = 0; right < n; right++){

    mp[fruits[right]]++;

    while(mp.size() > 2){

        mp[fruits[left]]--;

        if(mp[fruits[left]] == 0)
            mp.erase(fruits[left]);

        left++;
    }

    ans = max(ans, right - left + 1);
}
```

---

## 3. Subarray Product < K

```cpp id="sw11"
long long prod = 1;
int left = 0;

for(int right = 0; right < n; right++){

    prod *= nums[right];

    while(prod >= k){

        prod /= nums[left];
        left++;
    }

    ans += (right - left + 1);
}
```

---

## 4. Binary Subarray Sum

```cpp id="sw12"
unordered_map<int,int> freq;
freq[0] = 1;

int sum = 0;

for(int right = 0; right < n; right++){

    sum += nums[right];

    if(freq.count(sum - goal))
        ans += freq[sum - goal];

    freq[sum]++;
}
```

---

# 4. Sliding Window Decision Rules

---

## Rule 1: Expanding Window

```text id="sw13"
Always do:
right++
```

---

## Rule 2: Shrinking Window

```text id="sw14"
while(invalid condition)
    left++
```

---

## Rule 3: Update Answer

Depends on problem:

```text id="sw15"
max window → longest
min window → smallest
count → add contribution
```

---

# 5. Fixed vs Variable Window Comparison

| Type     | When            | Example            |
| -------- | --------------- | ------------------ |
| Fixed    | size k given    | max sum k-subarray |
| Variable | condition based | longest substring  |

---

# 6. Complexity

```text id="sw16"
Time  : O(n)
Space : O(1) or O(k)
```

Why?

```text id="sw17"
Each element enters once and exits once
```

---

# 7. Sliding Window + Hashing Combo ⭐

Most important interview combo.

```text id="sw18"
Window + frequency map
```

Used in:

* Longest substring
* At most K distinct
* Anagrams
* Minimum window substring

---

# 8. Advanced Sliding Window Patterns

---

## A) At Most K Pattern

```cpp id="sw19"
while(mp.size() > k)
    shrink
```

---

## B) Exactly K Pattern

```text id="sw20"
exactly K = atMost(K) - atMost(K-1)
```

---

## C) Monotonic Deque Window ⭐

Used for:

```text id="sw21"
Sliding window maximum/minimum
```

---

# 9. Sliding Window Cheat Sheet

---

## Always Ask:

```text id="sw22"
1. Subarray or substring?
2. Need max/min/longest/count?
3. Contiguous constraint?
```

---

## Then Choose:

```text id="sw23"
Fixed size → k window

Variable size → expand/shrink

Frequency needed → hashmap

Max/min window → deque

Count subarrays → prefix + window
```

---

# 10. Final Mental Model ⭐⭐⭐

```text id="sw24"
Sliding Window =

"Keep expanding until invalid,
then shrink until valid again"
```

---
