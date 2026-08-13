---
layout: page
title: Company Profiles
description: Detailed profiles of website design, web development, e-commerce, SEO and digital marketing companies serving Uganda, with verified listing badges where a company has claimed its profile.
permalink: /companies/
---
# Company Profiles

Profiles below are based on publicly available information — each company's official website and other verifiable public sources. Listings record what the company offers, where it is based, and the date it was last reviewed.

Verified listings carry a **Verified** badge, meaning the company has confirmed its own information.

{% assign profiles = site.pages | where_exp: "p", "p.path contains 'companies/'" | where_exp: "p", "p.name != 'index.md'" | sort: "title" %}
<div class="card-grid company-grid">
  {% for p in profiles %}
  <a class="card" href="{{ p.url | relative_url }}">
    <h3>{{ p.title }}
      {% if p.status == 'verified' %}<span class="mini-badge mini-badge--verified">Verified</span>{% elsif p.status == 'claimed' %}<span class="mini-badge mini-badge--claimed">Claimed</span>{% else %}<span class="mini-badge mini-badge--unclaimed">Unclaimed</span>{% endif %}
    </h3>
    <p>{% if p.location %}{{ p.location }}{% endif %}{% if p.services %} &middot; {% for s in p.services %}{{ s }}{% unless forloop.last %}, {% endunless %}{% endfor %}{% endif %}</p>
    <span class="card-link">View profile &rarr;</span>
  </a>
  {% endfor %}
</div>

<h2>Run a company that should be listed?</h2>
<p>Use the <a href="{{ '/submit-your-agency/' | relative_url }}">Submit Your Agency</a> form, or <a href="{{ '/claim/' | relative_url }}">claim an existing listing</a> to confirm your company's information.</p>
