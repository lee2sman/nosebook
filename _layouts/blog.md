---
layout: default
title: Posts
---

  {% for post in site.posts %}
  
    <article role="article">
      <h2><a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }}
      </a></h2>
      <p>{{ post.summary }}</p>
        <p>    <time class="date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%-d %B %Y" }}</time> </p>
  
    </article>
    
    
  {% endfor %}


