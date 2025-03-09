---
layout: default
---

# Nosebook

This is my informal web-based notebook with writing, links, tutorials, ideas, and lists. These are not meant to be formal articles or academic writing but instead a blog-like place to share ideas, collect thoughts and to cast speculative ideas. 

*Update 2024-01-06: I've added a [log](log) page for ongoing notes that aren't full blogposts.*

<ul>
  {% for post in site.posts %}
  <li style="list-style:none;">
    <p>
      <a href="{{ site.baseurl }}{{ post.url }}">
     {{ post.title }}
     </a>
     <br>
    <em style="font-size:small;">
	{{ post.date | date: "%Y %b %d" }}
      </em>
      </p>
      </li>
  {% endfor %}
</ul>

<em>Feel free to write me with any responses or share links to your own writing or projects online.</em>
