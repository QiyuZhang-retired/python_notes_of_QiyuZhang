# E21459:How old are you？
**算法核心：while循环**
```python
x=int(input())
while x!=1:
    if x%2==0:
        print(f'{x}/2={x//2}')
        x//=2
    else:
        print(f'{x}*3+1={x*3+1}')
        x=x*3+1
```
http://cs101.openjudge.cn/pctbook/E21459/
