---
title: offerbook6
date: 2016-09-06 20:47:34
tags: 算法
---
### 剑指offer面试题6
<!-- more -->
``` bash
#include <iostream>
#include <stack>
using namespace std ;
struct BinaryTreeNode
{
  int                 m_value ;
  BinaryTreeNode*     m_pLeft ;
  BinaryTreeNode*     m_pRight ;
};
typedef BinaryTreeNode BinaryTreeNode ;
BinaryTreeNode* ConstrutCore( int* startPreorder, int* endPreorder, 
                              int* startInorder, int* endInorder )
{
  if ( startInorder > endInorder || startPreorder > endPreorder )
    return NULL ;
  int rootVal = startPreorder[0] ;
  BinaryTreeNode* root = new BinaryTreeNode() ;
  root->m_value = rootVal ;
  root->m_pLeft = root->m_pRight = NULL ;
  
  int* findnode = startInorder ;
  while ( findnode != endInorder && *findnode != rootVal )
    ++findnode ;
  if ( findnode > endInorder )
    return NULL ;
  
  int leftLength = findnode - startInorder ;
  int* leftPreorderEnd = startPreorder + leftLength ;
  root->m_pLeft = ConstrutCore( startPreorder+1, startPreorder+leftLength, startInorder, findnode-1 ) ;
  root->m_pRight = ConstrutCore( leftPreorderEnd+1, endPreorder,findnode+1, endInorder ) ;
  return root ;
}
BinaryTreeNode* Construt( int* preorder, int* inorder, int length )
{
  if ( preorder == NULL || inorder == NULL || length <= 0 )
  {
    return NULL ; 
  } 
  return ConstrutCore( preorder, preorder+length-1, inorder, inorder+length-1 ) ;
}
void preorderTravel( BinaryTreeNode* node )
{
  if ( NULL == node ) 
    return ;
  cout << node->m_value << " " ;
  preorderTravel( node->m_pLeft ) ;
  preorderTravel( node->m_pRight ) ;
}
void inorderTravel( BinaryTreeNode* node )
{
  if ( NULL == node )
    return ;
  inorderTravel( node->m_pLeft ) ;
  cout << node->m_value << " " ;
  inorderTravel( node->m_pRight ) ;
}
void preorderTravel1( BinaryTreeNode* node ) 
{
  stack<BinaryTreeNode*> sNodes ;
  sNodes.push( node ) ;
  
  while ( !sNodes.empty() )
  {
    BinaryTreeNode* tmpNode = sNodes.top() ;
    cout << tmpNode->m_value << " " ;
    sNodes.pop() ;
    if ( tmpNode->m_pRight )
    {
      sNodes.push( tmpNode->m_pRight ) ;
    }
    if ( tmpNode->m_pLeft )
    {
      sNodes.push( tmpNode->m_pLeft ) ;
    }
  }
}
void inorderTravel1( BinaryTreeNode* node )
{
  stack<BinaryTreeNode*> sNodes ;
  BinaryTreeNode* curNode = node ;
  while ( curNode )
  {
    while ( curNode )
    {
      sNodes.push( curNode ) ;
      curNode = curNode->m_pLeft ;
    }
    BinaryTreeNode* tmpNode = sNodes.top() ;
    cout << tmpNode->m_value << " " ;
    sNodes.pop() ;
    if ( tmpNode->m_pRight )
    {
      curNode = tmpNode->m_pRight ;
    }
    else
    {
      while ( !tmpNode->m_pRight && !sNodes.empty() )
      {
        tmpNode = sNodes.top() ;
        cout << tmpNode->m_value << " " ;
        sNodes.pop() ;
      }
      curNode = tmpNode->m_pRight ;
    } 
  }
}
int main ()
{
  int preorder[] = { 1, 2, 4, 7, 3, 5, 6, 8 } ;
  int inorder[] = { 4, 7, 2, 1, 5, 3, 8, 6 } ;
  BinaryTreeNode* root = Construt( preorder, inorder, 8 ) ;
  preorderTravel1( root ) ;
  cout << endl ;
  inorderTravel1( root ) ;
  cout << endl ;
  return 0 ;
}
```