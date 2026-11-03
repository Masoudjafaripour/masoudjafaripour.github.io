<h2 id="publications">Publications</h2>

<div class="publications">
<ol class="bibliography">
{%- for link in site.data.publications.main %}
<li>
<div class="pub-row">
  <div class="pub-thumb">
    {%- if link.badge %}
    <span class="pub-badge">{{ link.badge }}</span>
    {%- endif %}
    {%- assign pub_image = link.image | default: "assets/img/pubs/placeholder.svg" %}
    <img class="pub-image" src="{{ pub_image | relative_url }}?v={{ site.time | date: '%s' }}" alt="{% if link.image %}Teaser figure for {{ link.title }}{% else %}Figure coming soon{% endif %}" loading="lazy" />
  </div>
  <div class="pub-content">
    <div class="title">{% if link.pdf %}<a href="{{ link.pdf }}">{{ link.title }}</a>{% else %}{{ link.title }}{% endif %}</div>
    {%- if link.authors %}
    <div class="author">{{ link.authors }}</div>
    {%- endif %}
    <div class="periodical"><em>{{ link.conference }}</em>
      {%- if link.notes %} <strong><i class="pub-note">{{ link.notes }}</i></strong>{% endif %}
    </div>
    {%- if link.pdf or link.code or link.page or link.video or link.bibtex or link.others %}
    <div class="links">
      {%- if link.pdf %}
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">PDF</a>
      {%- endif %}
      {%- if link.code %}
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">Code</a>
      {%- endif %}
      {%- if link.page %}
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">Project Page</a>
      {%- endif %}
      {%- if link.video %}
      <a href="{{ link.video }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">Video</a>
      {%- endif %}
      {%- if link.bibtex %}
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">BibTeX</a>
      {%- endif %}
      {%- if link.others %}
      {{ link.others }}
      {%- endif %}
    </div>
    {%- endif %}
  </div>
</div>
</li>
{%- endfor %}
</ol>
</div>
