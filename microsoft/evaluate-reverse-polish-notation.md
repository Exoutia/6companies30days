# [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)


Reverse polish notation is the mathematical notation in which the expression are written in (a,b,+) like this instead of (a+b).

So in this expression we need to calculate the number in order they are provided and push them again for evaulating the other steps this can be done by the stack data structure.

1. First take a empty stack.
2. Now we will access the elements of token one by one from start to finish.
3. At every step if the element we accessed is a number then we push it into stack if the element is a symbol we will pop the top two elements and evaluate the numbers according the symbol and push it again to the stack.
4. There will be some rules we need to follow for minus and divide which is to evaulate like this: [a, b] if the cur symbol is '-' or '/' then we will first pop b, and then a and the evaluate will be done like this, (a-b) or (a/b).
5. At the end of loop we will return the only number left in stack.


```py
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for i in tokens:
            if i == '+':
                stack.append(stack.pop() + stack.pop())
            elif i == '-':
                a, b = stack.pop(), stack.pop()
                stack.append(b-a)
            elif i == '*':
                stack.append(stack.pop()*stack.pop())
            elif i == '/':
                a, b = stack.pop(), stack.pop()
                stack.append(int(b/a))
            else:
                stack.append(int(i))
        return stack.pop()
```

