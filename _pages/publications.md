---
layout: page
permalink: /publications/
title: publications
description: 
years: [2022, 2021, 2019, 2018, 2015]
nav: true
nav_order: 1
categories: ['paper', 'book']
catprint: ['', 'Peer-Reviewed Articles', 'Book Chapters']
---
<!-- _pages/publications.md -->
<div class="publications">

{% for cat_ in page.categories  %}
	{% assign ind = forloop.index %}

	{%- capture cat -%}
	{{ page.catprint[ind] }}
	{%- endcapture -%}
	
	<h4 class="font-weight-bolder">{{cat}}</h4>

{%- for y in page.years %}
{%- capture citecount -%}
		{% bibliography_count -f papers -q @*[kind={{cat_}} && year={{y}}]* %}
		{%- endcapture -%}

		{% if citecount != "0"  %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[kind={{cat_}} && year={{y}}]* %}
{% endif %}
{% endfor %}
{% endfor %}

</div>
