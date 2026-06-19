# Two Pointers: Complete Interview Revision Sheet

This sheet is designed to be your **single revision page** before interviews.

---

# 1. How to Identify a Two Pointer Problem

Ask yourself:

```text
1. Is the array/string sorted?
   → Opposite-end pointers

2. Need pair/triplet/quadruplet?
   → Two pointers after sorting

3. Need longest/shortest valid subarray?
   → Sliding Window

4. Need remove duplicates / move elements?
   → Slow-Fast pointers

5. Need partition around pivot?
   → Dutch Flag / Partition pointers

6. Need palindrome?
   → Left-Right pointers

7. Need cycle detection?
   → Fast-Slow pointers
```

---

# MASTER TEMPLATE 1: Opposite-End Pointers

## Template

```cpp
int left = 0;
int right = n - 1;

while(left < right){

    if(condition){
        left++;
    }
    else{
        right--;
    }
}
```

---

## Recognition

```text
✓ Sorted Array
✓ Pair Sum
✓ Palindrome
✓ Container Water
✓ Rain Water
✓ 3Sum
✓ 4Sum
```

---

## Problem: Two Sum II

```cpp
int left = 0;
int right = n-1;

while(left < right){

    int sum = nums[left] + nums[right];

    if(sum == target)
        return {left,right};

    else if(sum < target)
        left++;

    else
        right--;
}
```

### Logic

```text
sum too small → move left
sum too large → move right
```

Complexity:

```text
O(n)
```

---

## Problem: Valid Palindrome

```cpp
int left = 0;
int right = s.size()-1;

while(left < right){

    if(s[left] != s[right])
        return false;

    left++;
    right--;
}

return true;
```

---

## Problem: Container With Most Water

```cpp
while(left < right){

    ans = max(ans,
             min(h[left],h[right]) *
             (right-left));

    if(h[left] < h[right])
        left++;
    else
        right--;
}
```

### Key Observation

```text
Always move smaller height.
```

---

## Problem: Trapping Rain Water

```cpp
int left = 0;
int right = n-1;

int leftMax = 0;
int rightMax = 0;

while(left < right){

    if(height[left] < height[right]){

        leftMax = max(leftMax,height[left]);

        water += leftMax - height[left];

        left++;
    }
    else{

        rightMax = max(rightMax,height[right]);

        water += rightMax - height[right];

        right--;
    }
}
```

---

# MASTER TEMPLATE 2: Slow-Fast Pointers

Used when modifying arrays in-place.

## Template

```cpp
int slow = 0;

for(int fast = 0; fast < n; fast++){

    if(valid){
        nums[slow++] = nums[fast];
    }
}
```

---

## Recognition

```text
✓ Remove Duplicates
✓ Move Zeroes
✓ Remove Element
✓ Stable Partition
```

---

## Problem: Remove Duplicates

```cpp
int slow = 1;

for(int fast=1; fast<n; fast++){

    if(nums[fast] != nums[fast-1]){
        nums[slow++] = nums[fast];
    }
}
```

---

## Problem: Move Zeroes

```cpp
int slow = 0;

for(int fast=0; fast<n; fast++){

    if(nums[fast] != 0){
        swap(nums[slow++], nums[fast]);
    }
}
```

---

## Problem: Remove Element

```cpp
int slow = 0;

for(int fast=0; fast<n; fast++){

    if(nums[fast] != val){
        nums[slow++] = nums[fast];
    }
}
```

---

# MASTER TEMPLATE 3: Sliding Window

Most important pattern for modern interviews.

---

## Fixed Window

### Example: Maximum Sum Subarray of Size K

```cpp
int sum = 0;

for(int i=0;i<k;i++)
    sum += nums[i];

int ans = sum;

for(int i=k;i<n;i++){

    sum += nums[i];
    sum -= nums[i-k];

    ans = max(ans,sum);
}
```

Complexity:

```text
O(n)
```

---

## Variable Window

### Template

```cpp
int left = 0;

for(int right=0; right<n; right++){

    add(nums[right]);

    while(window_invalid){

        remove(nums[left]);
        left++;
    }

    update_answer();
}
```

---

## Recognition

```text
✓ Longest Substring
✓ Minimum Window
✓ At Most K Distinct
✓ Fruits Into Basket
✓ Binary Subarrays
✓ Product Less Than K
```

---

## Problem: Longest Substring Without Repeating

```cpp
unordered_set<char> st;

int left = 0;

for(int right=0; right<n; right++){

    while(st.count(s[right])){

        st.erase(s[left]);
        left++;
    }

    st.insert(s[right]);

    ans = max(ans,right-left+1);
}
```

---

## Problem: Minimum Window Substring

### Template

```cpp
for(right){

    include(right);

    while(valid){

        update_answer();

        exclude(left);
        left++;
    }
}
```

### Core Idea

```text
Expand → satisfy condition
Shrink → minimize answer
```

---

## Problem: Fruits Into Basket

```cpp
unordered_map<int,int> mp;

for(right){

    mp[fruits[right]]++;

    while(mp.size() > 2){

        mp[fruits[left]]--;

        if(mp[fruits[left]] == 0)
            mp.erase(fruits[left]);

        left++;
    }

    ans=max(ans,right-left+1);
}
```

---

## Problem: Subarray Product Less Than K

```cpp
int left = 0;
long long prod = 1;

for(int right=0; right<n; right++){

    prod *= nums[right];

    while(prod >= k){

        prod /= nums[left];
        left++;
    }

    ans += right-left+1;
}
```

---

# MASTER TEMPLATE 4: Sort + Two Pointers

Used in 3Sum and 4Sum.

---

# Problem: 3Sum

### Template

```cpp
sort(nums.begin(),nums.end());

for(int i=0;i<n;i++){

    int left = i+1;
    int right = n-1;

    while(left < right){

        int sum =
            nums[i]
          + nums[left]
          + nums[right];

        if(sum == 0){
            // found answer
        }
        else if(sum < 0){
            left++;
        }
        else{
            right--;
        }
    }
}
```

Complexity:

```text
O(n²)
```

---

# Problem: 4Sum

### Pattern

```text
Sort
Fix First Number
Fix Second Number
Apply Two Pointers
```

Complexity:

```text
O(n³)
```

---

# MASTER TEMPLATE 5: Dutch National Flag

---

## Problem: Sort Colors

```cpp
int low = 0;
int mid = 0;
int high = n-1;

while(mid <= high){

    if(nums[mid] == 0){

        swap(nums[low],nums[mid]);

        low++;
        mid++;
    }

    else if(nums[mid] == 1){

        mid++;
    }

    else{

        swap(nums[mid],nums[high]);

        high--;
    }
}
```

### Meaning

```text
0 → left
1 → middle
2 → right
```

Complexity:

```text
O(n)
```

---

# MASTER TEMPLATE 6: Partition Pointer

Used in Quick Sort.

```cpp
int i = 0;

for(int j=0;j<n;j++){

    if(nums[j] < pivot){

        swap(nums[i],nums[j]);

        i++;
    }
}
```

---

# MASTER TEMPLATE 7: Fast-Slow Cycle Detection

Used beyond linked lists.

---

## Linked List Cycle

```cpp
while(fast && fast->next){

    slow = slow->next;
    fast = fast->next->next;

    if(slow == fast)
        return true;
}
```

---

## Happy Number

```cpp
slow = n;
fast = n;

do{

    slow = nextNumber(slow);

    fast = nextNumber(
           nextNumber(fast));

}while(slow != fast);
```

---

# Problem → Pattern Mapping

| Problem             | Pattern             |
| ------------------- | ------------------- |
| Two Sum II          | Opposite Ends       |
| Valid Palindrome    | Opposite Ends       |
| Container Water     | Opposite Ends       |
| Rain Water          | Opposite Ends       |
| Remove Duplicates   | Slow/Fast           |
| Move Zeroes         | Slow/Fast           |
| Remove Element      | Slow/Fast           |
| Sort Colors         | Dutch Flag          |
| Partition Array     | Partition           |
| Longest Substring   | Sliding Window      |
| Minimum Window      | Sliding Window      |
| Fruits Into Basket  | Sliding Window      |
| Product Less Than K | Sliding Window      |
| Binary Subarrays    | Sliding Window      |
| 3Sum                | Sort + Two Pointers |
| 4Sum                | Sort + Two Pointers |
| Happy Number        | Fast/Slow           |
| Linked List Cycle   | Fast/Slow           |

---

# Ultimate Interview Decision Tree

```text
ARRAY / STRING

├── Sorted?
│   └── Opposite-End Pointers

├── Pair / Triplet?
│   └── Sort + Two Pointers

├── Longest / Shortest Window?
│   └── Sliding Window

├── Remove / Compact Elements?
│   └── Slow-Fast

├── 0,1,2 Sorting?
│   └── Dutch Flag

├── Partition Around Pivot?
│   └── Partition Pointer

└── Cycle?
    └── Fast-Slow
```

# Top 5 Templates to Memorize

```cpp
// 1. Opposite Ends
while(left < right)

// 2. Slow-Fast
for(fast=0; fast<n; fast++)

// 3. Sliding Window
for(right=0; right<n; right++)

// 4. Sort + Two Pointers
sort(nums.begin(),nums.end());

// 5. Dutch Flag
low, mid, high
```

If you master these 5 templates, you'll be able to solve the vast majority of two-pointer questions asked in coding interviews, LeetCode, and competitive programming.
