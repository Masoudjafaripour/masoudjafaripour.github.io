<h2 id="selected-projects">Selected Projects</h2>

<div class="project-list">
{%- for project in site.data.projects %}
  {%- assign project_link = project.page | default: project.code %}
  {%- if project.subpage %}{% assign project_href = project.subpage | relative_url %}{% else %}{% assign project_href = project_link %}{% endif %}
  {%- assign project_image = project.image | default: "assets/img/pubs/placeholder.svg" %}
  <div class="project-item{% if project.featured %} project-item-featured{% endif %}">
  <div class="project-row">
    <div class="project-thumb">
      {%- if project_href %}<a href="{{ project_href }}"{% unless project.subpage %} target="_blank" rel="noopener"{% endunless %}>{% endif -%}
      <img class="project-image" src="{{ project_image | relative_url }}?v={{ site.time | date: '%s' }}" alt="{% if project.image %}Preview of {{ project.title }}{% else %}Figure coming soon{% endif %}" loading="lazy" />
      {%- if project_href %}</a>{% endif %}
    </div>
    <div class="project-content">
    <div class="project-head">
      <span class="project-title">
        {%- if project.subpage %}<a href="{{ project.subpage | relative_url }}">{{ project.title }}</a>
        {%- elsif project_link %}<a href="{{ project_link }}" target="_blank" rel="noopener">{{ project.title }}</a>
        {%- else %}{{ project.title }}{% endif %}
        {%- if project.featured %} <span class="project-badge">Featured</span>{% endif %}
      </span>
      {%- if project.time %}
      <span class="project-time">{{ project.time }}</span>
      {%- endif %}
    </div>
    {%- if project.tech or project.context %}
    <div class="project-meta">{{ project.tech }}{% if project.tech and project.context %} &middot; {% endif %}{% if project.context %}<em>{{ project.context }}</em>{% endif %}</div>
    {%- endif %}
    <div class="project-desc">{{ project.description }}</div>
    {%- if project.subpage or project.page or project.code or project.report %}
    <div class="links">
      {%- if project.subpage %}
      <a href="{{ project.subpage | relative_url }}" class="btn">Details</a>
      {%- endif %}
      {%- if project.page %}
      <a href="{{ project.page }}" class="btn" target="_blank" rel="noopener">Project Page</a>
      {%- endif %}
      {%- if project.code %}
      <a href="{{ project.code }}" class="btn" target="_blank" rel="noopener">Code</a>
      {%- endif %}
      {%- if project.report %}
      <a href="{{ project.report }}" class="btn" target="_blank" rel="noopener">Report</a>
      {%- endif %}
    </div>
    {%- endif %}
    </div>
  </div>
  </div>
{%- endfor %}
</div>
