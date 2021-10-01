---
title: "HDU 1509 - Windows Message Queue"
date: "2017-07-14"
categories: 
  - "coding"
tags: 
  - "数据结构"
url: "/archives/76"
---

Message queue is the basic fundamental of windows system. For each process, the system maintains a message queue. If something happens to this process, such as mouse click, text change, the system will add a message to the queue. Meanwhile, the process will do a loop for getting message from the queue according to the priority value if it is not empty. Note that the less priority value means the higher priority. In this problem, you are asked to simulate the message queue for putting messages to and getting message from the message queue.

**Input**

There's only one test case in the input. Each line is a command, "GET" or "PUT", which means getting message or putting message. If the command is "PUT", there're one string means the message name and two integer means the parameter and priority followed by. There will be at most 60000 command. Note that one message can appear twice or more and if two messages have the same priority, the one comes first will be processed first.(i.e., FIFO for the same priority.) Process to the end-of-file.

**Output**

For each "GET" command, output the command getting from the message queue with the name and parameter in one line. If there's no message in the queue, output "EMPTY QUEUE!". There's no output for "PUT" command.

**Sample Input**

GET  
PUT msg1 10 5  
PUT msg2 10 4  
GET  
GET  
GET

**Sample Output**

EMPTY QUEUE!  
msg2 10  
msg1 10  
EMPTY QUEUE!

题目大意是windows的信息队列是按照优先级执行的，输入PUT时输入一行信息，包括一个字符串和两个整数，第一个整数是元素，第二个是优先级，输入GET指令时按照优先级的从低到高输出信息，当两个优先级相同时按照输入的顺序输出。练习使用优先队列。

注意：当两个优先级相同时按照输入的顺序输出。在程序中记录输入次序，在重载运算符的时候注意比较俩的次序。

```
#include
#include
#include
#include
#include
using namespace std;

struct Node {
    int ord, x,num;
    char c[1000];
    bool operator b.ord;
        return x > b.x;

    }
};

int main() {
    int n, d, cot = 1;
    char s[5];
    Node k;
    priority_queue q;
    while (scanf("%s", s) != EOF) {
        if (!strcmp(s,"PUT"))
        {
            scanf("%s %d %d", k.c, &k.num, &k.x);
                k.ord = cot++;
                q.push(k);
        }
        else if (q.empty()) printf("EMPTY QUEUE!\n");
        else
        {
            printf("%s %d\n", q.top().c, q.top().num);
            q.pop();
        }
    }
    return 0;
}
```
