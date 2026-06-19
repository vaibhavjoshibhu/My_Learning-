# 🔗 Linked List Patterns Master Sheet (Interview Revision Guide)

Linked Lists are less about “tricks” and more about **pointer manipulation patterns**.

Most problems reduce to:
👉 traversal
👉 reversal
👉 merging
👉 cycle detection
👉 re-linking nodes

---

# 0. When to Use Linked List Patterns?

```text id="ll0"
Ask:

✔ Need dynamic insertion/deletion?
✔ Need pointer manipulation?
✔ Need reversal / reordering?
✔ Need cycle detection?
✔ Need merging sorted sequences?
```

If YES → Linked List.

---

# 1. Core Idea ⭐

```text id="ll1"
Think in pointers, not values.
Change links, not data.
```

---

# 2. Linked List Node

```cpp id="ll2"
struct ListNode {
    int val;
    ListNode* next;

    ListNode(int x){
        val = x;
        next = NULL;
    }
};
```

---

# 3. Core Linked List Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Traversal

```cpp id="ll3"
ListNode* temp = head;

while(temp != NULL){
    temp = temp->next;
}
```

---

# Pattern 2: Fast & Slow Pointer ⭐⭐⭐⭐

## Used for:

* Cycle detection
* Middle of list
* Palindrome check

---

## Template

```cpp id="ll4"
ListNode *slow = head, *fast = head;

while(fast && fast->next){

    slow = slow->next;
    fast = fast->next->next;
}
```

---

## Key Insight

```text id="ll5"
fast moves 2x speed → detects cycle / middle
```

---

# Pattern 3: Cycle Detection (Floyd) ⭐⭐⭐⭐

```cpp id="ll6"
ListNode *slow = head, *fast = head;

while(fast && fast->next){

    slow = slow->next;
    fast = fast->next->next;

    if(slow == fast)
        return true;
}

return false;
```

---

# Pattern 4: Reverse Linked List ⭐⭐⭐⭐⭐

## Iterative

```cpp id="ll7"
ListNode* prev = NULL;
ListNode* curr = head;

while(curr){

    ListNode* next = curr->next;

    curr->next = prev;

    prev = curr;
    curr = next;
}

return prev;
```

---

## Recursive

```cpp id="ll8"
ListNode* reverse(ListNode* head){

    if(!head || !head->next)
        return head;

    ListNode* newHead = reverse(head->next);

    head->next->next = head;
    head->next = NULL;

    return newHead;
}
```

---

# Pattern 5: Merge Two Sorted Lists ⭐⭐⭐

```cpp id="ll9"
ListNode dummy(0);
ListNode* tail = &dummy;

while(l1 && l2){

    if(l1->val < l2->val){
        tail->next = l1;
        l1 = l1->next;
    }
    else{
        tail->next = l2;
        l2 = l2->next;
    }

    tail = tail->next;
}
```

---

# Pattern 6: Merge K Lists ⭐⭐⭐⭐

👉 Heap + Linked List combo

```cpp id="ll10"
priority_queue<ListNode*, vector<ListNode*>, compare> pq;
```

---

# Pattern 7: Remove Nth Node ⭐⭐⭐

```cpp id="ll11"
ListNode* fast = head;
ListNode* slow = head;
```

Move fast n steps → then move both.

---

# Pattern 8: Reorder List ⭐⭐⭐⭐

```text id="ll12"
1. Find middle
2. Reverse second half
3. Merge two halves
```

---

# Pattern 9: Palindrome Linked List ⭐⭐⭐

```text id="ll13"
1. Find middle
2. Reverse second half
3. Compare
```

---

# Pattern 10: LRU Cache ⭐⭐⭐⭐⭐

👉 MOST IMPORTANT DESIGN PROBLEM

Uses:

* Doubly Linked List
* HashMap

---

## Idea:

```text id="ll14"
DLL = maintains order
HashMap = O(1) access
```

---

# Pattern 11: Intersection of Linked Lists ⭐⭐⭐

```cpp id="ll15"
p1 → headA
p2 → headB

when null → switch list
```

---

## Key Trick:

```text id="ll16"
Both pointers travel same distance
```

---

# Pattern 12: Copy Linked List with Random Pointer ⭐⭐⭐⭐

👉 HashMap pattern

```cpp id="ll17"
map<original, copy>
```

---

# Pattern 13: Detect Middle ⭐⭐⭐

```cpp id="ll18"
slow = 1 step
fast = 2 steps
```

---

# Pattern 14: Delete Node in O(1) ⭐

```cpp id="ll19"
node->val = node->next->val;
node->next = node->next->next;
```

---

# 4. Linked List Strategy Patterns

---

## Pattern A: Two Pointer Movement

```text id="ll20"
fast/slow pointer logic
```

Used in:

* cycle
* middle
* palindrome

---

## Pattern B: Reverse + Merge

```text id="ll21"
Break → reverse → reconnect
```

Used in:

* reorder list
* palindrome
* reverse k-group

---

## Pattern C: Dummy Node Trick ⭐

```text id="ll22"
Simplifies edge cases
```

Used in:

* merge
* delete
* partition list

---

# 5. Complexity

```text id="ll23"
Traversal → O(n)
Reversal → O(n)
Merge → O(n)
Cycle detection → O(n)
```

---

# 6. Problem → Pattern Mapping

| Problem          | Pattern               |
| ---------------- | --------------------- |
| Reverse List     | Pointer reversal      |
| Detect Cycle     | Fast/Slow             |
| Middle Node      | Fast/Slow             |
| Merge Lists      | Two pointers          |
| K-group Reverse  | Block reversal        |
| Palindrome       | Reverse + compare     |
| LRU Cache        | DLL + HashMap         |
| Intersection     | Two pointer switching |
| Copy Random List | HashMap               |

---

# 7. Linked List Decision Tree ⭐

```text id="ll24"
Need cycle detection?
→ Fast/slow

Need reversal?
→ Pointer reversal

Need merge?
→ Two pointers

Need random access?
→ HashMap

Need ordering?
→ DLL + design
```

---

# 8. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="ll25"
Linked List problems = pointer manipulation patterns

NOT value-based logic
```

---

# 9. ONE-LINE SUMMARY

```text id="ll26"
Linked List = pointers + restructuring links
```

---
