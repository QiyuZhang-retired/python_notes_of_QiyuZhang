# M01384:Piggy-Bank
**核心算法：动态规划（完全背包）**  
1）状态转移函数：i承重下的最小数目  
2）状态转移关系：i承重的dp应该是其前面少一个硬币可以凑出的数目中最小的加一
```python
T=int(input())
for _ in range(T):
    E,F=map(int,input().split())
    n=F-E
    N=int(input())
    coins=[]
    for _ in range(N):
        P,W=map(int,input().split())
        if W<=n:
            coins.append((P,W))

    #设置状态函数及初态
    dp=[float('inf')]*(n+1)
    dp[0]=0

    #进行状态转移
    for i in range(n+1):
        for coin in coins:
            if i>=coin[1]:
                dp[i]=min(dp[i],dp[i-coin[1]]+coin[0])

    if dp[n]==float('inf'):
        print('This is impossible.')
    else:
        print(f'The minimum amount of money in the piggy-bank is {dp[n]}.')
```
http://cs101.openjudge.cn/practice/01384/
