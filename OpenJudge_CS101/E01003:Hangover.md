# E01003:Hangover
**算法核心：while循环**
```python
while True:
    c=float(input())
    if c==0.00:
        break

    n=0
    sum_up=0

    while sum_up<c:
        sum_up+=1/(n+2)
        n+=1

    print(n,'card(s)')
```
http://cs101.openjudge.cn/pctbook/E01003/
