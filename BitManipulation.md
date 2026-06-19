# 🧠 Bit Manipulation Master Sheet (Interview Revision Guide)

Bit manipulation is about using **binary representation of numbers** to solve problems faster than normal arithmetic.

It is heavily used in:

* optimization
* subset problems
* XOR tricks
* hashing alternatives
* DP states (bitmask DP)

---

# 0. When to Use Bit Manipulation?

```text id="bm0"
Ask:

✔ Need to optimize space/time using binary?
✔ Subset / combinations problems?
✔ XOR patterns?
✔ “Odd one out / single number” type problems?
✔ Power of 2 / even-odd logic?
```

If YES → Bit Manipulation.

---

# 1. Core Idea ⭐

```text id="bm1"
Everything is stored in binary → manipulate bits directly
```

---

# 2. Basic Bit Operations ⭐⭐⭐

---

## AND (&)

```text id="bm2"
1 & 1 = 1
else = 0
```

Used for:

* checking bit
* masking

---

## OR (|)

```text id="bm3"
1 | 0 = 1
```

Used for:

* setting bits

---

## XOR (^)

```text id="bm4"
1 ^ 1 = 0
1 ^ 0 = 1
```

MOST IMPORTANT OPERATOR ⭐⭐⭐⭐⭐

---

## NOT (~)

```text id="bm5"
flips bits
```

---

# 3. Core Bit Tricks ⭐⭐⭐⭐⭐

---

## 1. Check if i-th bit is set

```cpp id="bm6"
if(n & (1 << i))
    cout << "bit is set";
```

---

## 2. Set i-th bit

```cpp id="bm7"
n = n | (1 << i);
```

---

## 3. Clear i-th bit

```cpp id="bm8"
n = n & ~(1 << i);
```

---

## 4. Toggle i-th bit

```cpp id="bm9"
n = n ^ (1 << i);
```

---

# 4. XOR Patterns ⭐⭐⭐⭐⭐

---

## A) Single Number (most important)

```cpp id="bm10"
int x = 0;

for(int num : nums)
    x ^= num;
```

---

## Why it works:

```text id="bm11"
a ^ a = 0
a ^ 0 = a
```

---

## B) Two unique numbers

```cpp id="bm12"
xor_all → split using rightmost set bit
```

---

## C) Missing number

```cpp id="bm13"
1 ^ 2 ^ 3 ^ ... ^ n
```

---

## D) Odd occurrences

```text id="bm14"
XOR cancels even occurrences
```

---

# 5. Count Bits ⭐⭐⭐

---

## Count set bits

```cpp id="bm15"
int count = 0;

while(n){
    count += (n & 1);
    n >>= 1;
}
```

---

## Brian Kernighan’s Algorithm ⭐

```cpp id="bm16"
while(n){
    n = n & (n - 1);
    count++;
}
```

---

# 6. Power of 2 Check ⭐

```cpp id="bm17"
if(n > 0 && (n & (n - 1)) == 0)
    cout << "Power of 2";
```

---

# 7. Subsets using Bits ⭐⭐⭐⭐⭐

---

## Idea:

```text id="bm18"
Each number represents inclusion/exclusion
```

---

## Template

```cpp id="bm19"
for(int mask = 0; mask < (1 << n); mask++){

    vector<int> subset;

    for(int i = 0; i < n; i++){

        if(mask & (1 << i)){
            subset.push_back(nums[i]);
        }
    }
}
```

---

# 8. Bitmask DP ⭐⭐⭐⭐⭐

```text id="bm20"
dp[mask] = answer for subset represented by mask
```

Used in:

* TSP
* assignment problems

---

# 9. Left & Right Shift ⭐⭐⭐

---

## Left shift

```text id="bm21"
n << 1 → multiply by 2
```

## Right shift

```text id="bm22"
n >> 1 → divide by 2
```

---

# 10. Important Bit Patterns

---

## Even / Odd

```cpp id="bm23"
if(n & 1) odd
else even
```

---

## Swap without temp

```cpp id="bm24"
a = a ^ b;
b = a ^ b;
a = a ^ b;
```

---

# 11. Bit Manipulation Patterns

---

## Pattern 1: XOR Cancellation ⭐

Used in:

* single number
* missing number

---

## Pattern 2: Bitmask Enumeration ⭐

Used in:

* subsets
* combinations

---

## Pattern 3: Bit DP ⭐

Used in:

* TSP
* subset optimization

---

## Pattern 4: Bit Checking ⭐

Used in:

* constraints filtering

---

# 12. Complexity

```text id="bm25"
Bit operations → O(1)
Subset generation → O(2^n)
Bit DP → O(n * 2^n)
```

---

# 13. Problem → Pattern Mapping

| Problem            | Pattern   |
| ------------------ | --------- |
| Single Number      | XOR       |
| Missing Number     | XOR       |
| Power of 2         | Bit check |
| Count bits         | Kernighan |
| Subsets            | Bitmask   |
| TSP                | Bit DP    |
| Two unique numbers | XOR split |
| Even/Odd           | AND       |

---

# 14. Decision Rules ⭐⭐⭐

```text id="bm26"
Need fast tricks?
→ Bit operations

Need subsets?
→ Bitmask

Need unique element?
→ XOR

Need optimization DP?
→ Bitmask DP
```

---

# 15. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="bm27"
Bit manipulation = controlling numbers at binary level
```

---

# 16. ONE-LINE SUMMARY

```text id="bm28"
Bits = smallest unit of optimization + subset representation
```

---
