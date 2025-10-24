# [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

### Problem Description

Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return an array of all the integers in the range `[1, n]` that do not appear in `nums`.

 

**Example 1:**
> Input: nums = [4,3,2,7,8,2,3,1]
>
> Output: [5,6]

**Example 2:**
> Input: nums = [1,1]
>
> Output: [2]
 

**Constraints:**
- `n == nums.length`
- `1 <= n <= 105`
- `1 <= nums[i] <= n`
 

Follow up: Could you do it without extra space and in `O(n)` runtime? You may assume the returned list does not count as extra space.

### My Solution
``` py
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        new_array = []
        nums.sort()
        new_set = set(nums)
        for i in range(1, len(nums)+1):
            if i in new_set:
                continue
            new_array.append(i)
        return new_array
```

### stoney codes first solution
``` py
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        set_nums = set(nums)
        ret = []
        for i in range(1, len(nums)+1):
            if i not in set_nums:
                ret.append(i)
        return ret
```

This solution is time O(N) because we iterate through the range and append to new list if not in given list. O(N) space as well.

### stoney codes second solution
``` py
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)):
            temp = abs(nums[i]) - 1
            if nums[temp] > 0:
                nums[temp] *= -1
        
        res = []
        for i, n in enumerate(nums):
            if n > 0:
                res.append(i+1)
        
        return res
```

This solution is O(1) space, but it is a little complex for now so he doesn't go in depth in this solution. If you want to explore the solution, you can.