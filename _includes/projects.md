<h2 id="selected-projects">Selected Projects</h2>

<div class="project-list">
{%- for project in site.data.projects %}
  {%- assign project_link = project.page | default: project.code %}
  <div class="project-item{% if project.featured %} project-item-featured{% endif %}">
    <div class="project-head">
      <span class="project-title">
        {%- if project_link %}<a href="{{ project_link }}" target="_blank" rel="noopener">{{ project.title }}</a>{% else %}{{ project.title }}{% endif %}
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
    {%- if project.page or project.code or project.report %}
    <div class="links">
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
{%- endfor %}
</div>
