---
layout: post
title: "ES6 Generator and Async"
description: "sync the syntax of async"
category: js
tags: [js, async]
---
{% include JB/setup %}


###ES6 Generator
Generator is a special type of function which allows to be stopped and resumed during execution. And this gives us a possibility to code async functionalities in a synced style.

Let's take a look at the syntax of the generator:

<pre class='prettyprint lang-js'>
	function* genFunc() {
		var i = 0;
		while(true) yield i++;
	}

	var gen = genFunc();
	gen.next().value; // 0
	gen.next().value; // 1
</pre>

What is amazing in this function is the 'infinite loop', in regular functions, if you put a while like this into it, you will end up with an infinite loop. But this is not true for generators. For the generator function <code>genFunc</code>, even i put an infinite while loop in it, i still have to call the <code>next()</code> function of the generator object to execute it step by step. This feature gives us the ability to stop and resume a code snippet.

The <code>next()</code> function call will cause the corresponding generator to be executed until it hits the yield statement. The expression after the yield key word will be evaluated, the value returned will become the return value of the <code>next()</code> call. The rest of the code will not be exected until you call <code>next()</code> again.

<script src="//google-code-prettify.googlecode.com/svn/loader/run_prettify.js"></script>
