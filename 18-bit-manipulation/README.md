# 0️⃣1️⃣ Bit Manipulation Pattern

> **2025 Interview Importance: ⭐⭐ MEDIUM**  
> Essential for Systems Programming, Embedded, and "Math" optimizations. "Find the single number" is a classic interview question.

---

## 📖 What is it? (Deep Dive for Beginners)

### The "Light Switch Panel" Analogy

Your computer stores numbers as a row of **Light Switches** (Bits).
`0 = OFF`, `1 = ON`.

Imagine you have a row of 4 switches: `0 1 0 1` (Binary for 5).
- **AND (&)**: "Both must be ON to stay ON." (Strict parent)
- **OR (|)**: "If either is ON, turn ON." (Lenient parent)
- **XOR (^)**: "If they are DIFFERENT, turn ON." (Contrarian)
- **Shift (<<)**: "Move everyone to the left." (Multiply by 2)

**Why use it?**
It's **Fast**. It happens directly in the CPU hardware.
It saves **Space**. You can store 8 "True/False" flags in a single byte (8 bits) instead of an array of 8 booleans.

### 🏠 Real-World Examples
1.  **Permissions (Linux chmod)**: Value `7` (Binary `111`) means Read(4) + Write(2) + Execute(1). System checks permissions using Bitwise AND.
2.  **Color Codes**: Is `#FF00AB` (Hex) mostly Red? The system extracts the first 8 bits using a "Mask" to check the Red value.
3.  **Data Compression**: Huffman coding uses individual bits to pack data tightly.

---

## 🎯 When to Use This Pattern

**Magic Keywords:**
| If you see... | Think... |
|--------------|----------|
| "Binary representation" | Bitwise Ops |
| "Number of 1 bits" | Bitwise Ops |
| "XOR" | Bitwise Ops |
| "Two unique numbers" | XOR |
| "Power of 2" | Bitwise AND |

**The XOR Trick (`^`):**
- `A ^ A = 0` (Identical numbers cancel out)
- `A ^ 0 = A` (XOR with 0 keeps value)
- `A ^ B ^ A = B` (Order doesn't matter, A's cancel)

---

## 🧠 Core Concept Visualization

```mermaid
graph TD
    A[Number A: 5 (0101)] 
    B[Number B: 3 (0011)]
    
    Op1{A AND B}
    Op2{A OR B}
    Op3{A XOR B}
    
    Op1 --> Res1[0001 (1)]
    Op2 --> Res2[0111 (7)]
    Op3 --> Res3[0110 (6)]
    
    style Res3 fill:#FFD700
```

---

## 📐 Template Code

### Python (Common Operations)
```python
def bit_manipulation_basics(n):
    # 1. Check if ith bit is set (1)
    def check_bit(num, i):
        return (num & (1 << i)) != 0
    
    # 2. Set ith bit (to 1)
    def set_bit(num, i):
        return num | (1 << i)
        
    # 3. Clear ith bit (to 0)
    def clear_bit(num, i):
        mask = ~(1 << i)
        return num & mask
        
    # 4. Toggle ith bit
    def toggle_bit(num, i):
        return num ^ (1 << i)
    
    return "Operations Ready"
```

---

## 🏆 Famous FAANG Problems

### Problem 1: Single Number (Easy)
**Asked by**: Facebook, Amazon, Google
**LeetCode #136**

**Problem**: Array where every element appears twice except for one. Find it.
**Solution**: simple `XOR` all numbers. The duplicates cancel out!
```python
def singleNumber(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```

### Problem 2: Number of 1 Bits (Easy)
**Asked by**: Microsoft, Apple
**LeetCode #191**
**Problem**: Count set bits (Hamming Weight).
*Trick:* `n & (n-1)` drops the lowest set bit. Count how many times you can do this until 0.

### Problem 3: Missing Number (Easy)
**Asked by**: Amazon
**LeetCode #268**
**Problem**: Missing number in range 0..n.
*Solution:* XOR all indices `0..n` versus all values in array. Everything cancels except the missing index!
