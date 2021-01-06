---
layout: page
title: Blog Aprende Docker en Español
permalink: /Blog/
---

<div class="posts">
  {% for post in site.posts %}
    <article class="post">
      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>
        <div class="entry">
          {{ post.excerpt }}
        </div>
        <div class="date">
          Publicado el {{ post.date | date: "%d/%m/%Y" }}
        </div>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">LEER MÁS...</a>
    </article>
  {% endfor %}
</div>
