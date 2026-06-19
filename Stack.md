# 🧠 Stack + Monotonic Stack Master Sheet (Interview Revision Guide)

Stack is one of the most powerful patterns for **“nearest greater/smaller + parsing + order tracking”** problems.

Monotonic Stack is the optimized version used in **O(n)** solutions.

---

# 0. When to Use Stack?

```text id="st0"
Ask:

✔ Need Next Greater / Smaller element?
✔ Need previous greater/smaller?
✔ Need “span” or “distance to closest condition”?
✔ Need to process in reverse order logically?
✔ Expression / parentheses problems?
```

If YES → Stack.

---

# 1. Core Idea ⭐

```text id="st1"
Stack helps track:
→ previous useful elements
→ in correct order
```

---

# 2. Types of Stack Patterns

```text id="st2"
1. Monotonic Increasing Stack
2. Monotonic Decreasing Stack
3. Normal Stack (parsing / simulation)
```

---

# 3. Monotonic Stack Concept ⭐⭐⭐⭐⭐

---

## A) Increasing Stack

```text id="st3"
Stack keeps elements in increasing order
(top is largest recent constraint)
```

Used for:

* Next smaller element
* Histogram problems

---

## B) Decreasing Stack

```text id="st4"
Stack keeps elements in decreasing order
(top is smallest recent constraint)
```

Used for:

* Next greater element
* Stock span
* Daily temperatures

---

# 4. Core Template ⭐⭐⭐

```cpp id="st5"
stack<int> st;

for(int i = 0; i < n; i++){

    while(!st.empty() && condition(st.top(), arr[i])){
        st.pop();
    }

    st.push(i);
}
```

---

# 5. Next Greater Element ⭐⭐⭐

```cpp id="st6"
vector<int> nge(n);

stack<int> st;

for(int i = n-1; i >= 0; i--){

    while(!st.empty() && st.top() <= arr[i]){
        st.pop();
    }

    nge[i] = st.empty() ? -1 : st.top();

    st.push(arr[i]);
}
```

---

# 6. Next Smaller Element ⭐⭐⭐

```cpp id="st7"
while(!st.empty() && st.top() >= arr[i])
    st.pop();
```

---

# 7. Previous Greater/Smaller ⭐⭐⭐

Just traverse left → right instead of right → left.

---

# 8. Stock Span Problem ⭐⭐⭐

```cpp id="st8"
stack<int> st;
vector<int> span(n);

for(int i = 0; i < n; i++){

    while(!st.empty() && arr[st.top()] <= arr[i])
        st.pop();

    span[i] = st.empty() ? i + 1 : i - st.top();

    st.push(i);
}
```

---

# 9. Daily Temperatures ⭐⭐⭐

```cpp id="st9"
stack<int> st;

for(int i = 0; i < n; i++){

    while(!st.empty() && temp[i] > temp[st.top()]){

        int idx = st.top();
        st.pop();

        ans[idx] = i - idx;
    }

    st.push(i);
}
```

---

# 10. Histogram (Largest Rectangle) ⭐⭐⭐⭐⭐

MOST IMPORTANT STACK PROBLEM.

---

## Idea:

Find:

* previous smaller
* next smaller

---

## Template

```cpp id="st10"
stack<int> st;
int maxArea = 0;

for(int i = 0; i <= n; i++){

    while(!st.empty() &&
          (i == n || height[i] < height[st.top()])){

        int h = height[st.top()];
        st.pop();

        int width = st.empty() ? i : i - st.top() - 1;

        maxArea = max(maxArea, h * width);
    }

    st.push(i);
}
```

---

# 11. Valid Parentheses ⭐⭐⭐

```cpp id="st11"
stack<char> st;

for(char c : s){

    if(c == '(') st.push(c);
    else{
        if(st.empty()) return false;
        st.pop();
    }
}
```

---

# 12. Expression Evaluation ⭐⭐⭐

Used for:

* Infix → postfix
* Calculator problems

---

# 13. Monotonic Stack Patterns

---

## Pattern 1: Next Greater / Smaller

```text id="st12"
Use monotonic decreasing stack
```

---

## Pattern 2: Span Problems

```text id="st13"
Use previous greater element logic
```

---

## Pattern 3: Histogram / Area Problems

```text id="st14"
Use both left & right boundaries
```

---

## Pattern 4: Time-based decay problems

```text id="st15"
Stack stores indices + conditions
```

---

# 14. Stack vs Other Structures

| Problem Type            | Data Structure |
| ----------------------- | -------------- |
| Nearest greater/smaller | Stack          |
| Top K elements          | Heap           |
| Range queries           | Segment tree   |
| Subarray sum            | Prefix + Hash  |
| Sliding window max      | Deque          |

---

# 15. Complexity

```text id="st16"
Each element pushed once → O(n)
Each element popped once → O(n)

Total = O(n)
```

---

# 16. Stack Decision Rules ⭐⭐⭐

```text id="st17"
Need "nearest" element?
→ Stack

Need "previous constraint"?
→ Stack

Need "remove until condition breaks"?
→ Stack

Need "span / distance backward"?
→ Stack
```

---

# 17. Problem → Pattern Mapping

| Problem                     | Pattern         |
| --------------------------- | --------------- |
| Next Greater Element        | Monotonic Stack |
| Next Smaller Element        | Monotonic Stack |
| Stock Span                  | Monotonic Stack |
| Daily Temperatures          | Monotonic Stack |
| Largest Rectangle Histogram | Monotonic Stack |
| Valid Parentheses           | Stack           |
| Basic Calculator            | Stack           |
| Remove Adjacent Duplicates  | Stack           |

---

# 18. FINAL MENTAL MODEL ⭐⭐⭐⭐⭐

```text id="st18"
Stack =

"Remember previous useful elements
and remove useless ones fast"
```

---

# 19. ONE-LINE SUMMARY

```text id="st19"
Monotonic Stack = Stack + sorting logic over time
```

---
