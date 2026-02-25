# 1. [two sum](https://leetcode.com/problems/two-sum/description/) 
You are given an array of integers and a target integer. Return the indices of two integers that add up to the target. You can assume that each input only has one solution. You cannot use the same element twice. You can return the indices in any order.

## my (brute force) solution

Let's go through each pair of integers in the array until we find a pair whose sum adds up to the target; if we find this pair, we can then return the indices of the pair's integers.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
        return []
```
**Time complexity:** O(n^2) | **Space complexity:** O(1)

Apparently there is a better solution that will beat the time complexity of my current solution :O

## optimised solution

The optimised solution I found online does not seem very intuitive, but it has a time complexity of O(n) instead of O(n^2). Yippee! Let's go through it.

First, we make a hash map to store the integers and their corresponding indices in the given array. We then iterate through the array to calculate the complement of each integer, i.e. what integer can we add to the current integer to make the sum equal the target?

If this complement is in our hash map, we can return the index of the current integer and the index of the complement (stored in the hash map). Otherwise, we can put the current integer and its index into the hash map so that it can be accessed later on as a potential complement to another integer in the array.
```python
class Solution(object):
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        num_map = {}
        n = len(nums)

        for i in range(n):
            complement = target - nums[i]
            if complement in num_map:
                return [num_map[complement], i]
            num_map[nums[i]] = i

        return []
    
```

**Time complexity:** O(n) | **Space complexity:** O(n)
