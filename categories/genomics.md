---
layout: page
category: genomics
permalink: /categories/genomics/
---

# Paper topics

<div class="explore">
    <ul class="categories">
		<li class="categories__item"><a href="{{ '/notes' | prepend: site.baseurl }}">All</a></li>
        {% for category in site.data.categories %}
            {% if category.slug == "genomics" %}
              <li class="categories__item"><a href="{{ '/categories/' | append: category.slug | prepend: site.baseurl }}" style="text-decoration:underline;color:black">{{ category.name }}</a></li>
            {% else %}
              <li class="categories__item"><a href="{{ '/categories/' | append: category.slug | prepend: site.baseurl }}">{{ category.name }}</a></li>
            {% endif %}
        {% endfor %}
    </ul>
</div>

<ul class="list-posts">
    {% for post in site.categories.genomics %}
        <li class="post-teaser">
            <a href="{{ post.url | prepend: site.baseurl }}">
                <span class="post-teaser__title">{{ post.title }}</span>
                <span class="post-teaser__date">{{ post.date | date: "%d %B %Y" }}</span>
            </a>
        </li>
    {% endfor %}
</ul>
