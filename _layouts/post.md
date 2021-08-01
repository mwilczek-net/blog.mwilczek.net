---
layout: default
---
<article class="post">

  <h1 class="post-title">{{ page.title }}</h1>

  <p class="post-meta">
    <time datetime="{{ page.date | date: "%Y-%m-%d" }}">{{ page.date | date: "%d-%m-%Y" }}</time>

    {% if page.author %}
      &nbsp;/&nbsp;
      <span>{{ page.author }}</span>
    {% endif %}
  </p>

  <div class="post-content">

    {{ content }}

    {% if page.references %}
      <div class="post-more">
        <h2>References</h2>

        {% for r in page.references %}
            <cite>
              {% if r[1] %}
                [{{ r[1].title }}]({{ r[0] }})
              {% else %}
                [{{ r[0] }}]({{ r[0] }})
              {% endif %}
            </cite><br>
        {% endfor %}
      </div>
    {% endif %}

    <div class="post-links">
      {% if page.next.url %}
        <a class="link-to-post" href="{{ page.next.url | relative_url}}">
          <span class="link-to-post__next">&#10535; &nbsp;Next post</span>
          <span class="link-to-post__title">{{ page.next.title }}</span>
        </a>
      {% endif %}

      {% if page.previous.url %}
        <a class="link-to-post" href="{{ page.previous.url | relative_url}}">
          <span class="link-to-post__prev">&#10535; &nbsp;Previous post</span>
          <span class="link-to-post__title">{{ page.previous.title }}</span>
        </a>
      {% endif %}
    </div>

  </div>

</article>