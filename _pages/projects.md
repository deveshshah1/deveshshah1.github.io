---
title: "Personal Projects"
permalink: /projects/
---

{% assign github = site.author.links | where: "label", "GitHub" | first %}
Things I've built outside of my day job. For a complete list, please browse my [GitHub]({{ github.url }}).
{: .pub-intro}

<div class="project-grid">
{% for project in site.data.projects %}
{% assign main_url = project.links[0].url %}
  <article class="project-card">
    {% if main_url %}<a class="project-card__media" href="{{ main_url }}" aria-hidden="true" tabindex="-1">{% else %}<div class="project-card__media">{% endif %}
      {% if project.image %}
        <img src="{{ '/assets/images/projects/' | append: project.image | relative_url }}?v={{ site.time | date: '%s' }}" alt="" loading="lazy">
      {% else %}
        <span class="project-card__tile" style="--accent: {{ project.accent | default: '#3bb9ff' }}"><i class="{{ project.icon }}"></i></span>
      {% endif %}
    {% if main_url %}</a>{% else %}</div>{% endif %}
    <div class="project-card__body">
      <h3 class="project-card__title">{% if main_url %}<a href="{{ main_url }}">{{ project.title }}</a>{% else %}{{ project.title }}{% endif %}</h3>
      <p class="project-card__desc">{{ project.description }}</p>
      {% if project.tags %}<ul class="project-card__tags">{% for tag in project.tags %}<li>{{ tag }}</li>{% endfor %}</ul>{% endif %}
      {% if project.links %}<span class="pub__links project-card__links">{% for link in project.links %}<a href="{{ link.url }}">[{{ link.label }}]</a> {% endfor %}</span>{% endif %}
    </div>
  </article>
{% endfor %}
</div>
