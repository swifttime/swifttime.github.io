---
layout: page
title: About
permalink: /about/
---

This is a blog about [the Swift language from Apple](http://developer.apple.com/swift). 

Members:
<ul>
{% for member in site.data.members %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>
