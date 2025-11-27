# Boredom
**核心算法：动态规划**  
方法一：  
1）状态转移函数：使用前i个数取最大  
2）状态转移函数：根据第i个数与第i-1个数的比较来分析是否选择，用is_chosen和cnt来记录选取状态  
3）思路直白，直接对不同情况处理，但是显得冗余
```python
from collections import Counter

n=int(input())
a=list(map(int,input().split()))
a.sort()
count_a=Counter(a)

#设置状态转移函数
dp=[0]*(n+1)
dp[1]=a[0]

#进行状态转移
is_chosen=True
cnt=1
for i in range(2,n+1):
    if a[i-1]==a[i-2]+1:
        cnt=1
        if dp[i-count_a[a[i-2]]-1]+a[i-1]<dp[i-1]:
            dp[i]=dp[i-1]
            is_chosen=False
        else:
            dp[i]=dp[i-count_a[a[i-2]]-1]+a[i-1]
            is_chosen=True
    elif a[i-1]==a[i-2]:
        cnt+=1
        if is_chosen:
            dp[i]=dp[i-1]+a[i-1]
        else:
            if dp[i-count_a[a[i-cnt-1]]-cnt]+a[i-1]*cnt<dp[i-1]:
                dp[i]=dp[i-1]
            else:
                dp[i]=dp[i-count_a[a[i-cnt-1]]-cnt]+a[i-1]*cnt
                is_chosen=True
    else:
        cnt=1
        dp[i]=dp[i-1]+a[i-1]
        is_chosen=True

print(dp[-1])
```
方法二：  
1）利用要取一个数肯定全取相同的数和取一个数不取相邻的数的条件转化  
2）改写为经典“打家劫舍”问题，代码极度简化  
3）用滚动数组节约空间开销
```python
from collections import Counter

n=int(input())
a=list(map(int,input().split()))

#生成“打家劫舍”式的表
count_a=Counter(a)
A=[i*count_a[i] for i in range(max(a)+1)]

#使用滚动数组进行状态转移
x,y=0,A[1]
for i in range(2,max(a)+1):
    x,y=y,max(y,x+A[i])

print(y)
```
https://codeforces.com/contest/455/problem/A
