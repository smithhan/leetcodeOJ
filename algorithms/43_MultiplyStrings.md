## Problem

Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

**Example 1:**
```
Input: num1 = "2", num2 = "3"
Output: "6"
```

**Example 2:**
```
Input: num1 = "123", num2 = "456"
Output: "56088"
```

**Note**

1. The length of both num1 and num2 is < 110.
2. Both `num1` and `num2` contain only digits `0-9`.
3. Both `num1` and `num2`do not contain any leading zero, except the number `0` itself.
4. You must not use any built-in BigInteger library or convert the inputs to integer directly.

## Solution

![image](../images/43_MultiplyStrings.png)

```
class Solution:
    def multiply(self, num1, num2):
        n1 = len(num1)
        n2 = len(num2)
        pos = [0] * (n1 + n2)
        i = n1 - 1
        while i >= 0:
            j = n2 - 1
            while j >= 0:
                mul = int(num1[i]) * int(num2[j])
                p1 = i + j
                p2 = i + j + 1
                sum = mul + pos[p2]
                pos[p1] += sum // 10
                pos[p2] = sum % 10
                j -= 1
            i -= 1
        new_pos = []
        for p in pos:
            if not(len(new_pos) == 0 and p == 0):
                new_pos.append(str(p))
        return '0' if len(new_pos) == 0 else ''.join(new_pos)
```
link: https://leetcode.com/problems/multiply-strings/


