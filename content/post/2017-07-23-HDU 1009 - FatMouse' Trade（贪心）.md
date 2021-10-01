---
title: "HDU 1009 - FatMouse' Trade（贪心）"
date: "2017-07-23"
categories: 
  - "coding"
tags: 
  - "贪心算法"
url: "/archives/56"
---

**Description**

FatMouse prepared M pounds of cat food, ready to trade with the cats guarding the warehouse containing his favorite food, JavaBean.  
The warehouse has N rooms. The i-th room contains Jii pounds of JavaBeans and requires Fii pounds of cat food. FatMouse does not have to trade for all the JavaBeans in the room, instead, he may get Jii\* a% pounds of JavaBeans if he pays Fii\* a% pounds of cat food. Here a is a real number. Now he is assigning this homework to you: tell him the maximum amount of JavaBeans he can obtain.

**Input**

The input consists of multiple test cases. Each test case begins with a line containing two non-negative integers M and N. Then N lines follow, each contains two non-negative integers Jii and Fii respectively. The last test case is followed by two -1’s. All integers are not greater than 1000.

**Output**

For each test case, print in a single line a real number accurate up to 3 decimal places, which is the maximum amount of JavaBeans that FatMouse can obtain.

**Sample Input**

5 3  
7 2  
4 3  
5 2  
20 3  
25 18  
24 15  
15 10  
\-1 -1

**Sample Output**

13.333  
31.500

* * *

**Solution**

题目大意：老鼠要买吃的它有m元，有n种吃的，老鼠花费pay元可以得到get的食物。求老鼠最大可以买到多少单位的食物。  
解题思路：pay/get就是一单位食物的价格。定义结构体，定义rat=pay/get，以升序排序。从便宜的买起即可。

* * *

```
#include 
#include 
#include 
#include 
using namespace std;
#define N 10010
struct node
{
    double  get, pay;
    double  rat;
}cat[N];
int cmp(node a, node b)
{
    return a.rat int main(int argc, char const *argv[])
{
    int m, n;
    while (scanf("%d%d", &m, &n))
    {
        if (m == -1 && n == -1) break;
        double ans = 0;
        for (int i = 0; i scanf("%lf%lf", &cat[i].get, &cat[i].pay);
            cat[i].rat = cat[i].pay / cat[i].get;
        }
        sort(cat, cat + n,cmp);
        for (int i = 0; i if (m >= cat[i].pay)
            {
                m -= cat[i].pay;
                ans += cat[i].get;
            }
            else
            {
                ans += m / cat[i].rat;
                break;
            }
        }
        printf("%.3lf\n", ans);
    }
    return 0;
}
```
