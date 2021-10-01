---
title: "POJ 2456 - Aggressive cows(二分)"
date: "2017-07-17"
categories: 
  - "coding"
tags: 
  - "二分三分查找"
url: "/archives/70"
---

**Description**

Farmer John has built a new long barn, with N (2

His C (2

**Input**

- Line 1: Two space-separated integers: N and C
    
- Lines 2..N+1: Line i+1 contains an integer stall location, xi
    

**Output**

- Line 1: One integer: the largest minimum distance

**Sample Input**

5 3  
1  
2  
8  
4  
9

**Sample Output**

3

**Hint**

OUTPUT DETAILS:

FJ can put his 3 cows in the stalls at positions 1, 4 and 8, resulting in a minimum distance of 3.

Huge input data,scanf is recommended.

* * *

题目大意：农夫养牛，牛喜欢打架，所以两个牛的距离越远越好。输入n m，n个房间，m头牛。依次输入房间坐标。如何分配房间使得每个牛直接的距离都尽量大，求满足这个条件两个牛房间距离的最小值

Solution：先对输入的房间坐标进行排序，然后二分查找即可。第一个房间先放一只牛,a\[f\]为上一头牛所在房间坐标 如果mid为所求解 当且仅当a\[i\]-a\[f\]≥mid。如果满足条件sum+1。如果sum大于等于m，说明mid小于所求解，更新l=mid。

* * *

```

#include 
#include 
#include 
#include
#include 
using namespace std;
const int N = 100010;
int a[N];
int n, m;

int judge(int mid)
{
    int f = 0;//f为 上一头牛 所在的房间号
    int sum = 1;//记录房间总数
    for (int i = 1; i if (a[i] - a[f] >= mid)//如果mid为所求解 当且仅当a[i]-a[f]大于等于mid
        {
            f=i;
            sum++;
        }
        else continue;
    }
    if (sum >= m) return 1;
    else return 0;

}

int main()
{
    scanf("%d%d", &n, &m);
    for (int i = 0; i scanf("%d", &a[i]);
    sort(a, a + n);
    int l = -1;
    int r = 1000000000;
    int ans;
    while (r - l >= 0)
    {
        int mid = (l + r) / 2;
        if (judge(mid) == 1)
        {
            ans = mid;
            l = mid;
        }
        else r = mid;
        if (r - l == 1) //终止条件
            break;
    }
    printf("%d\n", ans);
    return 0;
}
```
