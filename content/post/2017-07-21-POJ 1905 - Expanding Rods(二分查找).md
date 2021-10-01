---
title: "POJ 1905 - Expanding Rods(二分查找)"
date: "2017-07-21"
categories: 
  - "coding"
tags: 
  - "二分三分查找"
url: "/archives/65"
---

**Description**

When a thin rod of length L is heated n degrees, it expands to a new length L’=(1+n\*C)\*L, where C is the coefficient of heat expansion.  
When a thin rod is mounted on two solid walls and then heated, it expands and takes the shape of a circular segment, the original rod being the chord of the segment.

Your task is to compute the distance by which the center of the rod is displaced.

  
![](https://image.i-ll.cc/2021-10-01-130724.jpg)

**Input**

The input contains multiple lines. Each line of input contains three non-negative numbers: the initial lenth of the rod in millimeters, the temperature change in degrees and the coefficient of heat expansion of the material. Input data guarantee that no rod expands by more than one half of its original length. The last line of input contains three negative numbers and it should not be processed.

**Output**

For each line of input, output one line with the displacement of the center of the rod in millimeters with 3 digits of precision.

**Sample Input**

1000 100 0.0001  
15000 10 0.00006  
10 0 0.001  
\-1 -1 -1

**Sample Output**

61.329  
225.020  
0.000

* * *

**Solution**

题目大意：长为L的一个竿子，受热后会向上弯曲弯曲后的长度为L′\=(1+n∗C)∗L,求竿子可以向上弯曲的最大值h。L′的增量不超过L/2. 
将L′看作一个半径为R,圆心角为2a的圆的弧长。则L为该圆的弦长。  
可以得到如下公式：  

⎧⎩⎨⎪⎪R2\=(R−h)2+(L/2)2sina\=L/2RRa\=L′/2

刚开始我想通过弧微分把弧长表示出来，然后进行二分。应该是精度出现问题，所以一直过不了。代码在最后！！！

* * *

**AC Code**

```
#include 
#include 
#include 
#define eps 1e-5


int main() 
{
    double L, n, C;
    while (~scanf("%lf%lf%lf",&L,&n,&C)&&L!=-1&&n!=-1&&C!=-1)
    {

        double L1 = (1 + n*C)*L;
        double l = 0, r = L / 2, h;
        while (r-l>eps)
        {
            h = (l + r) / 2;
            double R = ((L*L / 4 + h*h) / (2 * h));
            double a = asin(L / (2 * R));
            if (R*a >= L1 / 2) r = h;
            else l = h;

        }
        printf("%.3f\n", h);
    }
}
```

**WA Code**

```
#include 
#include 
#include
#define eps 1e-10
int L, n;
double C;
double L1, L2, a, c, al;
double lo;
int judge(double L2, double L1)
{
    if (L2 > L1) return 1;
    else return 0;
}
int main()
{
    while (~scanf_s("%d%d%lf", &L, &n, &C) && L != -1 && n != -1 && C != -1) {

        double r = L/2;
        double l = 0;
        double ans;

        while (r-l>eps)
        {

            c = (l + r) / 2;
            al = (-4 * c) / L;
            a = (-4 * c) / (L * L);
            lo = logl(al + sqrtl((double)(1 + al*al)));
            L2 = (al*sqrtl((double)(1 + al*al)) + lo) / (2 * a);
            L1 = (1 + n*C)*L;
            if (judge(L2, L1))  r = c;
            else l = c,ans=c;
        }
        printf("%.3f\n", ans);





    }
    return 0;
}
```
