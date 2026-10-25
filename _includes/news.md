<h2 id="news">News</h2>

<div class="news-box">
{%- for item in site.data.news %}
  <div class="news-item{% if item.milestone %} news-item-milestone{% endif %}">
    <span class="news-date">[{{ item.date }}]</span> {{ item.text }}
  </div>
{%- endfor %}
</div>
