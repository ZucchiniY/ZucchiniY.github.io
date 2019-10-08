+++
title = "整数转英文表示"
author = ["Dylan Yang"]
date = 2019-10-08T10:13:00+08:00
categories = ["Python", "Leetcode"]
draft = false
+++

<https://leetcode-cn.com/problems/integer-to-english-words/>

```python
class Solution:
    def numberToWords(self, num: int) -> str:
       one_to_19 = '''One Two Three Four Five Six Seven Eight Nine Ten Eleven Twelve
               Thirteen Fourteen Fifteen Sixteen Seventeen Eighteen Nineteen'''.split()
       tens = 'Twenty Thirty Forty Fifty Sixty Seventy Eighty Ninety'.split()

       def helper(num):
           if num < 20:
               return one_to_19[num - 1:num]
           elif num < 100:
               return [tens[num // 10 - 2]] + helper(num % 10)
           elif num < 1000:
               return [one_to_19[num // 100 -1]] + ['Hundred'] + helper(num % 100)

           for p,w in enumerate(['Thousand','Million','Billion'],1):
               if num < 1000 ** (p+1):
                   return helper(num//1000**p) + [w] + helper(num % 1000 ** p)

        return ' '.join(helper(num)) or "Zero"
```

这里做了两个测试，关于 `if-elif` 和 `if...if` 的时间，在 Leetcode 上测试的时候，发现 `if-elif` 的效率是低于两个 `if...if` 的效率的，具体时候如下：

{{< figure src="/images/py-if-elif.png" caption="Figure 1: 使用 if-elif" >}}

{{< figure src="/images/py-if-if.png" caption="Figure 2: 使用 if...if" >}}

所以在没有具体的逻辑要求的时候，使用 `if...if` 代替 `if-elif` 来提高效率，但是为什么会与我的认知相反呢？很奇怪，有时间希望可以研究一下两个的时间使用效率的差别。
