---
layout: homepage
nav: blog
permalink: /blog/
---

## Blog

{% if site.posts.size > 0 %}
{% for post in site.posts %}
<div class="blog-entry">
  <span class="blog-date">{{ post.date | date: "%b %d, %Y" }}</span>
  &mdash;
  <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
</div>
{% endfor %}
{% else %}
<p>Coming soon.</p>
{% endif %}
