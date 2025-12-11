# M03441:4 Values whose Sum is 0
**算法核心：哈希表**  
直接算复杂度太高，用哈希表查询O(1)复杂度减小时间复杂度
```python
n=int(input())
a=[0]*(n+1)
b=[0]*(n+1)
c=[0]*(n+1)
d=[0]*(n+1)

for i in range(n):
    a[i],b[i],c[i],d[i]=map(int,input().split())

#构建哈希表
hash_dict={}
for i in range(n):
    for j in range(n):
        if not a[i]+b[j] in hash_dict:
            hash_dict[a[i]+b[j]]=0
        hash_dict[a[i]+b[j]]+=1

cnt=0
for i in range(n):
    for j in range(n):
        if -(c[i]+d[j]) in hash_dict:
            cnt+=hash_dict[-(c[i]+d[j])]

print(cnt)
```
http://cs101.openjudge.cn/pctbook/M03441
