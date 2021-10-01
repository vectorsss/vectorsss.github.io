---
title: "UVA 10059 - 	Maximum Product"
date: "2017-07-09"
categories: 
  - "coding"
tags: 
  - "字符串"
  - "枚举"
url: "/archives/88"
---

Given a sequence of integers S = {S1, S2, . . . , Sn}, you should determine what is the value of the  
maximum positive product involving consecutive terms of S. If you cannot find a positive sequence,  
you should consider 0 as the value of the maximum product.  
**Input**  
Each test case starts with 1 ≤ N ≤ 18, the number of elements in a sequence. Each element Si  
is  
an integer such that −10 ≤ Si ≤ 10. Next line will have N integers, representing the value of each  
element in the sequence. There is a blank line after each test case. The input is terminated by end of  
file (EOF).  
**Output**  
For each test case you must print the message: ‘Case #M: The maximum product is P.’, where  
M is the number of the test case, starting from 1, and P is the value of the maximum product. After  
each test case you must print a blank line.  
**Sample Input**  
3  
2 4 -3  
5  
2 5 -1 2 -1  
**Sample Output**  
Case #1: The maximum product is 8. 
Case #2: The maximum product is 20.

**题目大意**  
给出一段长度为 N（N≤ 18）的整数序列，请你找出其中乘积最大且为正值的连续子序列，输出乘积值。

```
#include 
#include 
#define T 30   
//30为数组最大长度

int main()
{    
    int d,M=0;//M为组号
    while(scanf("%d",&d)!=EOF&&dpmax)
                pmax=p;
        }

        }

        M++;
    printf("Case #%d: The maximum product is %lld.\n\n",M,pmax);

        }

    return 0;
}
```
