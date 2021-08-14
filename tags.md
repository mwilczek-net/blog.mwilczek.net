---
bg: "jan-antonin-kolar-lRoX0shwjUQ-unsplash.jpg"
bg_credential: <a href="https://unsplash.com/@jankolar?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Jan Antonin Kolar</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
layout: page
permalink: /tags/
title: "Tags"
crawlertitle: "All articles"
summary: "Posts grouped by tags"
active: tags
---

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <h2 class="category-key" id="{{ t | downcase }}">{{ t }}</h2>

  <ul class="year">
    {% for post in posts %}
      {% if post.tags contains t %}
        <li>
          <a href="{{ post.url | relative_url }}">
            {{ forloop.index }}: {{ post.title }}
          </a>
          {% if post.lastmod %}
            <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
          {% else %}
            <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
          {% endif %}
        </li>
      {% endif %}
    {% endfor %}
  </ul>

{% endfor %}
