---
layout: post
title:  "ROC Curve 예제2"
date:   2017-03-18 18:44:00 +0900
categories: ROC_curve
comments: true
---

a
{{ page.url | absolute_url }}
b
{% for category in site.categories %}
  <li><a name="{{ category | first }}">{{ category | first }}</a>
    <ul>
    {% for posts in category %}
      {% for post in posts %}
        {% if post.url %}
          <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endif %}
      {% endfor %}
    {% endfor %}
    </ul>
  </li>
{% endfor %}

<h1 class='tag'>Blog Posts Sorted By Category</h1>
{% assign sorted_categories = site.categories | sort {|left, right| left[0] <=> right[0]} %}
{% for tag in sorted_categories %}
  <h2 class='tag' id="{{ tag[0] }}">{{ tag[0] | capitalize }}</h2>
  <ul class="post-list">
    {% assign pages_list = tag[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ site.url }}{{ post.url }}">
          <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></span>
          &bull;
          {{ post.title }}
        </a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}
