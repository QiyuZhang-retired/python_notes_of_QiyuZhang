# E27653:Fraction类
**核心算法：数学**
```python
import math

a1,b1,a2,b2=map(int,input().split())

b0=b1*b2//math.gcd(b1,b2)
a0=a1*b0//b1+a2*b0//b2

a=a0//math.gcd(a0,b0)
b=b0//math.gcd(a0,b0)

print(f'{a}/{b}')
```
http://cs101.openjudge.cn/pctbook/E27653/
