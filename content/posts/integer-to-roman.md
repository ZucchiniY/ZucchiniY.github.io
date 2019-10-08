+++
title = "整数转罗马数字"
author = ["Dylan Yang"]
date = 2019-10-08T10:06:00+08:00
categories = ["Python", "Leetcode"]
draft = false
+++

<https://leetcode-cn.com/problems/integer-to-roman/>

```python
class Solution:
    def intToRoman(self, num: int) -> str:
        nums = [1000,900,500,400,100,90,50,40,10,9,5,4,1]
        romans = ['M','CM','D','CD','C','XC','L','XL','X','IX','V','IV','I']

        index = 0
        res = ''
        while index < 13:
            while num >= nums[index]:
                res += romans[index]
                num -= nums[index]

            index += 1

        return res
```
