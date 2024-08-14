---
layout: default
---

# Nosebook

This is my informal web-based notebook with writing, links, tutorials, ideas, and lists. These are not meant to be formal articles or academic writing but instead a blog-like place to share ideas, collect thoughts and to cast speculative ideas. There is also a [wiki]({% link wiki/index.md %}).

<ul>
  {% for post in site.posts %}
  <li>
    <p>
      <a href="{{ site.baseurl }}{{ post.url }}">
     {{ post.title }}
     </a>
    </p>
      <em>
	{{ post.date | date: "%Y %b %d" }}
      </em>
      </li>
  {% endfor %}
</ul>

<em>Feel free to write me with any responses or share links to your own writing or projects online.</em>
