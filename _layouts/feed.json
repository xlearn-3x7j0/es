{
    "articles": [
    {% for post in site.posts limit:100 %}
        {
            "permalink": "{{ post.permalink }}",
            "title": {{ post.title | jsonify }},
            "image": "{{ post.image}}",
            "date": "{{ post.date }}",
            "domain": "{{ post.domain }}",
            "translations": {
                {% for tag in post.tags %}
                    "{{ tag }}": "{{ tag | append: post.url | absolute_url }}"{% if forloop.last == false %},{% endif %} {% endfor %}
            }
        }{% if forloop.last == false %},{% endif %}
    {% endfor %}
    ]
}
