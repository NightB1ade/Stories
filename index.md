---
---

<h2>By Date</h2>
<ul>
	{% for post in site.posts %}
	<li>
		<p><a href="{{ post.url }}">{{ post.title }}</a> – {% assign d = post.date | date: "%-d" %}
			{%- case d %}
			{% when "1" or "21" or "31" %}{{ d }}<sup>st</sup>
				{% when "2" or "22" %}{{ d }}<sup>nd</sup>
				{% when "3" or "23" %}{{ d }}<sup>rd</sup>
				{% else %}{{ d }}<sup>th</sup>
			{%- endcase %} {{ post.date | date: "%B %Y" }}</p>
		<span class="postexcerpt">{{ post.excerpt }}</span>
	</li>
	{% endfor %}
</ul>


<h2>By Tag</h2>
{%- assign sorted_tags = site.tags | sort:tag[0] %}
{%- for tag in sorted_tags %}
<h3>{{ tag[0] }}</h3>
<ul>
	{% for post in tag[1] %}
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
</ul>
{% endfor %}
