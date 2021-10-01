---
title: "POJ 3069 - Saruman's Army(贪心)"
date: "2017-07-23"
categories: 
  - "coding"
tags: 
  - "贪心算法"
url: "/archives/58"
---

**Description**

Saruman the White must lead his army along a straight path from Isengard to Helm’s Deep. To keep track of his forces, Saruman distributes seeing stones, known as palantirs, among the troops. Each palantir has a maximum effective range of R units, and must be carried by some troop in the army (i.e., palantirs are not allowed to “free float” in mid-air). Help Saruman take control of Middle Earth by determining the minimum number of palantirs needed for Saruman to ensure that each of his minions is within R units of some palantir.

**Input**

The input test file will contain multiple cases. Each test case begins with a single line containing an integer R, the maximum effective range of all palantirs (where 0 ≤ R ≤ 1000), and an integer n, the number of troops in Saruman’s army (where 1 ≤ n ≤ 1000). The next line contains n integers, indicating the positions x1, …, xn of each troop (where 0 ≤ xi ≤ 1000). The end-of-file is marked by a test case with R = n = −1.

**Output**

For each test case, print a single integer indicating the minimum number of palantirs needed.

**Sample Input**

0 3  
10 20 20  
10 7  
70 30 1 7 15 20 50  
\-1 -1

**Sample Output**

2  
4

* * *

**Solution**

题目大意：直线上有N个点，对应的点为Xi，对于任何一个点，以R为半径，它周围必须有被标记的点，在满足这个条件的情况下，求最少需要标记多少个点。  
解题思路：  
先对坐标进行升序排序。  
1\. 以a\[0\]为左端点，找满足a\[i\]>a\[0\]+r的第一个a\[i\],找到后以a\[i-1\]画圆。  
2\. 然后找到满足a\[i-1\]+r 3. 重复上述步骤，直到j=n。

* * *

**Code**

```
#include 
#include 
#include 
#include 
using namespace std;
#define N 1010
int a[N];

int main( )
{
    int r, n,j=1;
    memset(a, -1, sizeof(a));
    while (scanf("%d%d", &r, &n) && r != -1 && n != -1)
    {
        for (int i = 0; i scanf("%d", &a[i]);
        sort(a, a + n);
        int ans = 0;
        int j = 0;
        while (jint temp = a[j];
            while (a[j] - temp 1];
            while (a[j] - temp printf("%d\n", ans);
    }
    return 0;
}
```
