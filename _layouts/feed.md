
---
layout: null
---
{
    {% comment %} 
        s/author/domain, s/tag/translation
    {% endcomment %}
    "articles": [
    {% for post in site.posts limit:100 %}
        {
            "original_url": "{{ post.original_url }}",
            "title": {{ post.title | jsonify }},
            {% if post.image.size > 1 %}"image": {{ post.image | jsonify }},{% endif %}
            {% if post.link.size > 1 %}"external_url": "{{ post.link }}",{% endif %}
            {% if post.tags.size > 1 %}"tags": {{ post.tags | jsonify }},{% endif %}
            "date": "{{ post.date }}",
            "domain": "{{ post.author }}",
            "translations": {{% for tag in post.tags %}
                "{{ tag }}": "{{ tag | append: post.url | absolute_url }}",
            {% endfor %}
            }
        }{% if forloop.last == false %},{% endif %}
    {% endfor %}
    ]
}
