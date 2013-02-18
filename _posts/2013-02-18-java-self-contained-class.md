---
layout: post
title: "java self contained class"
description: "some hints about self contained class in java"
category: technology
tags: [tech]
---
{% include JB/setup %}

As we know, a class in Java can contain fields of its own type. For example, a class A can contain a field of type A. But in this case, something tricky might happen when you are initializing your class.
If you define your class like this:

   class A {
   	 private A a = new A();
	 public A() {
	 	
	 }
   }
   
then something wrong will happen during run time when you want to initialize A. Why this happened? Let's analyze the code.
When you are trying to initialize A, you actually initialize the field a in class A first, and at this time, you will automatically call the constructor of A to initialize a, but the problem is during the process of initializing a, the virtual machine has to initialize the field a of the new instance again. Then this circle will go on forever... Then how to solve this problem? Here's one possible way:
     
     class A {
     	   static A a = new A();
	   public A() {

	   }
     }

In this code, the field a is declared as static so there will be only one copy of a during the whole life circle of the program. When you are trying to initialize A, it first initilize the static variable a and set it to a new instance, and the field a in this new instance is actually the same as the static variable a, so it is possible for you to write something like this:

   A a = new A();
   System.out.println(a.a.a.a.a.a.a.a == A.a);

the printed result will be true. And you can write as many a's as possible on the left hand side of the equation. This is because every instance of A contain a field a and this field is self contained.