---
layout: post
title: "Js Equality"
description: "Tips related to js equality"
category: js
tags: [js]
---
{% include JB/setup %}

1. js equality can be tested using <code>==</code> and <code>===</code>

2. <code>==</code> compares two values after necessary conversions. e.g

<pre class='prettyprint lang-js'>
	var a = '1', b = 1;
	console.log(a === b); 	// false, a is a string while b is a number
	console.log(a == b); 	// true
</pre>

3. js equality tests primitive value based on their values while tests objects based on their references. e.g

<pre class='prettyprint lang-js'>
	var a = [], b = c = [];
	console.log(a == b);	// false
	console.log(a === b); 	// false
	console.log(b == c);	// true
	console.log(b === c);	// true
</pre>

<code>b</code> and <code>c</code> are equal because they are referencing a same memory location, while <code>a</code> is referencing another memory location, although objects stored in the two locations are the same.

<script src="//google-code-prettify.googlecode.com/svn/loader/run_prettify.js"></script>