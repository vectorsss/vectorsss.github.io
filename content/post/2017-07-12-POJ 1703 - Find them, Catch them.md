---
title: "POJ 1703 - Find them, Catch them"
date: "2017-07-12"
categories: 
  - "coding"
tags: 
  - "并查集"
url: "/archives/83"
---

**POJ 1703 - Find them, Catch them**  
The police office in Tadu City decides to say ends to the chaos, as launch actions to root up the TWO gangs in the city, Gang Dragon and Gang Snake. However, the police first needs to identify which gang a criminal belongs to. The present question is, given two criminals; do they belong to a same clan? You must give your judgment based on incomplete information. (Since the gangsters are always acting secretly.)

Assume N (N

1. D \[a\] \[b\]  
    where \[a\] and \[b\] are the numbers of two criminals, and they belong to different gangs.
    
2. A \[a\] \[b\]  
    where \[a\] and \[b\] are the numbers of two criminals. This requires you to decide whether a and b belong to a same gang.

**Input**

The first line of the input contains a single integer T (1

**Output**

For each message "A \[a\] \[b\]" in each case, your program should give the judgment based on the information got before. The answers might be one of "In the same gang.", "In different gangs." and "Not sure yet."

**Sample Input**

1  
5 5  
A 1 2  
D 1 2  
A 1 2  
D 2 4  
A 1 4

**Sample Output**

Not sure yet.  
In different gangs.  
In the same gang.

题意：一个城市有两个帮派，现在公安局掌握了一些资料，但是只知道A,B两个属于不同的帮派。要你根据所给的信息判别任意两个人的关系，是属于同一个帮派还是属于不同的帮派，还是他们的关系不能确定了？

解题思路：  
食物链的简化版  
A x y 不能确定xy是否是同一帮派  
D x y 确定xy属于不同帮派  
x表示帮派A x+n表示帮派B

```
#include 
#include 
#include 
using namespace std;
const int N = 100000;
const int MAX = 2*N+16;

int fa[MAX], deep[MAX];

void init()
{
    memset(fa, -1, sizeof(fa));
    memset(deep, 0, sizeof(deep));
}

int find(int x)
{
    if (fa[x] == -1) return x;
    return fa[x] = find(fa[x]);
}

void unite(int x, int y)
{
    x = find(x), y = find(y);
    if (x == y) return;
    if (deep[x]= 20) break;
        scanf("%d%d", &n, &m);
        init();
        //cin>>n>>m;
        if (n>N || m>N) break;
        while (m--) {
            scanf("%s%d%d", c, &x, &y);
            //cin >> c >> x >> y;
            if (c[0] == 'D')
            {
                unite(x, y + n);
                unite(x + n, y);
            }
            else {
                if (same(x, y) || same(x + n, y + n))
                {
                    printf("In the same gang.\n");
                    continue;
                }
                if (same(x, y + n) || same(x + n, y))
                {
                    printf("In different gangs.\n");
                    continue;
                }
                printf("Not sure yet.\n");
            }
        }

    }
    return 0;
}
```
