# [368. Largest Divisible Subset](https://leetcode.com/problems/largest-divisible-subset/)

```py
class Solution:
    def largestDivisibleSubset(self, nums: List[int]) -> List[int]:
        if len(nums) == 0: return []
        nums.sort()
        sol = [[num] for num in nums]
        print(sol)
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] % nums[j] == 0 and len(sol[i]) < len(sol[j]) + 1:
                    sol[i] = sol[j] + [nums[i]]
                # print(sol)
        return max(sol, key=len)
```