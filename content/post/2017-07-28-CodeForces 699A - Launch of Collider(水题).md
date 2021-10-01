---
title: "CodeForces 699A - Launch of Collider(水题)"
date: "2017-07-28"
categories: 
  - "coding"
tags: 
  - "水题"
url: "/archives/51"
---

**Description**

There will be a launch of a new, powerful and unusual collider very soon, which located along a straight line. n particles will be launched inside it. All of them are located in a straight line and there can not be two or more particles located in the same point. The coordinates of the particles coincide with the distance in meters from the center of the collider, xi is the coordinate of the i-th particle and its position in the collider at the same time. All coordinates of particle positions are even integers.

You know the direction of each particle movement — it will move to the right or to the left after the collider’s launch start. All particles begin to move simultaneously at the time of the collider’s launch start. Each particle will move straight to the left or straight to the right with the constant speed of 1 meter per microsecond. The collider is big enough so particles can not leave it in the foreseeable time.

Write the program which finds the moment of the first collision of any two particles of the collider. In other words, find the number of microseconds before the first moment when any two particles are at the same point.

**Input**

The first line contains the positive integer n (1 ≤ n ≤ 200 000) — the number of particles.

The second line contains n symbols “L” and “R”. If the i-th symbol equals “L”, then the i-th particle will move to the left, otherwise the i-th symbol equals “R” and the i-th particle will move to the right.

The third line contains the sequence of pairwise distinct even integers x1, x2, …, xn (0 ≤ xi ≤ 109) — the coordinates of particles in the order from the left to the right. It is guaranteed that the coordinates of particles are given in the increasing order.

**Output**

In the first line print the only integer — the first moment (in microseconds) when two particles are at the same point and there will be an explosion.

Print the only integer -1, if the collision of particles doesn’t happen.

**Example**

**Input**

4  
RLRL  
2 4 6 10

**Output**

1

**Input**

3  
LLR  
40 50 60

**Output**

\-1

* * *

**Solution**  
题目大意：给定n个点，它们分别以1m/s的速度在运动，或左或右。求这些点中，最早发生碰撞所需要的时间，如果不能碰撞，输出-1。第一行输入n，第二行输入粒子的运动方向。第三行输入粒子x坐标。  
解题思路：暴力！！！

* * *

**Code**

```
#include 
#include 
#include 
using namespace std;
#define N 200010

int main( )
{

    int n;
    while (~scanf_s("%d", &n))
    {

        int Min = 0X3f3f3f3f;
        int ans = -1;
        int t = 0;
        char s[N];
        int a[N];
        memset(s, -1, sizeof(s));
        memset(a, -1, sizeof(a));
        for (int i = 0; i cin >> s[i];
        for (int i = 0; i "%d", &a[i]);
        for (int i = 0; i if (s[i] == 'R'&&s[i + 1] == 'L')
            {
                ans = (a[i + 1] - a[i]) / 2;
                if (ans//t>0则说明粒子可以发生碰撞
            }
        }
        if (t) printf("%d\n", Min);
        else printf("-1\n");

    }
    return 0;
}
```
