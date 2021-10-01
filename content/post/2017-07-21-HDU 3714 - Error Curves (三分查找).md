---
title: "HDU 3714 - Error Curves (三分查找)"
date: "2017-07-21"
categories: 
  - "coding"
tags: 
  - "二分三分查找"
url: "/archives/66"
---

**Description**

Josephina is a clever girl and addicted to Machine Learning recently. She  
pays much attention to a method called Linear Discriminant Analysis, which  
has many interesting properties.  
In order to test the algorithm’s efficiency, she collects many datasets.  
What’s more, each data is divided into two parts: training data and test  
data. She gets the parameters of the model on training data and test the  
model on test data. To her surprise, she finds each dataset’s test error curve is just a parabolic curve. A parabolic curve corresponds to a quadratic function. In mathematics, a quadratic function is a polynomial function of the form f(x) = ax2 + bx + c. The quadratic will degrade to linear function if a = 0.

  
![](https://image.i-ll.cc/2021-10-01-130720.png)

It’s very easy to calculate the minimal error if there is only one test error curve. However, there are several datasets, which means Josephina will obtain many parabolic curves. Josephina wants to get the tuned parameters that make the best performance on all datasets. So she should take all error curves into account, i.e., she has to deal with many quadric functions and make a new error definition to represent the total error. Now, she focuses on the following new function’s minimum which related to multiple quadric functions. The new function F(x) is defined as follows: F(x) = max(Si(x)), i = 1…n. The domain of x is 0,1000. Si(x) is a quadric function. Josephina wonders the minimum of F(x). Unfortunately, it’s too hard for her to solve this problem. As a super programmer, can you help her?

**Input**

The input contains multiple test cases. The first line is the number of cases T (T

**Output**

For each test case, output the answer in a line. Round to 4 digits after the decimal point.

**Sample Input**

2  
1  
2 0 0  
2  
2 0 0  
2 -4 2

**Sample Output**

0.0000  
0.5000

* * *

**Solution**  
题目大意：给定n个函数 f(x)\=ax2+bx+c,有一个新函数F(x)\=max(Si(x)),i\=1...n,求F(x)的最小值。结果保留四位小数。F(x)的意思是在给定所有的方程f(x)中，取在区间\[0,1000\]内的最大值连成的曲线。求F(x)的最小值。a>0开口向上，直接三分即可。

* * *

**Code**

```
#include 
#include 
#include 
using namespace std;
#define eps 1e-9
const int N = 10010;
int a[N], b[N], c[N];
int n;


double fx(double x)
{
    double ans = a[0] * x*x + b[0] * x + c[0];
    for (int i = 1; i return ans;
}


int main( )
{
    int T;
    scanf("%d", &T);
    while (T--)
    {
        scanf("%d", &n);
        for (int i = 0; i scanf("%d%d%d", &a[i], &b[i], &c[i]);
        double l = 0, r = 1000;
        while (r-l>eps)
        {
            double lmid = l + (r - l) / 3;
            double rmid = r - (r - l) / 3;
            if (fx(lmid)else l = lmid;

        }
        printf("%.4lf\n", fx(l));

    }
    return 0;
}
```
