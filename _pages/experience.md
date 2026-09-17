---
title: "Experience"
permalink: /experience/
---

## Selected work

<ul class="highlights">
{% for item in site.data.experience.highlights %}
  <li>
    <span class="highlight__title">{{ item.title }}<span class="highlight__org">{{ item.org }}</span></span>
    <span class="highlight__desc">{{ item.description }}{% if item.links %} <span class="pub__links highlight__links">{% for link in item.links %}<a href="{{ link.url }}">[{{ link.label }}]</a>{% unless forloop.last %} {% endunless %}{% endfor %}</span>{% endif %}</span>
  </li>
{% endfor %}
</ul>

## Work Experience

<ol class="timeline">
{% assign prev_org = "" %}
{% for role in site.data.experience.roles %}
  {% assign same_org = false %}{% if role.org == prev_org %}{% assign same_org = true %}{% endif %}
  <li class="timeline__item{% if same_org %} timeline__item--cont{% endif %}">
    {% unless same_org %}<span class="timeline__mark"><img src="{{ '/assets/images/logos/' | append: role.logo | relative_url }}?v={{ site.time | date: '%s' }}" alt="{{ role.org }}" loading="lazy"></span>{% endunless %}
    <span class="timeline__dates">{{ role.dates }}</span>
    <span class="timeline__body">
      {% if same_org %}<span class="visually-hidden">{{ role.org }}</span>{% else %}<span class="timeline__org">{{ role.org }}</span>{% endif %}
      <span class="timeline__role">{{ role.role }} · {{ role.location }}</span>
      <span class="timeline__summary">{{ role.summary }}</span>
    </span>
  </li>
  {% assign prev_org = role.org %}
{% endfor %}
</ol>

## Education

<ol class="timeline">
{% for school in site.data.experience.education %}
  <li class="timeline__item">
    <span class="timeline__mark"><img src="{{ '/assets/images/logos/' | append: school.logo | relative_url }}?v={{ site.time | date: '%s' }}" alt="{{ school.school }}" loading="lazy"></span>
    <span class="timeline__dates">{{ school.dates }}</span>
    <span class="timeline__body">
      <span class="timeline__org">{{ school.school }}</span>
      <span class="timeline__role">{{ school.degree }}</span>
    </span>
  </li>
{% endfor %}
</ol>
