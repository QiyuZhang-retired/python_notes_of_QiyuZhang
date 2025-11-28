# M01742:Coins
**核心算法：动态规划（多重背包）**  
1）通过二进制拆分把问题改变为01背包问题  
2）滚动数组解决01背包问题  
3）本题可以用状压dp大大优化运行速度
```python
while True:
    n,m=map(int,input().split())
    if (n,m)==(0,0):
        break
    A_C=list(map(int,input().split()))

    #进行二进制拆分并剪枝
    values=[]
    for i in range(n):
        value=A_C[i]
        remaining=A_C[i+n]
        if value<=m:
            binary=[]
            k=1
            while remaining>=k:
                if k*value<=m:
                    binary.append(k*value)
                    remaining-=k
                    k<<=1
                else:
                    break
            if 0<remaining*value<=m:
                binary.append(remaining*value)

            values+=binary

    #设置状态转移函数
    N=len(values)
    dp=[False]*(m+1)
    dp[0]=True

    #进行状态转移
    for i in range(N):
        for j in range(m,values[i]-1,-1):
            if dp[j-values[i]]:
                dp[j]=True

    print(dp.count(True)-1)
```
http://cs101.openjudge.cn/practice/01742/
