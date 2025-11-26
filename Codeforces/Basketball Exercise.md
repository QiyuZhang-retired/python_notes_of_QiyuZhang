# Basketball Exercise
**算法核心：动态递归**  
1）状态转移函数：两行表示以这一排结尾的前i项的最大值  
2）状态转移关系：取这一排前一个值和另一排前一个值加此处的值中较大者
```python
n=int(input())
h_1=list(map(int,input().split()))
h_2=list(map(int,input().split()))
 
#设置状态转移函数
dp=[[0]*n for _ in range(2)]
dp[0][0]=h_1[0]
dp[1][0]=h_2[0]
 
#进行状态转移
for i in range(1,n):
    dp[0][i]=max(dp[1][i-1]+h_1[i],dp[0][i-1])
    dp[1][i]=max(dp[0][i-1]+h_2[i],dp[1][i-1])
 
print(max(dp[0][n-1],dp[1][n-1]))
```
https://codeforces.com/problemset/problem/1195/C
