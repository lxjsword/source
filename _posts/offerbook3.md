---
title: offerbook3
date: 2016-09-06 20:47:12
tags: 算法
---
### 剑指offer面试题3
<!-- more -->
``` bash
#include <iostream>
using namespace std ;
bool find ( int* matrix, int rows, int columns, int number ) 
{
  bool found = false ;
  if ( NULL != matrix && rows > 0 && columns > 0 )
  {
    int row = 0 ;
    int column = columns - 1 ;
    while ( row < rows && column >= 0 )
    {
      if ( matrix[row*columns+column] == number )
      {
        found = true ; 
        break ;
      }
      else if ( matrix[row*columns+column] > number )
      {
        --column ;
      }
      else 
      {
        ++row ;
      }
    }
  }
  return found ;
}
int main ()
{
  int rows, columns ;
  cin >> rows >> columns ;
  int* matrix = new int[rows*columns] ;
  int i = 0 ;
  
  for ( i = 0; i < rows*columns; ++i )
  {
    cin >> matrix[i] ;
  }
  int number = 0;
  cin >> number ;
  cout << find( matrix, rows, columns, number ) << endl ;
  delete[] matrix ;
  return 0 ;
}

```