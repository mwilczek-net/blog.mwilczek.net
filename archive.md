---
bg: "c-m-X_j3b4rqnlk-unsplash.jpg"
bg_credential: <a href="https://unsplash.com/@ubahnverleih?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">C M</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
layout: page
permalink: /archive/
title: "Archive"
crawlertitle: "All articles"
summary: "All articles in chronological order"
active: archive
---

<ul class="year">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">
        {{ site.posts | size | minus: forloop.index | plus: 1 }}: {{ post.title }}
      </a>
      {% if post.lastmod %}
        <span class="date">{{ post.lastmod | date: "%Y-%m-%d" }}</span>
      {% else %}
        <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span>
      {% endif %}
      <p class="post-meta">
        {% for tag in post.tags %}
          <a href="{{ site.baseurl }}/tags/#{{ tag | downcase }}">#{{ tag }}</a>&nbsp;
        {% endfor %}
      </p>
    </li>
  {% endfor %}
</ul>
