---
title: Tuber Sale
description: Dahlia tuber sales — order online while supplies last.
---

<header class="page-header">
  <p class="eyebrow">Shop</p>
  <h1>Dahlia Tuber Sale</h1>
  <p class="lede">
    Order dahlia tubers online below. Quantities are limited per variety, and once
    a variety sells out it's marked sold out automatically.
  </p>
</header>

<section class="content">

  {% if site.data.store.checkout_live %}
    <div class="notice notice-live">
      <strong>Sale is live!</strong> Add tubers to your cart below to check out.
    </div>
  {% else %}
    <div class="notice">
      <strong>Coming soon:</strong> Dahlia tuber sales will be listed seasonally. Availability will be limited.
    </div>
  {% endif %}

  {% assign all_tubers = site.tubers %}
  {% if all_tubers.size == 0 %}
    <p>No tuber varieties have been added yet.</p>
  {% endif %}

  {% assign grouped = all_tubers | group_by: "type" | sort: "name" %}
  {% for group in grouped %}
    <h3 class="tuber-type-heading">{{ group.name | default: "Other" }}</h3>

    <div class="tuber-grid">
      {% assign sorted_items = group.items | sort: "title" %}
      {% for tuber in sorted_items %}
        {% assign sold_out = false %}
        {% if tuber.available == false or tuber.quantity == 0 %}
          {% assign sold_out = true %}
        {% endif %}

        <div class="tuber-card{% if sold_out %} sold-out{% endif %}">
          <figure>
            {% if sold_out %}<span class="badge">Sold out</span>{% endif %}
            {% if tuber.image %}
              <img src="{{ tuber.image | relative_url }}" alt="{{ tuber.title }} dahlia bloom">
            {% endif %}
          </figure>

          <h4>{{ tuber.title }}</h4>

          <p class="qty">
            {% if sold_out %}
              0 available
            {% else %}
              {{ tuber.quantity }} available
            {% endif %}
          </p>

          {% if tuber.price %}
            <p class="price">${{ tuber.price }}</p>
          {% endif %}

          {% if tuber.description %}
            <p class="desc">{{ tuber.description }}</p>
          {% endif %}

          {% if sold_out %}
            <button disabled>Sold out</button>
          {% elsif site.data.store.checkout_live %}
            <button
              class="snipcart-add-item"
              data-item-id="{{ tuber.slug }}"
              data-item-name="{{ tuber.title }} Dahlia Tuber"
              data-item-price="{{ tuber.price }}"
              data-item-url="{{ page.url | absolute_url }}"
              data-item-image="{{ tuber.image | absolute_url }}">
              Add to cart
            </button>
          {% else %}
            <button disabled>Not yet on sale</button>
          {% endif %}
        </div>
      {% endfor %}
    </div>
  {% endfor %}

  <h2>Sales notes</h2>
  <ul>
    <li>
      Shipping: all tuber orders ship USPS Priority Mail Flat Rate, and the shipping cost is
      calculated automatically at checkout based on how many tubers you order. Orders of 1–5
      tubers ship in a Small box, 6–12 in a Medium box, and 13–24 in a Large box. Larger orders
      combine boxes — for example, 25 tubers ships as one Large box plus one Small box, 40 tubers
      as two Large boxes, and so on.
    </li>
    <li>Add local pickup details if available.</li>
    <li>Add refund/replacement policy for tubers.</li>
    <li>Add growing/storage disclaimer.</li>
  </ul>
</section>
