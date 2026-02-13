# Question 1 — Two Sum (LeetCode)

Given an array and a target, return indices of two numbers whose sum equals target.

---

## Brute Force Approach

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
        return False
```

### Why I first thought this

I checked every possible pair because that is the most natural human way to solve it.

### Why brute force is bad

We compare every number with every other number.

Time Complexity:
O(n²)

For large arrays this becomes very slow (too many repeated checks).

---

## Optimized Approach — Using Dictionary (HashMap)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i in range(len(nums)):
            if target - nums[i] in d:
                return [d[target - nums[i]], i]
            else:
                d[nums[i]] = i
        return False
```

### Idea

Instead of searching the array again, store numbers already seen.

For each number:
needed = target - current

If needed exists → answer found immediately.

### Why this is good

We avoid repeated searching.
Each element is processed only once.

Time Complexity:
O(n)

---

## What I Learned

First solve correctly, then optimize.
The real trick was remembering past values instead of rechecking the array.
