---
layout: page
title: Index
share: false
permalink: /posts/
description: Notes of Nam Khanh Tran
---

A list of posts that aim to document what I've learned so far about ML, data science, devops and so on.

<ul>
  {% for post in site.posts %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
