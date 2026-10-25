<h2 id="selected-projects">Selected Projects</h2>

<div class="project-list">
{%- for project in site.data.projects %}
  <div class="project-item{% if project.featured %} project-item-featured{% endif %}">
    <div class="project-title">
      <a href="{{ project.page | default: project.code }}" target="_blank" rel="noopener">{{ project.title }}</a>
      {%- if project.featured %} <span class="project-badge">Featured</span>{% endif %}
    </div>
    <div class="project-desc">{{ project.description }}</div>
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
  </div>
{%- endfor %}
</div>
