---
title: Thinking in Java 第四章
date: 2019-07-16 22:15:20
tags:
categories: Java
---
# 第4章 控制执行流程
if-else while do-while for return break
## 4.1 ture 和 flase
关系操作符构造的条件语句如“==”的返回值是true和false，**Java中不允许将一个数字作为布尔值使用。**

## 4.2 if-else
if else语句与其它语言的相同，其中else是可选的。

## 4.3 迭代
 while、do-while、for用来控制循环，有时候将他们称为迭代语句。语句会重复执行，直到起控制作用的布尔值得到“假”的结果时停止。

#### 4.3.1 do-while
do-while 至少会执行一次。while 更常用一些。
#### 4.3.2 for
最常用的 迭代形式。适合计数。（练习4 最棒）
#### 4.3.3 逗号操作符
可以在 for 语句定义多个变量。其他迭代不适用。无论是初始化 还是步进部分 语句都是顺序执行。
## 4.4 foreach
更加简洁的for语法 用于数组和容器。
```
// f是要被访问的循环体 i是一个变量
for(int x:f){
    System.out.pringln(x);
}

```
顺带讲解了一下**重载：相同方法可以具有不同参数** 。<br>
range() 配上 foreach 效率低 可读性高。<br>
printnb（）方法不会换行。<br>
foreach 更加易读。

## 4.5 return
 return关键字有两个用途，一方面指定一个void方法返回什么值，另一方面它会强制结束当前void方法，并返回那个值。

## 4.6 break 和 continue
break用于强制退出循环，不执行循环剩余的语句<br>
continue是停止当前的迭代，退到循环开始执行下一次迭代

## 4.7 臭名昭著的goto
goto 起源于汇编。Java编译器会生成自己的“汇编代码”，但是是运行在Java虚拟机上的。而不是直接运行在cpu硬件上。它是在源码级上的跳转。 导致可读性差，Java 没有goto。
Java 有 标签 可以 替换goto 使用。

## 4.8 switch
switch也被划为一种选择语句，根据整数表达式的值，从一系列语句中选择一组执行。

## 4.9 总结
介绍了大多数编程语言都具有基本特性：运算 操作符 优先级 类型转换以及选择和循环等等。

