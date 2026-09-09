---
title: Tuber Sale
description: Dahlia tuber sales — order online while supplies last.
---

<header class="page-header">
  <p class="eyebrow">Shop</p>
  <h1>Dahlia Tuber Sale</h1>
  <p class="lede">
    Every variety below was grown right here on our farm, and we've dug and divided them
    ourselves. Once a variety is gone for the season, it's gone — so if there's one you've
    had your eye on, don't wait too long to grab it.
  </p>
</header>

<section class="content">

  {% if site.data.store.checkout_live %}
    <div class="notice notice-live">
      <strong>We're open!</strong> Take a look below and add your favorites to your cart.
    </div>
  {% else %}
    <div class="notice">
      <strong>Still Growing:</strong> Our flowers are still in the ground, but once we have tubers to sell, 
      they will be here. — Check back soon, and follow along on Instagram for the exact day we open the doors.
    </div>
  {% endif %}

  <div class="notice notice-tip">
    <strong>A tip if there's a variety you really want:</strong> our stock counts update as
    orders come in, but a tuber only gets reserved once your order is actually placed — not
    while it's just sitting in your cart. If you're after something popular that might sell
    out fast, we'd suggest checking out with that one on its own (or in a small, quick order)
    rather than adding it to a big cart you'll fill in slowly — that way nothing slips away
    while you're still deciding on the rest.
  </div>

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

  <h2>A few things to know</h2>

  <p>
    We ship everything USPS Priority Mail, and we pick the box size to fit your order — a
    small order goes in a small box, and it scales up from there for bigger orders. Shipping
    is calculated automatically once you're in checkout, so you'll always see the real cost
    before you pay.
  </p>

  <p>
    Every box we send out includes tracking and $100 of insurance from USPS at no extra
    charge. If something arrives damaged, we want to make it right — just reach out within
    48 hours of delivery with a photo of what you received, and we'll get you a replacement
    or a refund.
  </p>

  <p>
