# 🧠 Hashing Master Sheet (Interview Revision Guide)

Hashing is the **most underrated + most powerful optimization tool** in interviews.

It turns:

* O(n²) → O(n)
* Search → O(1)
* Counting → instant lookup

---

# 0. When to Use Hashing?

```text id="h0"
Ask:

✔ Need fast lookup?
✔ Need frequency/count?
✔ Need to detect duplicates?
✔ Need subarray/substring patterns?
✔ Need "seen before" tracking?
```

If YES → Use Hashing.

---

# 1. Core Idea ⭐

```text id="h1"
Store information while iterating
so you never recompute again.
```

---

# 2. Basic Hash Structures

---

## A) Hash Set (presence check)

```cpp id="h2"
unordered_set<int> st;
```

Used for:

* duplicates
* visited tracking
* existence check

---

## B) Hash Map (frequency / mapping)

```cpp id="h3"
unordered_map<int,int> mp;
```

Used for:

* frequency count
* prefix sum mapping
* index storage

---

# 3. Core Patterns in Hashing

---

# Pattern 1: Frequency Counting ⭐

```cpp id="h4"
unordered_map<int,int> freq;

for(int x : nums){
    freq[x]++;
}
```

### Used in:

* majority element
* anagrams
* duplicates
* top-k elements

---

# Pattern 2: Existence Check (O(1)) ⭐

```cpp id="h5"
unordered_set<int> st;

for(int x : nums){

    if(st.count(x))
        return true;

    st.insert(x);
}
```

### Used in:

* cycle detection
* duplicate detection
* pair problems

---

# Pattern 3: Subarray Sum / Prefix + Hashing ⭐⭐⭐

MOST IMPORTANT PATTERN.

```cpp id="h6"
unordered_map<int,int> mp;
mp[0] = 1;

int sum = 0, ans = 0;

for(int x : nums){

    sum += x;

    if(mp.count(sum - k)){
        ans += mp[sum - k];
    }

    mp[sum]++;
}
```

---

## Key Idea

```text id="h7"
If prefix[j] - prefix[i] = k
→ store prefix[i]
```

---

# Pattern 4: Sliding Window + Hashing ⭐⭐⭐

Used when:

* substring problems
* distinct elements
* frequency constraints

---

## Template

```cpp id="h8"
unordered_map<char,int> mp;

int left = 0;

for(int right = 0; right < n; right++){

    mp[s[right]]++;

    while(invalid){

        mp[s[left]]--;

        if(mp[s[left]] == 0)
            mp.erase(s[left]);

        left++;
    }
}
```

---

## Problems:

* Longest substring without repeating
* At most K distinct
* Minimum window substring
* Fruits into baskets

---

# Pattern 5: Two Sum / Pair Finding ⭐

```cpp id="h9"
unordered_map<int,int> mp;

for(int i = 0; i < n; i++){

    if(mp.count(target - nums[i]))
        return true;

    mp[nums[i]] = i;
}
```

---

# Pattern 6: Grouping (Anagrams) ⭐

```cpp id="h10"
unordered_map<string, vector<string>> mp;

for(string s : strs){

    string key = s;
    sort(key.begin(), key.end());

    mp[key].push_back(s);
}
```

---

# Pattern 7: First Unique / Order Tracking ⭐

```cpp id="h11"
unordered_map<int,int> freq;
```

Used for:

* first non-repeating character
* stream problems

---

# Pattern 8: Index Mapping ⭐

```cpp id="h12"
unordered_map<int,int> index;
```

Used for:

* restore arrays
* quick position lookup

---

# 4. Hashing + Prefix Sum Combo ⭐⭐⭐⭐

Most powerful interview pattern.

```text id="h13"
Prefix sum + hashmap = subarray problems
```

Examples:

* Subarray sum = K
* Count subarrays
* Continuous subarray sum

---

# 5. Hashing + Sliding Window Combo ⭐⭐⭐⭐

```text id="h14"
Window + frequency map = substring problems
```

Examples:

* Longest substring without repeating
* At most K distinct
* Minimum window substring

---

# 6. Hashing Variants

---

## A) Hashing for XOR

```cpp id="h15"
unordered_map<int,int> mp;
```

Used in:

* XOR subarrays
* missing number
* odd occurrence

---

## B) 2-Sum Variants

```text id="h16"
Store seen values while iterating
```

---

## C) Hashing for Counting Pairs

```cpp id="h17"
ans += freq[value];
```

---

# 7. Classic Problems

---

## 1. Two Sum ⭐

```cpp id="h18"
unordered_map<int,int> mp;

for(int i = 0; i < n; i++){

    if(mp.count(target - nums[i]))
        return {mp[target - nums[i]], i};

    mp[nums[i]] = i;
}
```

---

## 2. Subarray Sum = K ⭐⭐⭐

(Already shown above)

---

## 3. Longest Substring Without Repeat ⭐⭐⭐

```cpp id="h19"
unordered_set<char> st;

int left = 0;

for(int right = 0; right < n; right++){

    while(st.count(s[right])){
        st.erase(s[left]);
        left++;
    }

    st.insert(s[right]);
}
```

---

## 4. Group Anagrams ⭐

(Already shown above)

---

## 5. Majority Element

```cpp id="h20"
unordered_map<int,int> freq;

for(int x : nums){

    if(++freq[x] > n/2)
        return x;
}
```

---

# 8. Complexity

```text id="h21"
Insert  → O(1)
Search  → O(1)
Delete  → O(1)
Average → O(1)
Worst   → O(n) (rare)
```

---

# 9. Hashing Decision Rules

```text id="h22"
Need fast lookup?
→ unordered_set / map

Need frequency?
→ unordered_map

Need subarray sum?
→ prefix + map

Need substring constraint?
→ sliding window + map

Need pair?
→ map (value → index)
```

---

# 10. Final Mental Model ⭐⭐⭐

```text id="h23"
Hashing = "memory of what you have seen"
```

Instead of recalculating:

✔ store result
✔ reuse instantly

---

# 11. Problem → Pattern Mapping

| Problem            | Pattern               |
| ------------------ | --------------------- |
| Two Sum            | Hash Map              |
| Subarray Sum = K   | Prefix + Hash         |
| Longest Substring  | Sliding Window + Hash |
| Group Anagrams     | Hash Map              |
| Majority Element   | Frequency Hash        |
| Duplicate Check    | Hash Set              |
| At Most K Distinct | Sliding Window + Hash |

---

# 12. Final Insight ⭐⭐⭐

```text id="h24"
If brute force compares everything,

Hashing remembers everything.
```

---
