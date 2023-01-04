# [391. Perfect Rectangle](https://leetcode.com/problems/perfect-rectangle/)

Here we are using line sweeping algorithm. as we need to mind the the area given by two end points is larger or smaller than the rectangle we form and return true or false.

We are using corner as set to filter the same points out of the set and if the corner is less than we need to we return zero.

```py
class Solution:
    def isRectangleCover(self, rectangles: List[List[int]]) -> bool:
        area_sum = 0
        corners = set()
        for x, y, a, b in rectangles:
            area_sum += (a-x) * (b-y)
            corners ^= {(x, y), (x, b), (a, b), (a, y)}

        if len(corners) != 4:
            return False
        x, y = min(corners, key= lambda x: x[0] + x[1])
        a, b = max(corners, key= lambda x: x[0] + x[1])

        return (a-x) * (b-y) == area_sum
```
