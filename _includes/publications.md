<h2 id="publications">Publications</h2>

<div class="publications">
<div class="publications-box">
<ol class="bibliography">
{%- for link in site.data.publications.main %}
<li>
<div class="pub-row">
  <div class="pub-content">
    <div class="title">{% if link.pdf %}<a href="{{ link.pdf }}">{{ link.title }}</a>{% else %}{{ link.title }}{% endif %}</div>
    {%- if link.authors %}
    <div class="author">{{ link.authors }}</div>
    {%- endif %}
    <div class="pub-meta">
      <span class="periodical"><em>{{ link.conference }}</em></span>
      <span class="links">
        {%- if link.pdf %}
        <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">PDF</a>
        {%- endif %}
        {%- if link.code %}
        <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">Code</a>
        {%- endif %}
        {%- if link.page %}
        <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">Project Page</a>
        {%- endif %}
        {%- if link.bibtex %}
        <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener">BibTeX</a>
        {%- endif %}
        {%- if link.notes %}
        <strong><i class="pub-note">{{ link.notes }}</i></strong>
        {%- endif %}
        {%- if link.others %}
        {{ link.others }}
        {%- endif %}
      </span>
    </div>
  </div>
</div>
</li>
{%- endfor %}
</ol>
</div>
</div>
