# 3. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) 
Given a string s, find the length of the longest substring without duplicate characters.

## solution

A brute-force solution would be to identify the longest substrings with no repeating characters for each index and then return the maximum length we find. Let's see if we can use a sliding window for this problem instead.

We can make a hash map to store the most recent indices of the characters we come across. Whenever we come across a repeeated character, we will move the left pointer just enough to remove the repeated character from our window, provided that the left pointer doesn't move backwards.

Then, we update the index of the repeated character in our hash map to its most recent index. At each iteration, we check the size of the current window, updating our result if it is the maximum length we've found.

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s: str) -> int:
        index_map = {}
        l = 0
        result = 0

        for i in range(len(s)):
            if s[i] in index_map:
                l = max(index_map[s[i]] + 1, l)
            index_map[s[i]] = i
            result = max(result, i - l + 1)

        return result
```

**Time Complexity:** O(n) | **Space Complexity:** O(m), where n is the length of the string and m is the number of unique characters in the string.
