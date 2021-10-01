---
title: "hdu 5143 NPY and arithmetic progression(枚举)"
date: "2017-07-06"
categories: 
  - "coding"
tags: 
  - "字符串"
  - "枚举"
url: "/archives/96"
---

NPY is learning arithmetic progression in his math class. In mathematics, an arithmetic progression (AP) is a sequence of numbers such that the difference between the consecutive terms is constant.(from wikipedia)  
He thinks it's easy to understand,and he found a challenging problem from his talented math teacher:  
You're given four integers, $a\_1, a\_2, a\_3, a\_4$, which are the numbers of 1,2,3,4 you have.Can you divide these numbers into some Arithmetic Progressions,whose lengths are equal to or greater than 3?(i.e.The number of AP can be one)  
Attention: You must use every number exactly once.  
Can you solve this problem?  
**Input**  
The first line contains a integer T — the number of test cases (1≤T≤1000001≤T≤100000).  
The next T lines,each contains 4 integers a1,a2,a3,a4(0≤a1,a2,a3,a4≤109)a1,a2,a3,a4(0≤a1,a2,a3,a4≤109).  
**Output**  
For each test case,print "Yes"(without quotes) if the numbers can be divided properly,otherwise print "No"(without quotes).  
**Sample Input**

> 3  
> 1 2 2 1  
> 1 0 0 0  
> 3 0 0 0

**Sample Output**

> Yes  
> No  
> Yes

```
/*
解题思路：等差数列共三种情况：123 234 1234 用光所有数字，组成0到多个长度至少为3的等差数列 组不成等差数列返回No 组成返回Yes
            1. a个1 b个2 c个3 d个4 组成公差为1的等差数列后 剩余的数字大于3的话可以自身组成公差为0的等差数列（例如组成2个123 一个333 那么输入的abcd依次为2250）
            2. a个1 b个2 c个3 d个4 刚好用完，组成多个公差为1的等差数列
*/

#include
#include
#define MAX 100000
#define MAX2 1000000000
int main()
{
    int i,j,k,T,flag;
    int a,b,c,d;
    scanf("%d",&T);
    if (T=3))&&((b-i-j-k==0)||(b-i-j-k>=3))&&((c-i-j-k==0)||(c-i-j-k>=3))&&((d-j-k==0)||(d-j-k>=3)))
                            {flag=1;break;}
                    }




        if (flag)
            printf("Yes\n");        
        else
            printf("No\n");
    }
    }    
    }


    return 0;
}
```
