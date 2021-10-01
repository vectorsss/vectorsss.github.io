---
title: "POJ 1611 - The Suspects"
date: "2017-07-12"
categories: 
  - "coding"
tags: 
  - "并查集"
url: "/archives/82"
---

**POJ 1611 - The Suspects**

Severe acute respiratory syndrome (SARS), an atypical pneumonia of unknown aetiology, was recognized as a global threat in mid-March 2003. To minimize transmission to others, the best strategy is to separate the suspects from others.  
In the Not-Spreading-Your-Sickness University (NSYSU), there are many student groups. Students in the same group intercommunicate with each other frequently, and a student may join several groups. To prevent the possible transmissions of SARS, the NSYSU collects the member lists of all student groups, and makes the following rule in their standard operation procedure (SOP).  
Once a member in a group is a suspect, all members in the group are suspects.  
However, they find that it is not easy to identify all the suspects when a student is recognized as a suspect. Your job is to write a program which finds all the suspects.

**Input**

The input file contains several cases. Each test case begins with two integers n and m in a line, where n is the number of students, and m is the number of groups. You may assume that 0 A case with n = 0 and m = 0 indicates the end of the input, and need not be processed.

**Output**

For each case, output the number of suspects in one line.

**Sample Input**

100 4  
2 1 2  
5 10 13 11 12 14  
2 0 1  
2 99 2  
200 2  
1 5  
5 1 2 3 4 5  
1 0  
0 0

**Sample Output**

4  
1  
1

**题目大意：**  
n个人，如果有一个人感染了SARS病毒，那么和这个人同组的人都会感染病毒。也就是说和被感染的人有关系的人都感染了病毒。  
输入：n m n为成员个数 m为组数  
输出：被感染的人数  
定义 num\[\] 数组，num\[i\] 表示 i 所在集合的元素数量。 初始化 num\[\] 数组全为 1，每次合并的时候就更新每组代表元素的num\[\] 值。  
最后输出的时候先找到被感染的0号的父节点，然后输出父节点的num\[\].

**解题思路：**

- 定义 num\[\] 数组，num\[i\] 表示 i 所在集合的元素数量。
- 初始化 num\[\] 数组全为 1，每次合并的时候就更新每组代表元素的num\[\] 值。
- 最后输出的时候先找到被感染的0号的父节点，然后输出父节点的num\[\].

```
#include 
#include 
#include 
using namespace std;
const int MAX = 30000;

int fa[MAX], deep[MAX], num[MAX];

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
    x = find(x), y = find(y);
    if (x == y) return;
    if (deep[x] MAX || m > 500) break;
        init();
        for (int i = 0; i 
```
