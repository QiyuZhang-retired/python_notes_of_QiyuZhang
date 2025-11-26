# E01218:THE DRUNK JAILER
**算法核心：for循环**
```python
t=int(input())
for _ in range(t):
    n=int(input())
    prisons=0

    #判断每个牢门被操作几次
    for i in range(1,n+1):
        time=0
        for j in range(2,i+1):
            if i%j==0:
                time+=1
        if time%2==0:
            prisons+=1

    print(prisons)
```
http://cs101.openjudge.cn/pctbook/E01218/
