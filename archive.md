---
bg: "c-m-X_j3b4rqnlk-unsplash.jpg"
bg_credential: <a href="https://unsplash.com/@ubahnverleih?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">C M</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
layout: page
permalink: /posts/
title: "Archive"
crawlertitle: "All articles"
summary: "All articles in chronological order"
active: archive
---

<ul class="year">
  {% for post in site.posts %}
    {% if post.tags contains t %}
      <li>
        {% if post.lastmod %}
          <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
          <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
        {% else %}
          <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
          <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>
