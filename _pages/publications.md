---
title: "Publications"
permalink: /publications/
---

{% assign scholar = site.author.links | where: "label", "Google Scholar" | first %}
For a complete list, please browse my [Google Scholar]({{ scholar.url }}).
{: .pub-intro}

{% for pub in site.data.publications %}
{% assign main_url = pub.links[0].url %}
<div class="pub">
  <a class="pub__thumb" href="{{ main_url }}" aria-hidden="true" tabindex="-1">
    {% if pub.image %}
      <img src="{{ '/assets/images/papers/' | append: pub.image | relative_url }}?v={{ site.time | date: '%s' }}" alt="" loading="lazy">
    {% else %}
      <span class="pub__placeholder"><i class="far fa-file-lines"></i></span>
    {% endif %}
  </a>
  <div class="pub__body">
    <a class="pub__title" href="{{ main_url }}">{{ pub.title }}</a>
    <span class="pub__line">{{ pub.authors | replace: "Shah, Devesh", "<b>Shah, Devesh</b>" }}</span>
    <span class="pub__line pub__venue">{{ pub.venue }}{% if pub.award %} <span class="pub__award">{{ pub.award }}</span>{% endif %}</span>
    <span class="pub__line pub__links">{% for link in pub.links %}<a href="{{ link.url }}">[{{ link.label }}]</a> {% endfor %}{% if pub.bibtex %}<button type="button" class="pub__bibtex-toggle" aria-expanded="false" aria-controls="bibtex-{{ forloop.index }}">[BibTeX]</button>{% endif %}</span>
    {% if pub.bibtex %}
    <div class="pub__bibtex" id="bibtex-{{ forloop.index }}" hidden>
      <button type="button" class="pub__bibtex-copy">Copy</button>
      <pre>{{ pub.bibtex | strip | xml_escape }}</pre>
    </div>
    {% endif %}
  </div>
</div>
{% endfor %}

<script>
  // [BibTeX] toggles the citation under its paper; Copy puts it on the clipboard
  document.addEventListener("click", function (event) {
    var toggle = event.target.closest(".pub__bibtex-toggle");
    if (toggle) {
      var box = document.getElementById(toggle.getAttribute("aria-controls"));
      box.hidden = !box.hidden;
      toggle.setAttribute("aria-expanded", String(!box.hidden));
      return;
    }

    var copy = event.target.closest(".pub__bibtex-copy");
    if (copy) {
      var pre = copy.parentElement.querySelector("pre");
      var done = function (label) {
        copy.textContent = label;
        setTimeout(function () { copy.textContent = "Copy"; }, 1500);
      };
      // Fallback when the Clipboard API is unavailable or denied: select the
      // citation and try the legacy copy command (leaves it selected for Cmd+C)
      var fallback = function () {
        var range = document.createRange();
        range.selectNodeContents(pre);
        var selection = window.getSelection();
        selection.removeAllRanges();
        selection.addRange(range);
        done(document.execCommand("copy") ? "Copied" : "Selected");
      };
      if (navigator.clipboard) {
        navigator.clipboard.writeText(pre.textContent).then(function () { done("Copied"); }, fallback);
      } else {
        fallback();
      }
    }
  });
</script>
