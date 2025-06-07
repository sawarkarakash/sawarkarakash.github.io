---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css">

<style>
.selected-works {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  padding: 25px;
  margin: 30px 0;
  box-shadow: 0 8px 32px rgba(0,0,0,0.1);
  position: relative;
  overflow: hidden;
}

.selected-works h2 {
  color: white;
  margin-bottom: 20px;
  font-size: 2.2em;
  font-weight: 700;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
  position: relative;
  z-index: 1;
}

.selected-works h2 i {
  margin-right: 10px;
  color: #ffd700;
  text-shadow: 0 0 10px rgba(255,215,0,0.5);
}

.selected-publication {
  background: rgba(255,255,255,0.95);
  border-radius: 8px;
  padding: 20px;
  margin: 15px 0;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  position: relative;
  z-index: 1;
}

.selected-publication:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.pub-title {
  font-size: 1.2em;
  font-weight: 600;
  color: #2c3e50;
  margin-bottom: 8px;
  line-height: 1.4;
}

.pub-title a {
  color: #2c3e50;
  text-decoration: none;
}

.pub-title a:hover {
  color: #3498db;
  text-decoration: none;
}

.pub-authors {
  color: #555;
  margin-bottom: 5px;
  font-style: italic;
}

.pub-venue {
  color: #e74c3c;
  font-weight: 600;
  margin-bottom: 8px;
}

.pub-ranking {
  background: linear-gradient(45deg, #ff6b6b, #ee5a24);
  color: white;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.85em;
  font-weight: 600;
  display: inline-block;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
  box-shadow: 0 2px 8px rgba(238,90,36,0.3);
  margin-right: 10px;
}

.first-author-badge {
  background: linear-gradient(45deg, #2ecc71, #27ae60);
  color: white;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.85em;
  font-weight: 600;
  display: inline-block;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
  box-shadow: 0 2px 8px rgba(39,174,96,0.3);
}

.pub-links {
  margin-top: 10px;
}

.pub-links a {
  display: inline-block;
  margin-right: 10px;
  padding: 6px 12px;
  background: #3498db;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.9em;
  transition: background 0.3s ease;
}

.pub-links a:hover {
  background: #2980b9;
  text-decoration: none;
}

.pub-links a.code-link {
  background: #2ecc71;
}

.pub-links a.code-link:hover {
  background: #27ae60;
}

.pub-links a.paper-link {
  background: #e74c3c;
}

.pub-links a.paper-link:hover {
  background: #c0392b;
}

.section-divider {
  height: 2px;
  background: linear-gradient(90deg, transparent, #ddd, transparent);
  margin: 40px 0;
}

.pub-excerpt {
  color: #666;
  font-size: 0.95em;
  line-height: 1.5;
  margin-top: 10px;
  border-left: 3px solid #3498db;
  padding-left: 15px;
  font-style: italic;
}
</style>

{% if author.googlescholar %}
<section> 
  <h2>Google Scholar</h2> 
  <p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">Google Scholar profile</a>.</p> 
</section> 
{% endif %}

{% include base_path %}

<!-- Selected Works Section -->
{% assign selected_pubs = site.publications | where_exp: "item", "item.selected != false and item.selected != nil" | sort: "selected" %}

{% if selected_pubs.size > 0 %}
<section class="selected-works">
  <h2><i class="fas fa-star"></i>Selected Works</h2>
  
  {% for post in selected_pubs %}
  <div class="selected-publication">
    <div class="pub-title">
      {% if post.paperurl %}
        <a href="{{ post.paperurl }}" target="_blank">{{ post.title }}</a>
      {% else %}
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% endif %}
    </div>
    <div class="pub-authors">{{ post.authors }}</div>
    <div class="pub-venue">{{ post.venue }}</div>
    <div>
      {% if post.core %}
        <span class="pub-ranking">CORE Rank: {{ post.core }}</span>
      {% endif %}
      {% if post.first_author %}
        <span class="first-author-badge">First Author</span>
      {% endif %}
    </div>
    {% if post.excerpt %}
    <div class="pub-excerpt">{{ post.excerpt | truncatewords: 30 }}</div>
    {% endif %}
    <div class="pub-links">
      {% if post.paper %}
        <a href="{{ post.paper | relative_url }}" target="_blank" class="paper-link">
          <i class="fas fa-file-pdf"></i> PDF
        </a>
      {% endif %}
      {% if post.paperurl %}
        <a href="{{ post.paperurl }}" target="_blank" class="paper-link">
          <i class="fas fa-external-link-alt"></i> Publisher
        </a>
      {% endif %}
      {% if post.code %}
        <a href="{{ post.code }}" target="_blank" class="code-link">
          <i class="fas fa-code"></i> Code
        </a>
      {% endif %}
      <a href="{{ post.url | relative_url }}">
        <i class="fas fa-info-circle"></i> Details
      </a>
    </div>
  </div>
  {% endfor %}
</section>

<div class="section-divider"></div>
{% endif %}

<!-- All Publications -->
{% assign published_pubs = site.publications | where: "published", "yes" | sort: "date" | reverse %}
{% assign accepted_pubs = site.publications | where: "accepted", true | sort: "date" | reverse %}

{% if published_pubs.size > 0 %}
<section> 
  <h2>All Publications</h2>
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