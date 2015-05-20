---
layout: post
title: Đa hình C++
---

````cpp
#include <conio.h>
#include <stdio.h>
#include <iostream>
#include <string.h>

using namespace std;
 
class A {
public:
   virtual void Hello() {
     cout<<"\nHello A";
   }
};
 
class B: public A {
public:
    void Hello()
   {
     cout<<"\nHello B";
   }
};
 
class C: public A {
public:
    void Hello() {
     cout<<"\nHello C";
   }
};
 

int main() {
    A a;
    A *pa= new A;
    pa->Hello(); // Hello A
    
    B b;
    pa=&b;
    pa->Hello(); // Hello B
    
    C c;
    pa=&c;
    pa->Hello(); // Hello C
    return 0;
}
````
