---
layout: default
---

## 分类文章列表
{% for category in site.categories %}
### {{ category | first }} ({{ category | last | size }})
{% for post in category.last %}
* {{ post.date | date:"%Y-%m-%d"}} [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endfor %}
{% endfor %}