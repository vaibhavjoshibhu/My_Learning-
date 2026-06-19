# Linked List Interview Master Sheet (Memorize This)

If you remember these **base conditions + 10 patterns + 20 standard problems**, you can solve ~95% of linked-list interview questions.

---

# Universal Base Conditions

```cpp
// Empty list
if (!head) return head;

// Single node
if (!head->next) return head;

// Empty or single node
if (!head || !head->next) return head;
```

For boolean problems:

```cpp
if (!head || !head->next)
    return false;
```

For cycle-start / intersection:

```cpp
if (!head)
    return nullptr;
```

For K-group problems:

```cpp
if (!head || k <= 1)
    return head;
```

For merge problems:

```cpp
if (!l1) return l2;
if (!l2) return l1;
```

---

# Pattern 1: Traversal

```cpp
ListNode* curr = head;

while (curr) {
    curr = curr->next;
}
```

### Used In

* Length
* Search
* Print
* Count nodes

---

# Pattern 2: Reverse List

```cpp
ListNode* reverse(ListNode* head) {

    ListNode* prev = nullptr;
    ListNode* curr = head;

    while (curr) {

        ListNode* nxt = curr->next;

        curr->next = prev;

        prev = curr;
        curr = nxt;
    }

    return prev;
}
```

### Used In

* Reverse List
* Palindrome
* Reorder List
* Reverse K Group
* Reverse Between

---

# Pattern 3: Fast & Slow Pointer

```cpp
ListNode* slow = head;
ListNode* fast = head;

while (fast && fast->next) {
    slow = slow->next;
    fast = fast->next->next;
}
```

### Gives

* Middle node
* Cycle detection
* Cycle start
* Palindrome
* Reorder list

---

# Pattern 4: Dummy Node

```cpp
ListNode dummy(0);
dummy.next = head;

ListNode* temp = &dummy;
```

Return:

```cpp
return dummy.next;
```

### Used In

* Remove Nth Node
* Merge Lists
* Swap Pairs
* Partition List
* Add Numbers

---

# Pattern 5: Gap Pointer

```cpp
ListNode* first = head;
ListNode* second = head;

for(int i=0;i<n;i++)
    first = first->next;

while(first){
    first = first->next;
    second = second->next;
}
```

### Used In

* Remove Nth From End
* Nth Node From End

---

# Pattern 6: Floyd Cycle Detection

```cpp
while(fast && fast->next){

    slow = slow->next;
    fast = fast->next->next;

    if(slow == fast)
        return true;
}
```

---

# Pattern 7: Cycle Starting Node

```cpp
slow = head;

while(slow != fast){
    slow = slow->next;
    fast = fast->next;
}

return slow;
```

---

# Pattern 8: Merge Two Sorted Lists

```cpp
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

tail->next = l1 ? l1 : l2;

return dummy.next;
```

---

# Pattern 9: Find Middle + Reverse

```cpp
while(fast && fast->next){
    slow = slow->next;
    fast = fast->next->next;
}

ListNode* second = reverse(slow);
```

### Used In

* Palindrome
* Reorder List

---

# Pattern 10: Heap

```cpp
priority_queue<
pair<int,ListNode*>,
vector<pair<int,ListNode*>>,
greater<pair<int,ListNode*>>
> pq;
```

### Used In

* Merge K Sorted Lists

---

# 20 Standard Problems

| Problem             | Pattern                  |
| ------------------- | ------------------------ |
| Reverse Linked List | Reverse                  |
| Middle of List      | Slow Fast                |
| Cycle Detection     | Floyd                    |
| Cycle Start         | Floyd Phase 2            |
| Remove Nth From End | Gap Pointer              |
| Merge Two Lists     | Dummy + Merge            |
| Intersection        | Pointer Switching        |
| Palindrome List     | Middle + Reverse         |
| Reverse K Group     | Reverse Sublist          |
| Odd Even List       | Two Chains               |
| Delete Node         | Copy Next                |
| Partition List      | Two Dummy Lists          |
| Add Two Numbers     | Carry                    |
| Sort List           | Merge Sort               |
| Copy Random Pointer | HashMap                  |
| Rotate List         | Circular List            |
| Swap Pairs          | Dummy Node               |
| Reorder List        | Middle + Reverse + Merge |
| Flatten List        | DFS/Stack                |
| Merge K Lists       | Heap                     |

---

# 5 Most Important Interview Templates

### Reverse

```cpp
curr->next = prev;
```

### Slow Fast

```cpp
slow = slow->next;
fast = fast->next->next;
```

### Dummy Node

```cpp
ListNode dummy(0);
```

### Gap Pointer

```cpp
for(int i=0;i<n;i++)
    first = first->next;
```

### Merge

```cpp
tail->next = smallerNode;
tail = tail->next;
```

---

# Golden Rule

Whenever you see a linked-list problem, ask:

1. **Need middle?** → Slow/Fast
2. **Need reverse?** → 3-pointer reverse
3. **Need delete near head?** → Dummy node
4. **Need nth from end?** → Gap pointer
5. **Need sorting/merging?** → Merge template
6. **Need cycle?** → Floyd algorithm
7. **Need palindrome/reorder?** → Middle + Reverse

This decision tree alone is enough to recognize the solution pattern for most linked-list questions within seconds.
