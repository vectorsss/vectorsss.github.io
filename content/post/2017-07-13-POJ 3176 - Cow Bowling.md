---
title: "POJ 3176 - Cow Bowling"
date: "2017-07-13"
categories: 
  - "coding"
tags: 
  - "动态规划"
url: "/archives/81"
---

The cows don't use actual bowling balls when they go bowling. They each take a number (in the range 0..99), though, and line up in a standard bowling-pin-like triangle like this:

```
          7



        3   8



      8   1   0



    2   7   4   4



  4   5   2   6   5
```

Then the other cows traverse the triangle starting from its tip and moving "down" to one of the two diagonally adjacent cows until the "bottom" row is reached. The cow's score is the sum of the numbers of the cows visited along the way. The cow with the highest score wins that frame.

Given a triangle with N (1

**Input**

Line 1: A single integer, N

Lines 2..N+1: Line i+1 contains i space-separated integers that represent row i of the triangle.

**Output**

Line 1: The largest sum achievable using the traversal rules

**Sample Input**

5  
7  
3 8  
8 1 0  
2 7 4 4  
4 5 2 6 5

**Sample Output**

30

**题目大意：**  
给出一个 n 层的数字三角形，要从最顶端走到最低端，问哪条路径上沿途的数字之和最大？输出这个最大值  
**解题思路：**  
动态规划法  
用数组 a\[\]\[\] 存储数字三角形，定义数组 dp\[\]\[\]，dp\[i\]\[j\] 表示从 a\[0\]\[0\] 走到 a\[i\]\[j\] 能得到的最大值 显然有 dp\[0\]\[0\] = a\[0\]\[0\]  
我们要求的是max{dp\[n-1\]\[j\]|0≤j≤n-1}

j=0 dp\[i\]\[0\] = dp\[i - 1\]\[0\] + a\[i\]\[0\];  
0＜j＜i dp\[i\]\[j\] = max(dp\[i - 1\]\[j - 1\], dp\[i - 1\]\[j\]) + a\[i\]\[j\];  
j=i dp\[i\]\[i\] = dp\[i - 1\]\[i - 1\] + a\[i\]\[i\];

```
#include 
#include 
#define N 350
using namespace std;
int a[N][N], dp[N][N];

int max(int a, int b) {
    return a>b ? a : b;
}

void init() {
    memset(a, 0, sizeof(a));
    memset(dp, 0, sizeof(dp));

}

int main()
{
    int n;
    int i, j;
    int k = 1;
    scanf("%d", &n);
    init();
    for (int i = 0; i 
```
