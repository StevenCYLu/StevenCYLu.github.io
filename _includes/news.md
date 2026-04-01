<h2 id="news" style="margin: 2px 0px -15px;">News</h2>

<div class="news-section">
{% for item in site.data.news %}
<div class="news-item">
  <div class="news-date">{{ item.date }}</div>
  <div class="news-content">{{ item.content }}</div>
</div>
{% endfor %}
</div>
