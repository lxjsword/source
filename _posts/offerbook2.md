---
title: offerbook2
date: 2016-09-06 20:47:07
tags: 算法
---
### 剑指offer面试题2
<!-- more -->
``` bash

/*
 * t2.cpp
 *
 *  Created on: 2016年8月28日
 *      Author: lxj
 */
#include <iostream>
using namespace std ;
class Singleton
{
private:
    Singleton()
    {
        cout << "Singleton construct!" << endl ;
    }
    Singleton(const Singleton&)
    {
        cout << "Singleton copy construct!" << endl ;
    }
    Singleton& operator=(const Singleton&)
    {
        cout << "Singleton assign construct!" << endl ;
    }
public:
    static Singleton* getInstance()
    {
        return instance ;
    }
private:
    static Singleton* instance ;
} ;
Singleton* Singleton::instance = new Singleton() ;
int main ()
{
    Singleton* singleton1 = Singleton::getInstance() ;
    Singleton* singleton2 = Singleton::getInstance() ;
    return 0 ;
}

```