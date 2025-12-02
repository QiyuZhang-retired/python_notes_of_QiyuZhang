# E04067:回文数字（Palindrome Number）
**算法核心：字符串**
```python
while True:
    try:
        x=input()
        reversed_x=''
        for i in range(len(x)-1,-1,-1):
            reversed_x+=x[i]
        if x==reversed_x:
            print('YES')
        else:
            print('NO')
    except EOFError:
        break
```
http://cs101.openjudge.cn/pctbook/E04067/
