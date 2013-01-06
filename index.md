---
layout: page
title: Welcome to my Blog!
tagline: 
---
{% include JB/setup %}

## About the Author
    Charles Ma

    A student in the University of Pennsylvania. Majored in Computer Science.
    Having got his first master's degree last year and now working on his second.
    Intersted in Linux, Java, emacs, C, C++, Python and believing that writing code could be an art. 
    Also he has strong background in humanities. Born in China he has a deep understanding of Chinese traditional culture.
    Believing that economy is acting an important role to change the world, he is also interested in economy and trading...

    email: mcrichard.buaa@gmail.com
##About this Blog
	This blog is mainly about technology and some other related or unrelated interesting topics such as [ellen show](http://www.ellentv.com)...
## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

