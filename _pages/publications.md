---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

{% if author.googlescholar %}
<p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank">Google Scholar profile</a>.</p>
{% endif %}

{% include base_path %}

{% assign published_pubs = site.publications | sort: "date" | reverse %}
{% assign selected_pubs = published_pubs | where: "selected", true %}
{% assign accepted_pubs = site.publications | where: "accepted", true | sort: "date" | reverse %}

{% if selected_pubs.size > 0 %}
<h2>Selected Works</h2>
{% for post in selected_pubs %}
  {% include archive-single-pubs.html %}
{% endfor %}
{% endif %}

{% if published_pubs.size > 0 %}
<h2>Other Publications</h2>
<ul style="list-style-type: none; padding: 0;">
{% for post in published_pubs %}
  {% unless post.selected %}
  <li style="margin-bottom: 12px; padding-bottom: 8px; border-bottom: 1px solid #f0f0f0;">
    <strong>
      {% if post.paperurl %}
        <a href="{{ post.paperurl }}" target="_blank" style="color: #333; text-decoration: none;">{{ post.title }}</a>
      {% else %}
        {{ post.title }}
      {% endif %}
    </strong><br>
    <span style="color: #666; font-size: 14px;">{{ post.authors }}</span><br>
    <span style="color: #666; font-size: 14px; font-style: italic;">{{ post.venue }}, {{ post.date | date: "%Y" }}</span>
    {% if post.paper or post.paperurl or post.code %}
      <span style="font-size: 14px;"> • 
        {% if post.paper or post.paperurl %}
          <a href="{% if post.paper %}{{ post.paper | relative_url }}{% else %}{{ post.paperurl }}{% endif %}" target="_blank" style="color: #0366d6;">Paper</a>
        {% endif %}
        {% if post.code %}
          {% if post.paper or post.paperurl %} • {% endif %}<a href="{{ post.code }}" target="_blank" style="color: #0366d6;">Code</a>
        {% endif %}
      </span>
    {% endif %}
  </li>
  {% endunless %}
{% endfor %}
</ul>
{% endif %}

{% if accepted_pubs.size > 0 %}
<h2>Accepted Publications</h2>
{% for post in accepted_pubs %} 
  {% include archive-single-pubs.html %} 
{% endfor %} 
{% endif %}