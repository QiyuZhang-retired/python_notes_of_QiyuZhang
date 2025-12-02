# E02883:Checking order
**算法核心：排序**
```python
while True:
    try:
        a,b,c,d,e=map(int,input().split())

        nums=[a,b,c,d,e]
        if a<=b<=c<=d<=e:
            print('Yes')
        else:
            nums.sort()
            print(f'No {nums[0]} {nums[1]} {nums[2]} {nums[3]} {nums[4]}')

    except EOFError:
        break
```
http://cs101.openjudge.cn/pctbook/E02883/
