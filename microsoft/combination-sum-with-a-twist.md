# [216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)

This is classic backtrack question where we need to find the path to make the sum we are given. Bactracking is visualised by the decison tree at which we need to take the number we want to add to our sum until we make it the sum. if its not then we backtrack path.

![image of backtracking](https://imgur.com/a/sKCkBvH)

```py
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        self.res = []
        self.helper([], 1, k, n)
        return self.res

    def helper(self, path, start, k, target):

        if k == 0 and target == 0:
            self.res.append(path)
            return

        if k == 0 or target <= 0:
            return

        for i in range(start, 10):
            self.helper(path+[i], i+1, k-1, target - i)

```

time complexity: O(9!)
space complexity: O(N)
