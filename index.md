---
layout: page
title: C.M. @ js
tagline: 
---
{% include JB/setup %}

## About the Author

<span class='red'>C</span>.M.

Software Engineer <a href='mailto:mcrichard.buaa@gmail.com'><i class='fa fa-send'></i></a> <a href='//github.com/charles-ma'><i class='fa fa-github'></i></a> <a href='//twitter.com/intent/user?screen_name=CharlesRMa'><i class='fa fa-twitter'></i></a>
<br>#js #html5 #css #Angularjs #nodejs #front end dev

## About this Blog

Js related notes

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

