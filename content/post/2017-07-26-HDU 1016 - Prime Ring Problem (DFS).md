---
title: "HDU 1016 - Prime Ring Problem (DFS)"
date: "2017-07-26"
categories: 
  - "coding"
tags: 
  - "搜索"
url: "/archives/54"
---

**Description**

A ring is compose of n circles as shown in diagram. Put natural number 1, 2, …, n into each circle separately, and the sum of numbers in two adjacent circles should be a prime.

Note: the number of first circle should always be 1.

**Input**

n (0

**Output**

The output format is shown as sample below. Each row represents a series of circle numbers in the ring beginning from 1 clockwisely and anticlockwisely. The order of numbers must satisfy the above requirements. Print solutions in lexicographical order.

You are to write a program that completes above process.

Print a blank line after each case.

**Sample Input**

6  
8

**Sample Output**

**Case 1:**

1 4 3 2 5 6  
1 6 5 2 3 4

**Case 2:**

1 2 3 8 5 6 7 4  
1 2 5 8 3 4 7 6  
1 4 7 6 5 8 3 2  
1 6 7 4 3 8 5 2

* * *

**Solution**  
题目大意：输入一个数字n，输出满足相邻的数组相加为素数的序列 序列长度为n。  
解题思路：DFS，n不超过20，先找出50以内的素数，用DFS遍历。

* * *

**Code**

```
#include 
#include 
#define maxn 50
int is_prime[maxn], a[maxn], n, vis[maxn];
void get_prime(int n) {
    memset(is_prime, 0, sizeof(is_prime));
    is_prime[0] = is_prime[1] = 1;
    for (int i = 2;i if (!is_prime[i]) 
        {
            for (int j = 2;j*i 1;
        }

}

void dfs(int step)
{
    int i;
    if (step == n + 1 && !is_prime[a[n] + a[1]])//结束
    {
        for (i = 1; i printf("%d ", a[i]);
        printf("%d\n", a[n]);
        return;
    }
    for (i = 2; i if (!vis[i] && !is_prime[i + a[step - 1]])
        {
            a[step] = i;
            vis[i] = 1;
            dfs(step + 1);
            vis[i] = 0;//回溯
        }
    }
}

int main(int argc, char const *argv[])
{
    int cas = 1;
    get_prime(maxn);
    while (~scanf_s("%d", &n))
    {
        memset(vis, 0, sizeof(vis));
        printf("Case %d:\n", cas++);
        a[1] = 1;
        dfs(2);
        printf("\n");
    }
    return 0;
}
```
