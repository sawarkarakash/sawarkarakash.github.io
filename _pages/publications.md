---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css">

{% if author.googlescholar %}
<section> 
  <h2>Google Scholar</h2> 
  <p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">Google Scholar profile</a>.</p> 
</section> 
{% endif %}

{% include base_path %}

{% assign published_pubs = site.publications | sort: "date" | reverse %}
{% assign selected_pubs = published_pubs | where: "selected", true %}
{% assign accepted_pubs = site.publications | where: "accepted", true | sort: "date" | reverse %}

{% if selected_pubs.size > 0 %}
<section style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-radius: 12px; padding: 25px; margin: 30px 0; color: white;">
  <h2 style="color: white;"><i class="fas fa-star" style="color: #ffd700;"></i> Selected Works</h2>
  {% for post in selected_pubs %}
  <div style="background: rgba(255,255,255,0.95); border-radius: 8px; padding: 20px; margin: 15px 0; color: #333;">
    <h3 style="color: #2c3e50; margin-bottom: 10px;">
      {% if post.paperurl %}
        <a href="{{ post.paperurl }}" target="_blank" style="color: #2c3e50; text-decoration: none;">{{ post.title }}</a>
      {% else %}
        {{ post.title }}
      {% endif %}
    </h3>
    <p style="color: #555; font-style: italic; margin-bottom: 5px;">{{ post.authors }}</p>
    <p style="color: #e74c3c; font-weight: 600; margin-bottom: 8px;">{{ post.venue }}</p>
    {% if post.core %}
      <span style="background: #e74c3c; color: white; padding: 4px 12px; border-radius: 20px; font-size: 0.85em; font-weight: 600;">CORE Rank: {{ post.core }}</span>
    {% endif %}
    <div style="margin-top: 10px;">
      {% if post.paper %}
        <a href="{{ post.paper | relative_url }}" target="_blank" style="display: inline-block; margin-right: 10px; padding: 6px 12px; background: #e74c3c; color: white; text-decoration: none; border-radius: 5px; font-size: 0.9em;">PDF</a>
      {% endif %}
      {% if post.code %}
        <a href="{{ post.code }}" target="_blank" style="display: inline-block; margin-right: 10px; padding: 6px 12px; background: #2ecc71; color: white; text-decoration: none; border-radius: 5px; font-size: 0.9em;">Code</a>
      {% endif %}
    </div>
  </div>
  {% endfor %}
</section>
{% endif %}

{% if published_pubs.size > 0 %}
<section> 
  {% for post in published_pubs %} 
    {% include archive-single-pubs.html %} 
  {% endfor %} 
</section> 
{% endif %}

{% if accepted_pubs.size > 0 %}
<section> 
  <h2>Accepted Publications</h2> 
  {% for post in accepted_pubs %} 
    {% include archive-single-pubs.html %} 
  {% endfor %} 
</section> 
{% endif %}