---
title: "UVA 10583 - Ubiquitous Religions"
date: "2017-07-10"
categories: 
  - "coding"
tags: 
  - "并查集"
url: "/archives/87"
---

**Ubiquitous Religions**

There are so many different religions in the world today that it is difficult to keep track of them all. You are interested in finding out how many different religions students in your university believe in.

You know that there are n students in your university (0

**Input**

The input consists of a number of cases. Each case starts with a line specifying the integers n and m. The next m lines each consists of two integers i and j, specifying that students i and j believe in the same religion. The students are numbered 1 to n. The end of input is specified by a line in which n = m = 0.

**Output**

For each test case, print on a single line the case number (starting with 1) followed by the maximum number of different religions that the students in the university believe in.

**Sample Input**

10 9  
1 2  
1 3  
1 4  
1 5  
1 6  
1 7  
1 8  
1 9  
1 10  
10 4  
2 3  
4 5  
4 8  
5 8  
0 0

**Sample Output**

Case 1: 1  
Case 2: 7

**题目大意**

当今世界有很多不同的宗教,很难通晓他们。你有兴趣找出在你的大学里有多少种不同的宗教信仰。  
你知道在你的大学里有n个学生(0

**Input**

第一行第一个数字代表宗教总数，第二个为组数

```
#include 
#include 
#include 
using namespace std;
const int N = 50000;
int fa[N], deep[N];

void init()
{
    memset(fa, -1, sizeof(fa));
    memset(deep, 0, sizeof(deep));
}

int find(int x)
{
    if (fa[x] == -1) return x;
    return fa[x] = find(fa[x]);
}

void unite(int x, int y)
{
    x = find(x);y = find(y);
    if (x == y) return;
    if (deep[x]
```
