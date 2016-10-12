---
title: offerbook11
date: 2016-09-06 20:47:59
tags: 算法
---
### 剑指offer面试题11
<!-- more -->
``` bash
#include <iostream>
using namespace std ;

#define PRECISE 0.0000001
bool g_InvalidInput = false ;

bool equal(double num1, double num2)
{
    if ((num1 - num2 > -PRECISE) && 
        (num1 - num2 < PRECISE))
        return true ;
    else 
        return false ;
}

// double PowerWithUnsignedExponent(double base, unsigned int exponent)
// {
//     double result = 1.0 ;
//     for (int i = 1; i <= exponent; ++i)
//     {
//         result *= base ;
//     }

//     return result ;
// }

double PowerWithUnsignedExponent(double base, unsigned int exponent)
{
    if (exponent == 0)
        return 1 ;
    if (exponent == 1)
        return base ;
    double result = PowerWithUnsignedExponent(base, exponent >> 1) ;
    result *= result ;
    if (exponent & 0x1 == 1)
        result *= base ;
    return result ;
}

double Power(double base, int exponent)
{
    g_InvalidInput = false ;
    if (equal(base, 0.0) && exponent < 0)
    {
        g_InvalidInput = true ;
        return 0.0 ;
    }
    unsigned int absExponent = (unsigned int)(exponent) ;
    if (exponent < 0)
    {
        absExponent = (unsigned int)(-exponent) ;
    }
    double result = PowerWithUnsignedExponent(base, absExponent) ;
    if (exponent < 0)
    {
        result = 1.0 / result ;
    }
    return result ;
}

int main ()
{
    cout << Power(3, 2) << endl ;
    cout << Power(2, -2) << endl ;
    return 0 ;
}
```