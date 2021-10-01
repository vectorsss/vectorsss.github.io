---
title: "UVA 10006 - Carmichael Numbers(卡迈克尔数 快速幂算法)"
date: "2017-07-21"
categories: 
  - "coding"
tags: 
  - "快速幂"
url: "/archives/64"
---

**Description**

An important topic nowadays in computer science is cryptography. Some people even think that  
cryptography is the only important field in computer science, and that life would not matter at all  
without cryptography.  
Alvaro is one of such persons, and is designing a set of cryptographic procedures for cooking paella. ´  
Some of the cryptographic algorithms he is implementing make use of big prime numbers. However,  
checking if a big number is prime is not so easy. An exhaustive approach can require the division of the  
number by all the prime numbers smaller or equal than its square root. For big numbers, the amount  
of time and storage needed for such operations would certainly ruin the paella.  
However, some probabilistic tests exist that offer high confidence at low cost. One of them is the  
Fermat test.  
Let a be a random number between 2 and n−1 (being n the number whose primality we are testing).  
Then, n is probably prime if the following equation holds:  
**a^n mod n = a**  
If a number passes the Fermat test several times then it is prime with a high probability.  
Unfortunately, there are bad news. Some numbers that are not prime still pass the Fermat test  
with every number smaller than themselves. These numbers are called Carmichael numbers.  
In this problem you are asked to write a program to test if a given number is a Carmichael number.  
Hopefully, the teams that fulfill the task will one day be able to taste a delicious portion of encrypted  
paella. As a side note, we need to mention that, according to Alvaro, the main advantage of encrypted ´  
paella over conventional paella is that nobody but you knows what you are eating.

**Input**

The input will consist of a series of lines, each containing a small positive number n (2 A number n = 0 will mark the end of the input, and must not be processed.

**Output**

For each number in the input, you have to print if it is a Carmichael number or not, as shown in the  
sample output.

**Sample Input**

1729  
17  
561  
1109  
431  
0

**Sample Output**

The number 1729 is a Carmichael number.  
17 is normal.  
The number 561 is a Carmichael number.  
1109 is normal.

* * *

**Solution**

> 卡迈克尔数的定义是对于合数n，如果对于所有正整数b，b和n互素，都有同余式b^(n-1)≡ 1 (mod n)成立，则合数n为Carmichael数。

卡迈克尔数是合数，所以需要先判断n是否是素数。

an mod n\=(a mod n)n mod n\=a

有了如上公式，直接用快速幂算法进行判定即可。

* * *

**Code**

```
#include 
#include 
#define MAXN 65000
typedef long long ll;
ll  mod, ans;
int n;

int isprime(int n)
{
    for (int i = 2; i*i if (n%i == 0)
            return 0;
    return 1;
}

ll power(ll a, ll n, ll m)
{
    ll ans = 1;
    while (n)
    {
        if (n & 1) ans = ans*a%m;
        a = a * a % m;
        n >>= 1;
    }
    return ans;
}


int main()
{


    while (scanf("%d", &n) && n) {
        int flag = 1;
        if (isprime(n)) flag = 0;
        else
        {
            for (ll i = 2; i if (power(i, n, n) != i)
                {
                    flag = 0;
                    break;
                }
        }
        if (flag) printf("The number %d is a Carmichael number.\n",n);
        else printf("%d is normal.\n",n);

    }
    return 0;

}
```
