---
title: "POJ 1064 - Cable master(二分)"
date: "2017-07-17"
categories: 
  - "coding"
tags: 
  - "二分三分查找"
url: "/archives/71"
---

**Description**

Inhabitants of the Wonderland have decided to hold a regional programming contest. The Judging Committee has volunteered and has promised to organize the most honest contest ever. It was decided to connect computers for the contestants using a “star” topology - i.e. connect them all to a single central hub. To organize a truly honest contest, the Head of the Judging Committee has decreed to place all contestants evenly around the hub on an equal distance from it.  
To buy network cables, the Judging Committee has contacted a local network solutions provider with a request to sell for them a specified number of cables with equal lengths. The Judging Committee wants the cables to be as long as possible to sit contestants as far from each other as possible.  
The Cable Master of the company was assigned to the task. He knows the length of each cable in the stock up to a centimeter,and he can cut them with a centimeter precision being told the length of the pieces he must cut. However, this time, the length is not known and the Cable Master is completely puzzled.  
You are to help the Cable Master, by writing a program that will determine the maximal possible length of a cable piece that can be cut from the cables in the stock, to get the specified number of pieces.

**Input**

The first line of the input file contains two integer numb ers N and K, separated by a space. N (1≤N≤10000) is the number of cables in the stock, and K (1≤K≤10000) is the number of requested pieces. The first line is followed by N lines with one number per line, that specify the length of each cable in the stock in meters. All cables are at least 1 meter and at most 100 kilometers in length. All lengths in the input file are written with a centimeter precision, with exactly two digits after a decimal point.

**Output**

Write to the output file the maximal length (in meters) of the pieces that Cable Master may cut from the cables in the stock to get the requested number of pieces. The number must be written with a centimeter precision, with exactly two digits after a decimal point.  
If it is not possible to cut the requested number of pieces each one being at least one centimeter long, then the output file must contain the single number “0.00” (without quotes).

**Sample Input**

4 11  
8.02  
7.43  
4.57  
5.39

**Sample Output**

2.00

**题目大意**：给定n段较长的绳子，需要将这些绳子均等分割成k段。求每段最大长度

**Solution**：每段长度最小为1米，最大为100000米 在这个范围内进行二分即可,可以把米转换成厘米，也可以直接对小数进行二分。保留小数点后两位，也就是说1个单位长度的绳子可以分100次。

```
#include 
#include 
#include
#define N 10010
double a[N];
int n, k;

int judge(double mid)
{
    int sum = 0;
    for (int i = 0; i return sum;
}

int main()
{
    while (~scanf("%d%d", &n, &k)) {
        double r = 100000;
        double l = -1;
        double res = 0;
        for (int i = 0; i scanf("%lf", &a[i]);
        for (int i = 0; i 100; ++i)
        {
            double mid = (l + r) / 2;
            int tmp = judge(mid);
            if (tmp >= k) res = mid, l = mid;
            else r = mid;
        }
        printf("%.2f\n", floor(res * 100) / 100);

    }
    return 0;
}
```
