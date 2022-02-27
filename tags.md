---
bg: "jan-antonin-kolar-lRoX0shwjUQ-unsplash.jpg"
bg_credential: <a href="https://unsplash.com/@jankolar?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Jan Antonin Kolar</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>
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

  <h2 class="category-key" id="{{ t | downcase }}">
    <a href="{{ site.baseurl }}/tags/#{{ t | downcase }}">
      #{{ t }}
    </a>
  </h2>

  <ul class="year">
    {% for post in posts %}
      {% if post.tags contains t %}
        <li>
          <a href="{{ post.url | relative_url }}">
            {{ forloop.index }}: {{ post.title }}
          </a>
          {% if post.lastmod %}
            <span class="date">{{ post.lastmod | date: "%Y-%m-%d"  }}</span>
          {% else %}
            <span class="date">{{ post.date | date: "%Y-%m-%d"  }}</span>
          {% endif %}
          <p class="post-meta">
            {% for tag in post.tags %}
              <a href="{{ site.baseurl }}/tags/#{{ tag | downcase }}">#{{ tag }}</a>&nbsp;
            {% endfor %}
          </p>
        </li>
      {% endif %}
    {% endfor %}
  </ul>

{% endfor %}
