---
title: offerbook1
date: 2016-09-06 20:46:29
tags: 算法
---
### 剑指offer面试题1
<!-- more -->
``` bash
#include <iostream>
#include <string.h>
using namespace std ;
class CMyString
{
public:
  CMyString( char* pData = NULL ) ;
  CMyString( const CMyString& str ) ;
  ~CMyString() ;
  CMyString& operator=( const CMyString& str ) ;
private:
  char* m_pData ;
} ;
CMyString::CMyString( char* pData /*= NULL*/ ) 
{
  if ( NULL == pData )
  {
    m_pData = NULL ;
  }
  else
  {
    m_pData = new char[strlen(pData)+1] ;
    strcpy( m_pData, pData ) ;
  }
}
CMyString::CMyString( const CMyString& str )
{
  if ( NULL == str.m_pData )  
  {
    m_pData = NULL ;
  }
  else
  {
    m_pData = new char[strlen(str.m_pData)+1] ;
    strcpy( m_pData, str.m_pData ) ;
  }
}
CMyString::~CMyString() 
{
  if ( NULL != m_pData )
  {
    delete[] m_pData ;
    m_pData = NULL ;
  }
}
CMyString& CMyString::operator=( const CMyString& str )
{
  if ( this != &str)
  { 
    CMyString strTmp(str) ;
    char* pTmp = strTmp.m_pData ;
    strTmp.m_pData = m_pData ;
    m_pData = pTmp ;
  }
  return *this ;
}
/*
CMyString& CMyString::operator=( const CMyString& str)
{
  if ( this == &str )
  {
    return *this ;
  }  
  if ( NULL != m_pData )
  {
    delete[] m_pData ;
    m_pData = NULL ;
  }
  
  m_pData = new char[strlen(str.m_pData) + 1] ;
  strcpy( m_pData, str.m_pData ) ;
  
}
*/
int main ()
{
  CMyString str1("hello") ;
  CMyString str2("world") ;
  str1 = str2 ;
}
```