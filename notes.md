---
layout: page
title:
permalink: /notes/
---

# Paper topics

<div class="explore">
    <ul class="categories">
		<li class="categories__item"><a href="{{ '/notes' | prepend: site.baseurl }}" style="text-decoration:underline;color:black">All</a></li>
        {% for category in site.data.categories %}
            <li class="categories__item"><a href="{{ '/categories/' | append: category.slug | prepend: site.baseurl }}">{{ category.name }}</a></li>
        {% endfor %}
    </ul>
</div>

<ul class="list-posts">
    {% for post in site.categories.notes %}
        <li class="post-teaser">
            <a href="{{ post.url | prepend: site.baseurl }}">
                <span class="post-teaser__title">{{ post.title }}</span>
                <span class="post-teaser__date">{{ post.date | date: "%d %B %Y" }}</span>
            </a>
        </li>
    {% endfor %}
</ul>
