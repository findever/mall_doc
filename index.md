---
layout: default
---

## 文章列表
{%for post in site.posts %}
* {{ post.date | date_to_string }} [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endfor %}

## 分类文章列表
{% for category in site.categories %}
### {{ category | first }} （{{ category | last | size }}）
{% for post in category.last %}
	1. {{ post.date | date:"%Y-%m-%d"}} [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endfor %}
{% endfor %}