---
layout: page
title: Welcome to my Blog!
tagline: 
---
{% include JB/setup %}

## About the Author
Charles Ma

Software engineer
#js #html5 #css #Angularjs #nodejs #front end dev

email: mcrichard.buaa@gmail.com
## About this Blog
This blog is mainly about front end technology
## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

