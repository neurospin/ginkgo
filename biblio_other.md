---
title:
layout: page
permalink: /bibliography/other
---


<h2> Publications of the {{site.title}} group </h2>

{% assign today = site.time | date: '%Y' %}
{% assign biblio_sorted = (site.biblio | sort: 'year' | reverse %}

{% for idx in (0..7) %}

{% assign year = today | minus: idx %}

<div class="bibliography_header">
<h3>{{year}}</h3>
</div>

<div class="bibliography">
  {% for entry in biblio_sorted %}
    {% if entry.year == year %}
    <div class="text-justify">
        <li>
        {% if entry.journal %}
            {{entry.author}} {{entry.title}}, <i>{{entry.journal}}</i> ({{entry.year}})
        {% elsif entry.booktitle %}
            {{entry.author}} {{entry.title}}, {{entry.booktitle}} ({{entry.year}})
        {% else %}
            {{entry.author}} {{entry.title}} ({{entry.year}})
        {% endif %}
        {% if entry.doi %}
            <a href="http://doi.org/{{entry.doi}}" class="button tiny">DOI</a>
        {% endif %}
        {% if entry.pdf %}
            <a href="{{entry.pdf}}" class="button tiny">PDF</a>
        {% endif %}
        </li>
    </div>
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}
