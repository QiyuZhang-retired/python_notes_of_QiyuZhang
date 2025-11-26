# Cut Ribbon
**核心算法：动态规划（完全背包）**  
1）状态转移函数：dp表示分割i条带的最大段数  
2）状态转移关系：在索引范围内，dp是前面第a，b，c个数中最大的加一
```python
n, a, b, c = map(int, input().split())

#设置状态转移函数及初始状态
dp=[0]*(n+1)
for i in (a,b,c):
    if i<=n:
        dp[i]=1

#进行状态转移
for i in range(n+1):
    for k in (a,b,c):
        if i>k:
            dp[i]=max(dp[i],dp[i-k]+1)
    if dp[i]<=1 and i not in (a,b,c):
        dp[i]=0

print(dp[n])
```
https://codeforces.com/problemset/problem/189/A
