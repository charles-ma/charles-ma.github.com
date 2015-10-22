---
layout: post
title: "Js Prototype and __proto__"
description: "Difference btw prototype and __proto__"
category: js
tags: [js, inheritance]
---
{% include JB/setup %}

###The magic <code>new</code> keyword
The <code>new</code> keyword should be very familiar to you. Basically, if you are using it with a function, you can get a newly created object having similar properties as the constructor itself. Let's inspect what exactly is happening using some sample code:

<pre class='prettyprint lang-js'>
	function F () {};   // define a new function
	F[1] = 's';	    // give the constructor a new property
	var a = new F();    // create a new object using the construcor
</pre>

Basically, this piece of code defines a constructor function and creates a new object using the it.

A commonly misunderstanding for beginners is that <code>a</code> should have the property inherited from <code>F</code> because it is a new F anyway. While that is not the truth. Because js doesn't have the concept of class (no until ES6, while in ES6, the class is merely a syntax sugar so it won't affect our discussion here), F is only another object which is in the same inheritance level of a, they can be viewed as siblings! And sure you don't want a sibling to inherit anything from other siblings. 

What js really does here is:

<pre>
	1. Create a new object
	2. Set the <code>[[prototype]]</code> of the object to <code>F.prototype</code>
	3. Call the constructor on the newly created object with <code>this</code> set to the object reference
	4. Return newly created object to the context
</pre>

<code>[[prototype]]</code> is the real prototype js use in the prototype chain, it can also be accessed using <code>__proto__</code> which is merely a getter and setter for <code>[[prototype]]</code> or <code>Object.getPrototypeOf(); Object.setPrototypeOf(); // for ES6 </code>. 

What is not intuitive for beginners is that <code>F.prototype</code> and <code>F.__proto__</code> are not necessarily the same, meaning that object created by calling <code>new F()</code> doesn't necessarily have the same prototype as <code>F</code>. You are free to do something like:

<pre class='prettyprint lang-js'>
	var p = {};        // create a new object
	p[1] = 1;          // give it a property '1', value is 1
	F.prototype = p;   // make F.prototype == p
	a = new F();
	console.log(a.__proto__) // {'1': 1} will be printed out, indicating a is inheriting from p rather than F
	var b = new F();
	console.log(b.__proto__) // will get the same output
</pre>

And the magic is, when you change the property of p, it will be reflected on a and b!

<pre class='prettyprint lang-js'>
	p[1] = 2;
	console.log(a[1]);
	console.log(b[1]);    // you will get 2 in the console for both a and b!
</pre>

It means both <code>a</code> and <code>b</code> has a reference to the same <code>p</code>! But if you change <code>a[1]</code> or <code>b[1]</code>, it won't affect their prototype value.

In conclusion, to use js fluently, knowing the difference btw <code>prototype</code> and <code>__proto__</code> is crucial.

<script src="//google-code-prettify.googlecode.com/svn/loader/run_prettify.js"></script>