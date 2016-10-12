---
title: offerbook5
date: 2016-09-06 20:47:30
tags: 算法
---
### 剑指offer面试题5
<!-- more -->
``` bash
#include <iostream>
using namespace std ;
struct ListNode
{
  int           m_value ;
  ListNode*     m_next ;
} ;
typedef ListNode ListNode ;
void AddToTail( ListNode** pHead, int value )
{
  ListNode* pNew = new ListNode() ;
  pNew->m_value = value ;
  pNew->m_next = NULL ;
  if ( NULL == *pHead )
  {
    *pHead = pNew ;
  }
  else 
  {
    ListNode* pNode = *pHead ;
    while ( NULL != pNode->m_next )
    {
      pNode = pNode->m_next ;
    }
    pNode->m_next = pNew ;
  }
}
void RemoveNode( ListNode** pHead, int value ) 
{
  if ( pHead == NULL || *pHead == NULL )
    return ;
  ListNode* pToDeleted = NULL ;
  if ( (*pHead)->m_value == value )
  {
    pToDeleted = *pHead ;
    *pHead = (*pHead)->m_next ;
  }
  else
  {
    ListNode* pNode = *pHead ;
    while ( pNode->m_next != NULL && 
      pNode->m_next->m_value != value )
    {
      pNode = pNode->m_next ;
    }
    if ( pNode->m_next != NULL && 
        pNode->m_next->m_value == value )
    {
      pToDeleted = pNode->m_next ;
      pNode->m_next = pNode->m_next->m_next ;
    }
  }
  if ( pToDeleted != NULL )
  {
    delete pToDeleted ;
    pToDeleted = NULL ;
  }
}

#include <stack>
#include "listnode.hpp"
void PrintListReversingly_Iteratively( ListNode* pHead )
{
  std::stack<ListNode*> nodes; 
  ListNode* pNode = pHead ;
  while ( NULL != pNode )
  {
    nodes.push( pNode ) ;
    pNode = pNode->m_next ;
  }
  while ( !nodes.empty() )
  {
    pNode = nodes.top() ;
    cout << pNode->m_value << endl ;
    nodes.pop() ;
  }
}
void PrintListReversingly_Recursively( ListNode* pHead ) 
{
  if ( pHead != NULL )
  {
    if ( pHead->m_next != NULL )
    {
      PrintListReversingly_Recursively( pHead->m_next ) ;
    }
    cout << pHead->m_value << endl ;
  }
}
int main()
{
  ListNode* listHead = NULL ; 
  AddToTail( &listHead, 1 ) ;
  AddToTail( &listHead, 2 ) ;
  AddToTail( &listHead, 3 ) ;
  AddToTail( &listHead, 4 ) ;
  AddToTail( &listHead, 5 ) ;
  PrintListReversingly_Iteratively( listHead ) ;
  PrintListReversingly_Recursively( listHead ) ;
  return 0 ;
}

```