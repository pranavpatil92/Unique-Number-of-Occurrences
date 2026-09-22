# LeetCode 1207 — Unique Number of Occurrences

## Problem

Given an array of integers `arr`, determine whether the number of occurrences of each value is unique.

### Example

```text
Input:
[1, 2, 2, 1, 1, 3]

Occurrences:
1 → 3
2 → 2
3 → 1

Since 3, 2, and 1 are all different:
Output → true
```

---

## Approach

I used a **brute-force approach** with nested loops.

### Logic

1. Use `i` to pick an element from the array.
2. Use `j` to scan the complete array and count how many times `arr[i]` occurs.
3. Use `k` to pick another element.
4. Use another `j` loop to count how many times `arr[k]` occurs.
5. Compare the two occurrence counts.
6. If two different elements have the same occurrence count, return `false`.
7. If no duplicate occurrence count is found, return `true`.

### Variable Roles

```text
i       → picks the first element
j       → scans the array
count1  → frequency of arr[i]

k       → picks another element
j       → scans the array again
count2  → frequency of arr[k]
```

---

## C++ Solution

```cpp
class Solution {
public:
    bool uniqueOccurrences(vector<int>& arr) {
        int n = arr.size();

        for (int i = 0; i < n; i++) {

            int count1 = 0;

            // Count how many times arr[i] occurs
            for (int j = 0; j < n; j++) {
                if (arr[i] == arr[j]) {
                    count1++;
                }
            }

            // Compare with another element
            for (int k = i + 1; k < n; k++) {

                int count2 = 0;

                // Count how many times arr[k] occurs
                for (int j = 0; j < n; j++) {
                    if (arr[k] == arr[j]) {
                        count2++;
                    }
                }

                // Same frequency for different elements
                if (arr[i] != arr[k] && count1 == count2) {
                    return false;
                }
            }
        }

        return true;
    }
};
```

---

## Dry Run

For:

```text
arr = [1, 2, 2, 1, 1, 3]
```

The frequencies are:

```text
1 → 3 occurrences
2 → 2 occurrences
3 → 1 occurrence
```

Comparison:

```text
3 vs 2 → different
3 vs 1 → different
2 vs 1 → different
```

Therefore:

```text
Output: true
```

---

## Complexity

### Time Complexity

The solution uses multiple nested loops.

```text
O(n³)
```

### Space Complexity

Only a few variables are used.

```text
O(1)
```

---

## Key Learning

This problem helped me understand how to use nested loops for **frequency counting and comparison**.

The main pattern I learned was:

```text
Pick → Scan → Count
        ↓
Pick another → Scan → Count
        ↓
Compare frequencies
```

This is a brute-force solution. A more optimized solution can use data structures such as a **hash map** and **set** to reduce the time complexity.
