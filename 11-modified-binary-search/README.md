# 🔍 Modified Binary Search Pattern

> **2025 Interview Importance: ⭐⭐⭐⭐ HIGH**  
> Searching is fundamental. FAANG loves "Rotated Sorted Arrays" and "Infinite Arrays" because they test boundary conditions perfectly.

---

## 📖 What is it? (Deep Dive for Beginners)

### The "Torn Dictionary" Analogy

**Standard Binary Search:** Looking for "Zebra" in a perfect dictionary.
1. Open Middle (M).
2. "Zebra" is after M. Throw away Left half.
3. Repeat.

**Modified Binary Search:**
Imagine someone took a dictionary, **ripped off the second half (N-Z), and glued it to the front.**
Now it looks like: `[N...Z, A...M]`.
It's "sorted", but "rotated".
To find "Zebra", standard logic fails. You open to "T".
- "Is Zebra after T?" Yes.
- But wait, the list loops back to A!
- You need **Modified Logic** to check which "portion" is sorted and search there.

**Key Insight:**
Even in a rotated or weird array, **at least one half is ALWAYS perfectly sorted.**
- Check Left Half. Is it sorted?
- If yes, is target in there?
- If not, check Right Half.

---

## 🌍 Real-World Applications

### 1. Distributed Log Search
Logs often rotate. `Log_2024.txt` is appended to `Log_2023.txt`. If you search for a timestamp by binary search, you might encounter a "rotated" timeline around the New Year.

### 2. IP Range Lookup
Routers store IP ranges in sorted tables. Finding which range an IP belongs to (Ceiling/Floor) requires binary search variants.

### 3. Git Bisect
To find which commit introduced a bug, you don't check every commit. You pick the middle one. If bug exists, go older. If not, go newer. This is Binary Search applied to debugging!

---

## 🎯 When to Use This Pattern

**Magic Keywords:**
| If you see... | Think... |
|--------------|----------|
| "Sorted array" (or partially sorted) | Modified Binary Search |
| "Search in O(log n)" | Modified Binary Search |
| "Rotated sorted array" | Modified Binary Search |
| "Bitonic array" (Up then Down) | Modified Binary Search |
| "Search in infinite array" | Modified Binary Search |

---

## 🧠 Core Concept Visualization

```mermaid
graph TD
    A[Start: [4,5,6,7,0,1,2]] --> B{Find Mid (7)}
    B --> C{Is Left Half [4,5,6,7] Sorted?}
    C -- Yes --> D{Is Target inside 4..7?}
    C -- No --> E{Right Half MUST be sorted}
    
    D -- Yes --> F[Search Left]
    D -- No --> G[Search Right]
    
    style B fill:#FFD700
    style D fill:#90EE90
```

---

## 📐 Template Code

### Python (Rotated Array Search)
```python
def search_rotated(nums, target):
    left, right = 0, len(nums) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if nums[mid] == target:
            return mid
            
        # Check if Left Half is sorted
        if nums[left] <= nums[mid]:
            # Target is in the sorted left half?
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        # Otherwise, Right Half MUST be sorted
        else:
            # Target is in the sorted right half?
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
                
    return -1
```

---

## 🏆 Famous FAANG Problems

### Problem 1: Search in Rotated Sorted Array (Medium)
**Asked by**: Facebook, Google, Amazon
**LeetCode #33**
The classic logic described above.

### Problem 2: First Bad Version (Easy)
**Asked by**: Facebook, Google
**LeetCode #278**
Example of "Floor/Ceiling" binary search.
`[Good, Good, Good, BAD, BAD, BAD]`
Find the *first* BAD.

### Problem 3: Find Minimum in Rotated Sorted Array (Medium)
**Asked by**: Amazon, Microsoft
**LeetCode #153**
Find the "pivot" point where the rotation happens.
*Logic: If `mid > right`, the dip (min) is to the right.*
