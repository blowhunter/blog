---
layout: page
title: 陋室蔷薇
tagline: 简陋破败中寻找生命的真迹..
---
{% include JB/setup %}
访问量：<span data-hk-page="current"> - </span>次

{% for post in site.posts %}
<div class = "card">
	<div class = "date_label">
		<div class="day_month">
    		{{ post.date | date:"%m/%d" }}
      	</div>
      	<div class="year">
      		{{ post.date | date:"%Y" }}
      	</div>
    </div> 
	<h3><a class="fa fa-link" href="{{ BASE_PATH }}{{ post.url }}">{{ post.title || split:'<!--break-->' | first }}</a></h3>
	    {{ post.excerpt }} ...
    <div class = "tags">
        {% unless site.tags == empty %}
    		<ul class="tag_box inline ">
     			<li><i class="icon-tags"></i></li>
      			{% assign tags_list = post.tags %}
      			{% include JB/tags_list %}
    		</ul>
  		{% endunless %} 
	</div>
	
</div>

{% endfor %}

