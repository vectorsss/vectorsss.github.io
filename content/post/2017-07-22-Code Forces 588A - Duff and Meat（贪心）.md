---
title: "Code Forces 588A - Duff and Meat（贪心）"
date: "2017-07-22"
categories: 
  - "coding"
tags: 
  - "贪心算法"
url: "/archives/59"
---

**Description**

Duff is addicted to meat! Malek wants to keep her happy for n days. In order to be happy in i-th day, she needs to eat exactly ai kilograms of meat.

There is a big shop uptown and Malek wants to buy meat for her from there. In i-th day, they sell meat for pi dollars per kilogram. Malek knows all numbers a1, …, an and p1, …, pn. In each day, he can buy arbitrary amount of meat, also he can keep some meat he has for the future.

Malek is a little tired from cooking meat, so he asked for your help. Help him to minimize the total money he spends to keep Duff happy for n days.

**Input**

The first line of input contains integer n (1 ≤ n ≤ 105), the number of days.

In the next n lines, i-th line contains two integers ai and pi (1 ≤ ai, pi ≤ 100), the amount of meat Duff needs and the cost of meat in that day.

**Output**

Print the minimum money needed to keep Duff happy for n days, in one line.

**Example**

**Input**

3  
1 3  
2 2  
3 1

**Output**

10

**Input**

3  
1 3  
2 1  
3 2

**Output**

8

* * *

**Solution**  
题目大意：达夫喜欢吃肉，共n天，每天必须吃掉ai斤肉，每天的肉价为pi。设肉的保质期无上限，求达夫怎样安排可以保证每天吃到足够的肉且花费最小。  
解题思路：简单的贪心，设最小肉价为min，每次都按min买肉。

* * *

**Code**

```
#include 
#include 
#include 
#include 

int main()
{
    int n, a, p;
    while (~scanf("%d", &n))
    {
        int min = 101;int ans = 0;
        for (int i = 1; i "%d%d", &a, &p);
            if (p *p,min = p;
            else ans += min*a;
        }
        printf("%d\n", ans);
    }
    return 0;
}
```
