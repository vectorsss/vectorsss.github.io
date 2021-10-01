---
title: "HDU 1702 - ACboy needs your help again!"
date: "2017-07-14"
categories: 
  - "coding"
tags: 
  - "数据结构"
url: "/archives/78"
---

ACboy was kidnapped!!  
he miss his mother very much and is very scare now.You can't image how dark the room he was put into is, so poor :(.  
As a smart ACMer, you want to get ACboy out of the monster's labyrinth.But when you arrive at the gate of the maze, the monste say :" I have heard that you are very clever, but if can't solve my problems, you will die with ACboy."  
The problems of the monster is shown on the wall:  
Each problem's first line is a integer N(the number of commands), and a word "FIFO" or "FILO".(you are very happy because you know "FIFO" stands for "First In First Out", and "FILO" means "First In Last Out").  
and the following N lines, each line is "IN M" or "OUT", (M represent a integer).  
and the answer of a problem is a passowrd of a door, so if you want to rescue ACboy, answer the problem carefully!

**Input**

The input contains multiple test cases.  
The first line has one integer,represent the number oftest cases.  
And the input of each subproblem are described above.

**Output**

For each command "OUT", you should output a integer depend on the word is "FIFO" or "FILO", or a word "None" if you don't have any integer.

**Sample Input**

4  
4 FIFO  
IN 1  
IN 2  
OUT  
OUT  
4 FILO  
IN 1  
IN 2  
OUT  
OUT  
5 FIFO  
IN 1  
IN 2  
OUT  
OUT  
OUT  
5 FILO  
IN 1  
IN 2  
OUT  
IN 3  
OUT

**Sample Output**

1  
2  
2  
1  
1  
2  
None  
2  
3

题意：栈和队列的模拟，栈（先进后出），队列（先进先出）

```
#include
#include
#include
#include

using namespace std;

int t, n;
void Stack() {
    char c[5];
    int x;
    stack s;
    for (int  i = 0; i q;
    for (int i = 0; i 
```
