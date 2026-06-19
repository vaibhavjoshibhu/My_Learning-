# 🌲 Trie (Prefix Tree) Master Sheet — Interview Revision Guide

Trie is a data structure used to **store strings efficiently for prefix-based operations**.

It is heavily used in:

* dictionary problems
* autocomplete
* prefix search
* word search optimization

---

# 0. When to Use Trie?

```text id="tr0"
Ask:

✔ Need prefix search?
✔ Need dictionary / word lookup?
✔ Need autocomplete / suggestions?
✔ Many string queries with shared prefixes?
✔ Search words in board efficiently?
```

If YES → Trie.

---

# 1. Core Idea ⭐

```text id="tr1"
Store characters in a tree where:
→ each node = character
→ path = word/prefix
```

---

# 2. Trie Node Structure ⭐⭐⭐

```cpp id="tr2"
struct TrieNode {

    TrieNode* children[26];
    bool isEnd;

    TrieNode(){
        isEnd = false;

        for(int i = 0; i < 26; i++)
            children[i] = NULL;
    }
};
```

---

# 3. Core Operations ⭐⭐⭐⭐⭐

---

## A) Insert Word

```cpp id="tr3"
void insert(TrieNode* root, string word){

    TrieNode* node = root;

    for(char c : word){

        int idx = c - 'a';

        if(node->children[idx] == NULL)
            node->children[idx] = new TrieNode();

        node = node->children[idx];
    }

    node->isEnd = true;
}
```

---

## B) Search Word

```cpp id="tr4"
bool search(TrieNode* root, string word){

    TrieNode* node = root;

    for(char c : word){

        int idx = c - 'a';

        if(node->children[idx] == NULL)
            return false;

        node = node->children[idx];
    }

    return node->isEnd;
}
```

---

## C) Prefix Search ⭐

```cpp id="tr5"
bool startsWith(TrieNode* root, string prefix){

    TrieNode* node = root;

    for(char c : prefix){

        int idx = c - 'a';

        if(node->children[idx] == NULL)
            return false;

        node = node->children[idx];
    }

    return true;
}
```

---

# 4. Core Trie Patterns ⭐⭐⭐⭐⭐

---

# Pattern 1: Prefix Search ⭐⭐⭐⭐

```text id="tr6"
Check if any word starts with prefix
```

Used in:

* autocomplete
* dictionary lookup

---

# Pattern 2: Word Dictionary ⭐⭐⭐⭐

Supports:

* add word
* search word
* wildcard search ('.')

---

# Pattern 3: Word Search in Grid ⭐⭐⭐⭐⭐

```text id="tr7"
Combine:
→ DFS + Trie
```

Used in:

* Leetcode Word Search II

---

# Pattern 4: Auto-complete System ⭐⭐⭐⭐

```text id="tr8"
Prefix → return all words under node
```

---

# Pattern 5: Longest Prefix Matching ⭐⭐⭐

Used in:

* IP routing
* dictionary matching

---

# 5. Trie vs HashMap

| Feature       | Trie           | HashMap   |
| ------------- | -------------- | --------- |
| Prefix search | Fast           | Slow      |
| Exact search  | O(1 avg)       | O(1 avg)  |
| Memory        | High           | Low       |
| Use case      | strings prefix | key-value |

---

# 6. Complexity

```text id="tr9"
Insert  → O(L)
Search  → O(L)
Prefix  → O(L)

L = length of word
```

---

# 7. Trie Decision Rules ⭐⭐⭐

```text id="tr10"
Need prefix search?
→ Trie

Many string queries?
→ Trie

Word search in grid?
→ Trie + DFS

Autocomplete?
→ Trie
```

---

# 8. Problem → Pattern Mapping

| Problem        | Pattern        |
| -------------- | -------------- |
| Implement Trie | Basic Trie     |
| Search Word    | Trie search    |
| Prefix Search  | Trie           |
| Word Search II | Trie + DFS     |
| Auto-complete  | Trie traversal |
| Replace Words  | Trie prefix    |
| Longest Word   | Trie           |

---

# 9. Core Mental Model ⭐⭐⭐⭐⭐

```text id="tr11"
Trie = "prefix tree where paths represent words"
```

---

# 10. ONE-LINE SUMMARY

```text id="tr12"
Trie = optimized tree for prefix-based string operations
```

---
