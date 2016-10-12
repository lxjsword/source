---
title: offerbook9
date: 2016-09-06 20:47:49
tags: 算法
---
### 剑指offer面试题9
<!-- more -->
``` bash
#include <iostream>
using namespace std ;
long long Fibonacci( unsigned int n )
{
  if ( n <= 0 )
    return 0 ;
  if ( n == 1 )
    return 1 ;
  return Fibonacci( n-1 ) + Fibonacci( n-2 ) ;
}
long long Fibonacci2( unsigned int n )
{
  int result[2] = { 0, 1 } ;
  if ( n < 2 )
    return result[n] ;
  long long fibNMinusOne = 1 ;
  long long fibNMinusTwo = 0 ;
  long long fibN = 0 ;
  for ( unsigned int i = 2; i <= n; ++i )
  {
    fibN = fibNMinusOne + fibNMinusTwo ;
    fibNMinusTwo = fibNMinusOne ;
    fibNMinusOne = fibN ;
  }
  return fibN ;
}
int main()
{
  cout << Fibonacci(10) << endl ;
  cout << Fibonacci2(10) << endl ;
  return 0 ;
}
```