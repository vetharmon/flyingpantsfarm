---
title: Welcome
description: Welcome to Flying Pants Flower Farm.
---

<section class="hero">
  <div class="hero-inner">
    <p class="eyebrow">Specialty dahlias & seasonal flowers</p>
    <h1>Flying Pants Flower Farm</h1>
    <p class="lede">
      A small flower farm growing dahlias, sunflowers, seasonal bouquets, and a little bit of joy.
    </p>
    <div class="button-row">
      <a class="button" href="/gallery/">View the Flowers</a>
      <a class="button secondary" href="/sales/">Shop Tubers</a>
    </div>
  </div>
</section>

<section class="section">
  <div class="grid two">
    <div>
      <p class="eyebrow">Find us</p>
      <h2>Fresh flowers, farm updates, and seasonal availability.</h2>
      <p>
        Follow along for bloom updates, farm stand hours, tuber sales, bouquet availability, and behind-the-scenes garden notes.
      </p>
    </div>
    <div class="card">
      <h3>Contact</h3>
      <p><strong>Email:</strong> <a href="mailto:hello@flyingpants.farm">hello@flyingpants.farm</a></p>
      <p><strong>Instagram:</strong> <a href="https://instagram.com/YOUR_INSTAGRAM">@YOUR_INSTAGRAM</a></p>
      <p><strong>Location:</strong> Add your town/region here</p>
    </div>
  </div>
</section>

<section class="section alt">
  <p class="eyebrow">Seasonal notes</p>
  <h2>Current updates</h2>
  <div class="grid three">
    {% for post in site.posts limit:3 %}
      <article class="card">
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt | strip_html | truncate: 130 }}</p>
      </article>
    {% endfor %}
  </div>
</section>
