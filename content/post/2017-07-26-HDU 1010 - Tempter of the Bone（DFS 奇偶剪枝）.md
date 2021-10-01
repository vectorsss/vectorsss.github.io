---
title: "HDU 1010 - Tempter of the Bone（DFS 奇偶剪枝）"
date: "2017-07-26"
categories: 
  - "coding"
tags: 
  - "搜索"
url: "/archives/55"
---

**Description**

The doggie found a bone in an ancient maze, which fascinated him a lot. However, when he picked it up, the maze began to shake, and the doggie could feel the ground sinking. He realized that the bone was a trap, and he tried desperately to get out of this maze.

The maze was a rectangle with sizes N by M. There was a door in the maze. At the beginning, the door was closed and it would open at the T-th second for a short period of time (less than 1 second). Therefore the doggie had to arrive at the door on exactly the T-th second. In every second, he could move one block to one of the upper, lower, left and right neighboring blocks. Once he entered a block, the ground of this block would start to sink and disappear in the next second. He could not stay at one block for more than one second, nor could he move into a visited block. Can the poor doggie survive? Please help him.

**Input**

The input consists of multiple test cases. The first line of each test case contains three integers N, M, and T (1

‘X’: a block of wall, which the doggie cannot enter;  
‘S’: the start point of the doggie;  
‘D’: the Door; or  
‘.’: an empty block.

The input is terminated with three 0’s. This test case is not to be processed.

**Output**

For each test case, print in one line “YES” if the doggie can survive, or “NO” otherwise.

**Sample Input**

4 4 5  
S.X.  
..X.  
..XD  
….  
3 4 5  
S.X.  
..X.  
…D  
0 0 0

**Sample Output**

NO  
YES

* * *

**Solution**

题目大意：狗狗要走出一个m\*n的迷宫，S为起点，D为终点，碰到’.’和’D’可以走下一步，碰到’X’代表此路不通。问狗狗能不能在第t步**刚好**走出迷宫。  
解题思路：DFS，奇偶剪枝。tmin=abs(sx-ex)+abs(sy-ey),t与tmin的奇偶性相同。[详情看这里](https://baike.baidu.com/item/%E5%A5%87%E5%81%B6%E5%89%AA%E6%9E%9D)若 ttmin或t≡tmin(mod2)，则进行剪枝。

* * *

**Code**

```
#include 
#include 
#include 
#include 
using namespace std;
int dir[4][2]{ {-1,0},{0,-1},{1,0},{0,1} };//up left lower right
char map[10][10];
int m, n, t;
int sx, sy, ex, ey;
int flag;

void dfs(int x, int y, int t)
{
    if (flag) return;
    if (tabs(x - ex) + abs(y - ey) || (t - abs(x - ex) - abs(y - ey)) % 2)//剪枝
        return;
    if (!t)
    {
        if (x == ex&&y == ey)
            flag = 1;
        return;
    }
    for (int i = 0; i 4; i++)
    {
        int xx = x + dir[i][0];
        int yy = y + dir[i][1];
        if (xx >= 0 && xx= 0 && (map[xx][yy] == '.' || map[xx][yy] == 'D'))
        {
            map[xx][yy] = 'X';
            dfs(xx, yy, t - 1);
            map[xx][yy] = '.';
        }
    }
    return;
}

int main(int argc, char const *argv[])
{
    while (scanf_s("%d%d%d", &m, &n, &t),m)
    {
        for (int i = 0; i for (int j = 0; j cin >> map[i][j];
                if (map[i][j] == 'S')
                    sx = i, sy = j;
                if (map[i][j] == 'D')
                    ex = i, ey = j;
            }
        flag = 0;
        dfs(sx, sy, t);
        if (flag) printf("YES\n");
        else printf("NO\n");
    }
    return 0;
}
```
