---
layout: page
title: Arduino Classes
excerpt: "Here is a list of the arduino classes we offer."
search_omit: true
---

### Arduino With Blocks
<ul class="post-list">
{% assign blockly_posts = site.categories.arduino_block | sort: "sort_order" %}

{% for post in blockly_posts   %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>


### Arduino C Programming
<ul class="post-list">
{% assign blockly_posts = site.categories.arduino | sort: "sort_order" %}

{% for post in blockly_posts   %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>