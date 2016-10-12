---
title: OJ输入输出教训
date: 2016-09-06 09:11:42
tags: 经验教训
---
### OJ输入输出教训
#### 题目描述
描述
给予两个整数 a 和 b ，计算它们的和 a + b
输入
输入包含多组测试数据，每一行包含两个整数 a 和 b
输出
在一行中输出 a + b 的值
<!-- more -->
样例输入
``` bash
1 2
3 4
5 6
```
样例输出
``` bash
3
7
11
```
#### 正确解答
``` bash
#include  <iostream> 
using namespace std;
int main()
{
    int a, b;
    while(cin>> a >> b)
    cout << a + b << endl;
    return 0;
}
```
#### 错误解答
``` bash
#include  <iostream> 
using namespace std;
int main()
{
    int a, b;
    while(cin>> a >> b)
    cout << a + b;
    return 0;
}
```
#### 原因分析
在网上OJ的实现方式是将测试用例和结果都写入文件中， 将标准的输入输出重定向到文件中， 验证代码的正确性是对比输出文件， 这种实现方式比较
死板， 就要求必须严格的输入输出格式。
将测试用例写到文件data中， 输出到文件result或控制台，然后看一下上述两个例子的输出：
用命令：
``` bash
./iotest <data >result 或者 ./iotest <data
```
正确用例输出：
``` bash
3
7
11
```
错误用例输出：
``` bash
3711
```
由于我们自己测试的时候用控制台输入，下意识的输入的回车， 没有注意到问题，但OJ就是简单的对比输出结果是否符合预期。