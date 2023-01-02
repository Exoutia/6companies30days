# [396. Rotate Function](https://leetcode.com/problems/rotate-function/)

```js
  f(i)          = 0 * A[0] + 1 * A[1] + 2 * A[2] + .... +  (k-1) * A[k-1] + k * A[k]
  f(i+1)        = 1 * A[0] + 2 * A[1] + 3 * A[2] + ...  +     k  * A[k-1] + 0 * A[k]
=>f(i+1) - f(i) =     A[0]   +   A[1]   +   A[2] + ...  +       A[k-1]    - k * A[k]
   = (A[0]   +   A[1]   +   A[2] + ...  +       A[k-1] +  A[k]) - (k+1) * A[k]
   = sum(Array) - A[k] * array.length
=> f(i+1) = f(i) + sum(Array) -  last element * array.length
```
Above expression should tell you this that at any point we can get the sums of that rotation of array. so we can just pop the array at different and get the max value of rotation. and return the ans.

```py
class Solution:
    def maxRotateFunction(self, nums: List[int]) -> int:
        res = curr = sum(i*j for i, j in enumerate(nums))
        s = sum(nums)
        n = len(nums)
        while nums:
            curr += s - nums.pop() * n
            res = max(res, curr)
        return res
```
