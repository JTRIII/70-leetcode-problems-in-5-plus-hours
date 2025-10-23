# [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

### Problem Description:

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.
 

**Example 1:**
> Input: nums = [1,2,3,1]
>
> Output: true
>
> Explanation:
>
> The element 1 occurs at the indices 0 and 3.

**Example 2:**
> Input: nums = [1,2,3,4]
>
> Output: false
>
> Explanation:
>
> All elements are distinct.

**Example 3:**
> Input: nums = [1,1,1,3,3,4,3,2,4,2]
>
> Output: true

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`


### My first solution:
``` py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashmap = {}

        for num in nums:
            if num not in hashmap:
                hashmap[num] = 0
            hashmap[num] += 1

            if hashmap[num] > 1:
                return True
        return False
```


### Better solution

Python has a cool thing called sets. They do not allow duplicate items. So, if the length of our set and the length of our numbers array are not equal, that means there was a duplicate item so we return `True`. If they are the same length, that means that every item is unique, we return `False`

``` py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        my_set = set(nums)
        if len(my_set) != len(nums):
            return True
        return False
```