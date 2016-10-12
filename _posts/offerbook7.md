---
title: offerbook7
date: 2016-09-06 20:47:40
tags: 算法
---
### 剑指offer面试题7
<!-- more -->
``` bash

#include <iostream>
#include <stack>
using namespace std ;
template<typename T>
class CQueue
{
public:
  void appendTail( const T& node ) ;
  T deleteHead() ;
private:
  stack<T> stack1 ;
  stack<T> stack2 ;
};
template<typename T>
void CQueue<T>::appendTail( const T& node ) 
{
  stack1.push( node ) ;
}
template<typename T>
T CQueue<T>::deleteHead()
{
  if ( stack2.empty() )
  {
    while ( !stack1.empty() )
    {
      T tmp = stack1.top() ;
      stack1.pop() ;
      stack2.push( tmp ) ;
    }
  }
  T ret = stack2.top() ;
  stack2.pop() ;
  return ret ;
}
int main()
{
  CQueue<int> myqueue ;
  myqueue.appendTail( 1 ) ;  
  myqueue.appendTail( 2 ) ;  
  myqueue.appendTail( 3 ) ;  
  cout << myqueue.deleteHead( ) ;  
  myqueue.appendTail( 4 ) ;  
  cout << myqueue.deleteHead( ) ;  
  cout << myqueue.deleteHead( ) << endl ;  
  return 0 ;
}

```