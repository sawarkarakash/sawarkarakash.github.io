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
<div style="margin-bottom: 24px; padding-bottom: 16px; border-bottom: 1px solid #eee;">
  <h3 style="margin: 0 0 8px 0; font-size: 18px;">
    {% if post.paperurl %}
      <a href="{{ post.paperurl }}" target="_blank" style="color: #333; text-decoration: none;">{{ post.title }}</a>
    {% else %}
      {{ post.title }}
    {% endif %}
  </h3>
  <p style="margin: 0 0 4px 0; color: #666; font-size: 14px;">{{ post.authors }}</p>
  <p style="margin: 0 0 8px 0; color: #666; font-size: 14px; font-style: italic;">{{ post.venue }} • {{ post.date | date: "%Y" }}</p>
  
  {% if post.core or post.quartile or post.first_author %}
  <p style="margin: 0 0 8px 0; font-size: 13px;">
    {% if post.core %}<span style="color: #666;">CORE {{ post.core }}</span>{% endif %}
    {% if post.quartile %}{% if post.core %} • {% endif %}<span style="color: #666;">{{ post.quartile }}</span>{% endif %}
    {% if post.first_author %}{% if post.core or post.quartile %} • {% endif %}<span style="color: #666;">First Author</span>{% endif %}
  </p>
  {% endif %}

  <p style="margin: 8px 0; font-size: 14px;">
    {% if post.paper or post.paperurl %}
      <a href="{% if post.paper %}{{ post.paper | relative_url }}{% else %}{{ post.paperurl }}{% endif %}" target="_blank" style="color: #0366d6; margin-right: 12px;">Paper</a>
    {% endif %}
    {% if post.code %}
      <a href="{{ post.code }}" target="_blank" style="color: #0366d6;">Code</a>
    {% endif %}
  </p>
</div>
{% endfor %}
{% endif %}

{% if published_pubs.size > 0 %}
<h2>All Publications</h2>
{% for post in published_pubs %} 
  {% include archive-single-pubs.html %} 
{% endfor %} 
{% endif %}

{% if accepted_pubs.size > 0 %}
<h2>Accepted Publications</h2>
{% for post in accepted_pubs %} 
  {% include archive-single-pubs.html %} 
{% endfor %} 
{% endif %}