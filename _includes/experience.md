<h2 id="selected-experience">Selected Experience</h2>

<div class="experience-list">
{%- for job in site.data.experience %}
  {%- if job.divider %}
  <div class="experience-divider"></div>
  {%- endif %}
  {%- if job.logo %}
  <img class="experience-logo" src="{{ job.logo }}?v={{ site.time | date: '%s' }}" alt="{{ job.org }} logo" />
  {%- else %}
  <i class="experience-icon {{ job.icon | default: 'fa-solid fa-flask' }}" aria-hidden="true"></i>
  {%- endif %}
  <div class="experience-text">
    <span class="experience-role">{{ job.role }}</span>
    <span class="experience-org">{% if job.link %}<a href="{{ job.link }}" rel="noopener"><autocolor>{{ job.org }}</autocolor></a>{% else %}{{ job.org }}{% endif %}</span>
    {%- if job.bullets %}
    <ul class="experience-bullets">
      {%- for item in job.bullets %}
      {%- if item.text %}
      <li>{{ item.text }}
        <ul>
          {%- for sub in item.sub %}
          <li>{{ sub }}</li>
          {%- endfor %}
        </ul>
      </li>
      {%- else %}
      <li>{{ item }}</li>
      {%- endif %}
      {%- endfor %}
    </ul>
    {%- elsif job.focus %}
    <span class="experience-focus">{{ job.focus }}</span>
    {%- endif %}
  </div>
  <span class="experience-time">{{ job.time }}</span>
{%- endfor %}
</div>
