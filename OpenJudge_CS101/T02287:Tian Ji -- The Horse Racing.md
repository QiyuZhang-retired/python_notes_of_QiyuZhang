# T02287:Tian Ji -- The Horse Racing
**算法核心：贪心算法，深度优先搜索**  
方法一：  
1）使用贪心算法，用指针直接得到比赛的方式  
2）贪心的方式：快快取快，慢快取慢，都满兑掉  
3）贪心的正确性：以最快马为依据优选选最优，能赢就赢；若最快马最慢马都不能赢，那自然用最慢马兑掉最快马；若最快马不能赢而最慢马能赢，有两种选择，用田忌最慢
马兑掉王最快马或让最慢马互相比赛，前者最多一赢一负，后者则是最少一赢一负，那么选后者（在这个过程中自然包括了平局的情况）  
4）亦可利用交换调整法证明贪心的正确性
```python
while True:
    try:
        n=int(input())
        if n==0:
            break

        t_horses=list(map(int,input().split()))
        k_horses=list(map(int,input().split()))
        t_horses.sort()
        k_horses.sort()

        #设置指针
        l_t,r_t,l_k,r_k=0,n-1,0,n-1
        output=0

        #进行算法推演
        while l_t<=r_t:
            if t_horses[l_t]>k_horses[l_k]:
                output+=200
                l_t+=1
                l_k+=1
            elif t_horses[r_t]>k_horses[r_k]:
                output+=200
                r_t-=1
                r_k-=1
            else:
                if t_horses[l_t]<k_horses[r_k]:
                    output-=200
                l_t+=1
                r_k-=1

        print(output)
    except EOFError:
        break
```
方法二：
1）用深度优先搜索遍历所有比赛方法，然后找到最优解
http://cs101.openjudge.cn/pctbook/T02287/
