---
title: "POJ 3233 - Matrix Power Series（矩阵快速幂）"
date: "2017-07-21"
categories: 
  - "coding"
tags: 
  - "快速幂"
url: "/archives/62"
---

**Description**

Given a n × n matrix A and a positive integer k, find the sum S\=A+A2+A3+…+Ak.

**Input**

The input contains exactly one test case. The first line of input contains three positive integers n (n ≤ 30), k (k ≤ 109) and m (m

**Output**

Output the elements of S modulo m in the same way as A is given.

**Sample Input**

2 2 4  
0 1  
1 1

**Sample Output**

1 2  
2 3

* * *

**Solution**  
题目大意：给一个n\*n矩阵A 和 系数k， 求 S\=A+A2+A3+…+Ak 。  
定义一个2n\*2n的矩阵B，I为单位矩阵  

Bn+1\=∣∣∣A0II∣∣∣n+1\=∣∣∣An0A+A2+A3+...+An+II∣∣∣

  
求Bn+1取B\[0\]\[1\]−I即可。

* * *

**Code**

```
include #include 
#include 
#include 
using namespace std;
#define maxn 100
typedef long long ll;
struct Mat
{
    int mat[maxn][maxn];//矩阵 
    int row, col;//矩阵行列数 
};
Mat mod_mul(Mat a, Mat b, int p)//矩阵乘法 
{
    Mat ans;
    ans.row = a.row;
    ans.col = b.col;
    memset(ans.mat, 0, sizeof(ans.mat));
    for (int i = 1;i for (int j = 1;j for (int k = 1;k return ans;
}
Mat mod_pow(Mat a, int k, int p)//矩阵快速幂 
{
    Mat ans;
    ans.row = a.row;
    ans.col = a.col;
    for (int i = 1;i for (int j = 1;j while (k)
    {
        if (k & 1)ans = mod_mul(ans, a, p);
        a = mod_mul(a, a, p);
        k >>= 1;
    }
    return ans;
}
int main()
{
    int n, m, k;
    while (~scanf("%d%d%d", &n, &k, &m))
    {
        Mat A;
        A.row = A.col = 2 * n;
        memset(A.mat, 0, sizeof(A.mat));
        for (int i = 1; i for (int j = 1; j scanf("%d", &A.mat[i][j]);
        for (int i = 1; i 1;//初始化单位矩阵
        Mat B = mod_pow(A, k + 1, m);
        for (int i = 1; i for (int j = n+1; j 2*n; j++)
            {
                if (i + n == j) printf("%d", ((B.mat[i][j] - 1) % m+m)%m);//((B.mat[i][j] - 1) % m+m)%m 避免结果为负数
                else printf("%d", B.mat[i][j]);
                printf("%c", j == 2 * n ? '\n' : ' ');
            }

    }
    return 0;
}
```
