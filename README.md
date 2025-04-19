# 🚀 Count the Number of Fair Pairs – LeetCode 2563

![LeetCode Badge](https://img.shields.io/badge/LeetCode-Medium-yellow)
![Language](https://img.shields.io/badge/Language-Python-blue)
![Brand](https://img.shields.io/badge/By-Coding%20Moves-green)

## 🧠 Problem Description

Given a 0-indexed integer array `nums` of size `n` and two integers `lower` and `upper`, return the **number of fair pairs**.

A pair `(i, j)` is **fair** if:
- `0 <= i < j < n`, and
- `lower <= nums[i] + nums[j] <= upper`

---

## 📥 Example

### Example 1:
**Input:**  
`nums = [0,1,7,4,4,5]`, `lower = 3`, `upper = 6`  
**Output:**  
`6`  
**Explanation:**  
The 6 fair pairs are: (0,3), (0,4), (0,5), (1,3), (1,4), and (1,5)

---

## 🧠 Approach

We solve this efficiently by:
1. **Sorting** the array.
2. For each element `nums[i]`, using **binary search** to find how many `nums[j]` (`j > i`) satisfy:  
   `lower - nums[i] <= nums[j] <= upper - nums[i]`
3. Using Python's `bisect` module for fast searching.

This approach runs in **O(n log n)** time.

---

## 💻 Code

```python
import bisect

class Solution(object):
    def countFairPairs(self, nums, lower, upper):
        nums.sort()
        n = len(nums)
        count = 0

        for i in range(n):
            low = lower - nums[i]
            high = upper - nums[i]
            left = bisect.bisect_left(nums, low, i + 1)
            right = bisect.bisect_right(nums, high, i + 1)
            count += right - left

        return count

# Example usage
solution = Solution()
print(solution.countFairPairs([0, 1, 7, 4, 4, 5], 3, 6))  # Output: 6
print(solution.countFairPairs([1, 7, 9, 2, 5], 11, 11))   # Output: 1
```

# 📊 Complexity

- Type	Complexity
- Time	O(n log n)
- Space	O(1) (excluding sort)

# ✨ Created by <a href="http//:youtube.come//@Coding_Moves/>Coding Moves</a>
Empowering coders to move with purpose 💻🔥
