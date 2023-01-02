# [299. Bulls and Cows](https://leetcode.com/problems/bulls-and-cows/)


This is pretty easy sums as we just need to consider the hashmap for storing the count of the secret msg to look up in the table.

```py
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        cnt = Counter(secret)
        cows = 0
        bulls = 0
        print(cnt)
        for i, j in zip(guess, secret):
            if i == j:
                cows += 1
                cnt[i] -= 1

        for i, j in zip(guess, secret):
            if i in cnt and i != j and cnt[i] > 0:
                bulls += 1
                cnt[i] -= 1
        return str(cows) + "A" + str(bulls) + "B"
```
time complexity: O(N)
space complexity: O(N)
