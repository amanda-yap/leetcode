# 217. [contains duplicate](https://leetcode.com/problems/contains-duplicate/description/)
You are given a list of integers. Return true if there are duplicate integers in the list.

## solution
We could check every pair of integers in the list and see if there are any duplicates, but that would be a bit inefficient, with a time complexity of O(n^2). 

The easiest solution is to use sets: a set is a collection of unordered elements with no duplicates.

If there are no duplicates in the list, when we turn the list into a set, the size of the set should be the same size as the list. If the size is not the same, then there must be duplicates in the list.

```python
class Solution(object):
    def containsDuplicate(self, nums: List[int) -> bool:
        n = len(nums)
        nums_set = set(nums)
        return n != len(nums_set)
```

**Time complexity:** O(n) | **Space Complexity:** O(n)
