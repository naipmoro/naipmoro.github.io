---
title: Exercises in Boundary Formalism
layout: default
excerpt_separator: <!--more-->
---
A series of posts exploring George Spencer-Brown's _Laws of Form_ and
related boundary systems.

<h2>Posts</h2>
<ul>
{% for post in site.posts %}
  <li><a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
   {{ post.excerpt }}</li>
{% endfor %}
</ul>

