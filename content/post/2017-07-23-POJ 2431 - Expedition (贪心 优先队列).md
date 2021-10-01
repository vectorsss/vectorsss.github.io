---
title: "POJ 2431 - Expedition (贪心 优先队列)"
date: "2017-07-23"
categories: 
  - "coding"
tags: 
  - "贪心算法"
url: "/archives/57"
---

**Description**

A group of cows grabbed a truck and ventured on an expedition deep into the jungle. Being rather poor drivers, the cows unfortunately managed to run over a rock and puncture the truck’s fuel tank. The truck now leaks one unit of fuel every unit of distance it travels.

To repair the truck, the cows need to drive to the nearest town (no more than 1,000,000 units distant) down a long, winding road. On this road, between the town and the current location of the truck, there are N (1

The jungle is a dangerous place for humans and is especially dangerous for cows. Therefore, the cows want to make the minimum possible number of stops for fuel on the way to the town. Fortunately, the capacity of the fuel tank on their truck is so large that there is effectively no limit to the amount of fuel it can hold. The truck is currently L units away from the town and has P units of fuel (1

Determine the minimum number of stops needed to reach the town, or if the cows cannot reach the town at all.

**Input**

- Line 1: A single integer, N
    
- Lines 2..N+1: Each line contains two space-separated integers describing a fuel stop: The first integer is the distance from the town to the stop; the second is the amount of fuel available at that stop.
    
- Line N+2: Two space-separated integers, L and P
    

**Output**

- Line 1: A single integer giving the minimum number of fuel stops necessary to reach the town. If it is not possible to reach the town, output -1.

**Sample Input**

4  
4 4  
5 2  
11 5  
15 10  
25 10

**Sample Output**

2

* * *

**Solution**

题目大意：一辆车要去终点，车辆初始油量为P，距离终点距离为L，路上有n个加油站，每个加油站的加油量都不同。求这辆车到终点最少加多少次油？  
解题思路：按照距离终点的距离，进行升序排序。将当前油量可以到达的加油站都放进优先队列，如果P>L，则不加油，否则从优先队列里面选择油量最多的加油站加油即可。

优先队列可以参考另外一个博主的文章  
[C++（标准库）栈和队列以及优先队列的使用](http://blog.csdn.net/smile_kai/article/details/51355989%20%E4%BC%98%E5%85%88%E9%98%9F%E5%88%97)

* * *

**Code**

```
#include 
#include 
#include 
#include 
#include 
#include 
using namespace std;
#define N 10010
struct cmp
{
    int l, cnt;
    bool operator const cmp&b)const
    {
        return l > b.l;
    }
}a[N];
int n, L, P;
priority_queueint>que;
int main() {
    while (~scanf("%d",&n))
    {
        for (int i = 0; i scanf("%d%d", &a[i].l, &a[i].cnt);
        scanf("%d%d", &L, &P);
        if (P >= L) printf("0");
        else
        {
            sort(a, a + n);
            while (!que.empty()) que.pop();
            int i = 0, now = P, ans = 0;
            while (i //车可以到达a[i]加油站
            while (!que.empty())
            {
                now += que.top();
                que.pop();
                ans++;
                if (now >= L) break;
                while (i if (now >= L) printf("%d\n", ans);
            else printf("-1\n");

        }

    }
    return 0;
}
```
