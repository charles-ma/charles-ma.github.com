---
layout: post
title: "Sum All Numbers in a Range"
description: "A simple algorithm question"
category: js
tags: [alg, js]
---
{% include JB/setup %}

This is a pretty simple algorithm question, what is more important is the solution evolving.

##Question
You are given an array of two different integers, your function should return sum of those two integers and all the intergers between them, e.g func([1, 4]) should return 10. And in the given array, smaller number does not always come first.

###Solution 1
<b>Basic thought</b>: we already know the two numbers, in order to sum all the numbers between them, we have to know other numbers in the range. In order to do that, we have to figure out the larger and smaller number of the two. It is easy to do:

<pre class='prettyprint lang-js'>
     var larger = Math.max(arr[0], arr[1]);
     var smaller = Math.max(arr[0], arr[1]);
     var newArr = new Array();
     for(var i = smaller; i <= larger; i++) newArr[i] = i;
</pre>

Now that we have all the integers we need, it is easy to sum them up

<pre class='prettyprint lang-js'>
     newArr.reduce(function(pre, curr) {
         return pre + curr;    				 
     });
</pre>

Note we are using the <code>Array.prototype.reduce()</code> method, which is pretty convenient and you don't have to write your own loop.

Merge the two pieces together and do some small tinker, we have our first solution ready:

<pre class='prettyprint lang-js'>
     var newArr = new Array();
     for (var = Math.min(arr[0], arr[1]); i <= Math.max(arr[0], arr[1]); i++) newArr[i] = i;
     return newArr.reduce(function(pre, curr) {return pre + curr});
</pre>

But is this ideal? Obviously not. We are using one loop to populate the new array, and another one to sum them up, which is a waste of resource. We should tinker it more. Can we do it in one loop? Definitely yes.

###Solution 2
<b>Basic thought</b>: we can do sum directly without doing populating.

<pre class='prettyprint lang-js'>
     var sum = 0;
     for (var i = Math.min(arr[0], arr[1]); i <= Math.max(arr[0], arr[1]); i++) sum += i;
     return sum;
</pre>

We don't have to populate the newArr up! This will save us some cpu time and memory too. The problem is: whether we can make this code even more efficient? The answer is yes.

###Solution 3
<b>Basic thought</b>: now that we already have the two numbers, why we have to know which one is larger? Can we do this without a loop? The answer again, is yes.

<pre class='prettyprint lang-js'>
     return (arr[0] + arr[1]) * (Math.abs(arr[0] - arr[1]) + 1) / 2;
</pre>

In this solution, we only call <code>Math.abs()</code> which is a very simple function and all the others are simply arithmetic ops! So when you are coding, don't think you are coding, in the first place, you are trying to solve a problem. So come up with a mathematical solution, then convert it to real code. If you do it that way, you will come up with the third solution first.