---
title: "Code Forces 587A - Duff and Weight Lifting（贪心）"
date: "2017-07-22"
categories: 
  - "coding"
tags: 
  - "贪心算法"
url: "/archives/60"
---

**Description**

Recently, Duff has been practicing weight lifting. As a hard practice, Malek gave her a task. He gave her a sequence of weights. Weight of i-th of them is 2wi pounds. In each step, Duff can lift some of the remaining weights and throw them away. She does this until there’s no more weight left. Malek asked her to minimize the number of steps.

Duff is a competitive programming fan. That’s why in each step, she can only lift and throw away a sequence of weights 2a1, …, 2ak if and only if there exists a non-negative integer x such that 2a1 + 2a2 + … + 2ak = 2x, i. e. the sum of those numbers is a power of two.

Duff is a competitive programming fan, but not a programmer. That’s why she asked for your help. Help her minimize the number of steps.

**Input**

The first line of input contains integer n (1 ≤ n ≤ 106), the number of weights.

The second line contains n integers w1, …, wn separated by spaces (0 ≤ wi ≤ 106 for each 1 ≤ i ≤ n), the powers of two forming the weights values.

**Output**

Print the minimum number of steps in a single line.

**Example**

**Input**

5  
1 1 2 3 3

**Output**

2

**Input**

4  
0 1 2 3

**Output**

4

* * *

**Solution**  
题目大意：达夫练习举重，给他n个哑铃，他每次能举起重量满足2a1+2a2+...+2an\=2x.的哑铃。求他需要多少次才能将哑铃举完。第一行输入n表示哑铃总数，第二行输入的表示2的系数，数量不超过n。  
解题思路：a1、a2…ak如果两两不相同，则上面等式不成立，达夫需要n次。由2a+2a\=2a+1,可以知道两个小一号的哑铃可以合并成一个大一号的哑铃。  
可以定义一个数组用来存放2系数的和.  
比如输入 1 1 2 3 3  
则cnt\[1\]=2,cnt\[2\]=1,cnt\[3\]=2，2个1可以合并成一个2,则合并后cnt\[1\]=0,cnt\[2\]=0,cnt\[3\]=1,cnt\[4\]=1。

* * *

**Code**

```
#include 
#include 
#include 
#define maxn 1000100
using namespace std;

int cnt[maxn];
int main(int argc, char const *argv[])
{
    int n,a;
    while (~scanf("%d", &n))
    {
        int ans = 0;
        for (int i = 0; i scanf("%d", &a);
            cnt[a]++;
        }
        for (int i = 0; i 1] += cnt[i] / 2;
            cnt[i] = cnt[i] % 2;
            if (cnt[i]) ans++;

        }
        printf("%d\n", ans);
    }
    return 0;
}
```
