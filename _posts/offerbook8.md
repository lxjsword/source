---
title: offerbook8
date: 2016-09-06 20:47:44
tags: 算法
---
### 剑指offer面试题8
<!-- more -->
``` bash
#include <iostream>
#include <stdlib.h>
#include <time.h>
#include <exception>
using namespace std ;
void Swap( int& a, int& b )
{
    int tmp = a ;
    a = b ;
    b = tmp ;
}
int RandomInRange( int start, int end )
{
    return rand() % (end-start+1) + start ;
}
int Partion2( int data[], int length, int start, int end )
{
    if ( NULL == data || 0 >= length || start < 0 || end >= length )
        throw new exception() ;
    int tmp = data[end] ;
    int low = start ;
    int high = end ;
    while ( low < high )
    {
        while ( data[low] < tmp && low < high )
        {
            ++low ;
        }    
        if ( low < high )
            data[high--] = data[low] ;
        while ( data[high] > tmp && low < high )
        {
            --high;
        }
        if ( low < high )
            data[low++] = data[high] ;
    }
    data[low] = tmp ;
    return low ;
}
int Partion( int data[], int length, int start, int end )
{
    if ( NULL == data || 0 >= length || start < 0 || end >= length )
        throw new exception() ;
    int index = RandomInRange( start, end ) ;
    Swap( data[index], data[end] ) ;
    int small = start - 1 ;
    for ( index = start; index < end; ++index )
    {
        if ( data[index] < data[end] )
        {
            ++small ;
            if ( small != index )
            {
                Swap( data[small], data[index] ) ;
            }
        }
        
    }
    ++small ;
    Swap( data[small], data[end] ) ;
    return small ;
}
void QuickSort( int data[], int length, int start, int end )
{
    if ( start == end )
        return ;
    int index = Partion2( data, length, start, end ) ;
    if ( index > start )
    {
        QuickSort( data, length, start, index-1 ) ;
    }
    if ( index < end )
    {
        QuickSort( data, length, index+1, end ) ;
    }
}
int main() 
{
    srand( (unsigned)time( NULL ) );
    int data[] = { 5, 4, 3, 2, 1 } ;
    int i = 0; 
    for ( i = 0; i < 5; ++i )
        cout << data[i] << " " ;
    cout << endl ;
    QuickSort( data, 5, 0, 4 ) ;   
    for ( i = 0; i < 5; ++i )
        cout << data[i] << " " ;
    cout << endl ;
    return 0 ;
}

```