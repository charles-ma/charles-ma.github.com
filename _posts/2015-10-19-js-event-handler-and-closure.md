---
layout: post
title: "Js Event Handler and Closure"
description: "Some tips worth noting"
category: js  
tags: [js, closure, event-handling]
---
{% include JB/setup %}

###Question: 

Given an array of buttons, say <code>[b1, b2, b3, b4, b5]</code>, how can you bind actions to them so that once you click on any of the buttons, browser will popup with an alert message displaying the number of the clicked button? i.e when you click on <code>b2</code>, browser should say '2'.

####Initial thought:

Things seem to be pretty straight forward, you have an array of buttons, what you have to do is merely traverse them and bind them with corresponding methods, like the code below

<pre class='prettyprint lang-js'>
     function onLoad() {
         for (var i = 0; i < arr.length; i++) {
	     arr[i].onclick(function() {
                 alert(i);
	     });
	 }
     }	      
</pre>

But after you run the code, you will find that when you click on any of your buttons, the alert message will be identical, and always displaying <code>arr.length - 1</code> ... What is happening here?

####Solution:

The problem lies in the how js deal with closures. When you define another function within an existing one, the outer function's scope will be available for the inner one. When you change anything on the outer function's scope, it will be visible to the inner too because what the inner function has is merely a reference to the outer function's scope, not a copy... So every time <code>i</code> increment one, all the functions you try to register will see the change.

There are multiple ways to solve this issue, the simplest is to make a real copy of <code>i</code> in the call back function rather than maintaining a reference.

<pre class='prettyprint lang-js'>
    function onLoad() {
        for (var i = 0; i < arr.length; i++) {
	    arr[i].onclick(function() {
	        var j = i;
	        alert(j);
	    });
	}
    }
</pre>

This approach will make a copy of i locally in the call back function, thus different call-backs will have different versions of i. 

<script src="//google-code-prettify.googlecode.com/svn/loader/run_prettify.js"></script>