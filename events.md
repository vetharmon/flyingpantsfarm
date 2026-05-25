---
title: Current Events
description: Current events and seasonal updates from Flying Pants Flower Farm.
---

<header class="page-header">
  <p class="eyebrow">What’s happening</p>
  <h1>Current Events</h1>
  <p class="lede">
    Bloom updates, market dates, tuber sale announcements, farm stand news, and seasonal notes.
  </p>
</header>

<section class="section">
  <div class="grid two">
    {% for post in site.posts %}
      <article class="card">
        <p class="eyebrow">{{ post.date | date: "%B %-d, %Y" }}</p>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
        <a href="{{ post.url }}">Read more</a>
      </article>
    {% endfor %}
  </div>
</section>
