---
title: offerbook10
date: 2016-09-06 20:47:54
tags: 算法
---
### 剑指offer面试题10
<!-- more -->
``` bash
#include <iostream>
using namespace std ;

int NumberOf1(int n)
{
    int count = 0 ;
    unsigned int flag = 1 ;
    while ( flag )
    {
        if ( n & flag )
        {
            ++count ;
        }
        flag = flag << 1 ;
    }
    return count ;
}

int main()
{
    cout << NumberOf1(3) << endl ;
    return 0 ;
}
```