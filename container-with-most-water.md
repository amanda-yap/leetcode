# 11. [container with most water](https://leetcode.com/problems/container-with-most-water/description/) 
You are given an array of integer heights with length n. There are n vertical lines drawn, and the endpoints of each line are `(i, 0)` and `(i, height[i])`.

Find two lines that form a container (with the x-axis) so that the container contains the most water.

Return the maximum amount of water a container can store.

## solution
We could calculate the area of every single pair, but this would have a time complexity of O(n^2).

Let's use a two pointer solution instead. First, we start at the outer heights of the given array. These heights/lines form a container with the x-axis. We then calculate the area of this container, keeping track of whether it is the maximum area we have come across so far.

After calculating the area of the widest container, we will then calculate the area of the second widest container, and so on by moving the left and right pointers. 

Area depends on height and width - when decreasing the width of the container, we want to maximise the height in order to maximise the area. Hence, we will move the left and right pointers, depending on which is pointing to the smaller height; the smaller height limits the area of the container, so moving this pointer inwards to a potentially taller height may increase the area.


```python
class Solution(object):
    def maxArea(self, height: List[int]) -> int:
        l = 0
        r = len(height) - 1 
        max_area = 0

        while l < r:
            max_area = max(max_area, (r - l) * min(height[l], height[r]))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1

        return max_area
```

**Time complexity:** O(n) | **Space Complexity:** O(1)
