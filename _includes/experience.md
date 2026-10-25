<h2 id="research-experience">Research Experience</h2>

<div class="experience-list">
{%- for job in site.data.experience %}
  {%- if job.divider %}
  <div class="experience-divider"></div>
  {%- endif %}
  {%- if job.logo %}
  <img class="experience-logo" src="{{ job.logo }}" alt="{{ job.org }} logo" />
  {%- else %}
  <i class="experience-icon {{ job.icon | default: 'fa-solid fa-flask' }}" aria-hidden="true"></i>
  {%- endif %}
  <span class="experience-org">{% if job.link %}<a href="{{ job.link }}" rel="noopener"><autocolor>{{ job.org }}</autocolor></a>{% else %}{{ job.org }}{% endif %} <span class="experience-role">({{ job.role }})</span>{% if job.focus %} <span class="experience-focus">&mdash; {{ job.focus }}</span>{% endif %}</span>
  <span class="experience-time">{{ job.time }}</span>
{%- endfor %}
</div>
