---
title: offerbook4
date: 2016-09-06 20:47:25
tags: 算法
---
### 剑指offer面试题4
<!-- more -->
``` bash
#include <iostream>
#include <string.h>
using namespace std ;
void ReplaceBland( char str[], int length )
{
  if ( NULL == str && length <= 0 )
    return ;
  int orilength = 0 ;
  int numberOfBlank = 0 ;
  int i = 0 ;
  while ( str[i] != '\0')
  {
    ++orilength ;
    if ( ' ' ==  str[i] )
      ++numberOfBlank ;
    ++i ;
  }
  int newlength = orilength + numberOfBlank*2 ;
  if ( newlength > length )
    return ;
  
  int indexofori = orilength ;
  int indexofnew = newlength ;
  while ( indexofori >= 0 && indexofnew > indexofori )
  {
    if ( ' ' == str[indexofori] )
    {
      str[indexofnew--] = '0' ;
      str[indexofnew--] = '2' ;
      str[indexofnew--] = '%' ;
    }
    else
    {
      str[indexofnew--] = str[indexofori];
    }
    --indexofori ;
  }
}
int main()
{
  char str[100] ;
  memset( str, 0, 100 ) ;
  const char* oriStr = "We are Happy." ;
  strcpy( str, oriStr ) ;
  cout << str << endl ;
  ReplaceBland( str, 100 ) ;
  cout << str << endl ;
  char str1[] = "hello" ;
  cout << sizeof(str1) << endl ;
  cout << strlen(str1) << endl ;
  return 0 ;
}


```