---
title: "POJ 1258 - Agri-Net(最小生成树 Prim)"
date: "2017-07-28"
categories: 
  - "coding"
tags: 
  - "最小生成树"
url: "/archives/50"
---

**Description**

Farmer John has been elected mayor of his town! One of his campaign promises was to bring internet connectivity to all farms in the area. He needs your help, of course.  
Farmer John ordered a high speed connection for his farm and is going to share his connectivity with the other farmers. To minimize cost, he wants to lay the minimum amount of optical fiber to connect his farm to all the other farms.  
Given a list of how much fiber it takes to connect each pair of farms, you must find the minimum amount of fiber needed to connect them all together. Each farm must connect to some other farm such that a packet can flow from any one farm to any other farm.  
The distance between any two farms will not exceed 100,000.

**Input**

The input includes several cases. For each case, the first line contains the number of farms, N (3

**Output**

For each case, output a single integer length that is the sum of the minimum length of fiber required to connect the entire set of farms.

**Sample Input**

4  
0 4 9 21  
4 0 8 17  
9 8 0 16  
21 17 16 0

**Sample Output**

28

* * *

**Solution**  
题目大意：n个农场都互相联通，需要用光纤将这些农场全部连接起来，且光纤长度最小。  
解题思路：最小生成树，输入二维矩阵，代表它们之间的距离。prim模板题

* * *

**Code**

```
#include 
#include 
#define maxn 1000
#define INF 0x3f3f3f3f
using namespace std;
int n, m, fa[maxn];
bool vis[maxn];
int dis[maxn];
int mp[maxn][maxn];

int prim(int n) {
    int ans = 0;
    memset(vis, false, sizeof(vis));
    vis[0] = true;
    for (int i = 0; i 0][i];
    for (int i = 1; i int minn = INF;
        int pos = -1;
        for (int j = 0; jif (!vis[j] && minn>dis[j]) {
                minn= dis[j];
                pos= j;
            }
        }

        if (minn == INF) return -1;
        ans+= minn;
        vis[pos] = true;

        for (int j = 0; jif (!vis[j] && dis[j] > mp[pos][j])
                dis[j] = mp[pos][j];
        }
    }

    return ans;
}



int main()
{
    while (~scanf_s("%d",&n))
    {
        for (int i = 0; i for (int j = 0; j "%d", &mp[i][j]);
        int ans = prim(n);
        printf("%d\n", ans);
    }
    return 0;
}
```
