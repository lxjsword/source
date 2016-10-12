---
title: offerbook12
date: 2016-09-06 20:48:04
tags: 算法
---
### 剑指offer面试题12
<!-- more -->
``` bash
#include <iostream>
#include <string.h>
using namespace std ;

bool Increment(char* number)
{
    bool isOverflow = false ;
    int nTakeOver = 0 ;
    int nLength = strlen(number) ;

    for (int i = nLength-1; i >= 0; --i)
    {
        int nSum = number[i] - '0' + nTakeOver ;
        if (i == nLength-1)
            ++nSum ;
        if (nSum >= 10)
        {
            if (i == 0)
                isOverflow = true ;
            else
            {
                nTakeOver = 1;
                nSum -= 10 ;
                number[i] = '0' + nSum ;
            }
        }
        else
        {
            number[i] = '0' + nSum ;
            break ;
        }
    }
    return isOverflow ;
}

void PrintNumber(char* number)
{
    if (NULL == number)
        return ;
    int nLength = strlen(number) ;
    int i = 0;
    while ((number[i] - '0' == 0) && 
            (i < nLength)) 
        ++i ;
    while (i < nLength)
        cout << number[i++] ;
    cout << endl ;
}

void PrintToMaxNDigits(int n)
{
    if (n <= 0)
        return ;
    char* number = new char[n+1] ;
    memset(number, '0', n) ;
    number[n] = '\0' ;

    while (!Increment(number))
    {
        PrintNumber(number) ;
    }

    delete[] number ;
}

void PrintNumber2(char* number, int n)
{
    
    int num = strlen(number) ;
    for (int i = 0; i <= 9; ++i)
    {
        number[num-n] = i + '0';
        if (1 == n)
            PrintNumber(number) ;
        else
            PrintNumber2(number, n-1) ;
    }

}

void PrintToMaxNDigits2(int n)
{
    if (n <= 0)
        return ;
    char* number = new char[n+1] ;
    memset(number, '0', n) ;
    number[n] = '\0' ;

    PrintNumber2(number, n) ;
}

int main()
{
    PrintToMaxNDigits2(3) ;
    return 0 ;
}
```