---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css">
{% if author.googlescholar %}

<section> <h2>Google Scholar</h2> <p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">Google Scholar profile</a>.</p> </section> {% endif %}
{% include base_path %}

{% assign published_pubs = site.publications | where: "published", true | sort: "date" | reverse %}
{% assign accepted_pubs = site.publications | where: "accepted", true | sort: "date" | reverse %}

{% if published_pubs.size > 0 %}

<section> {% for post in published_pubs %} {% include archive-single-pubs.html %} {% endfor %} </section> {% endif %}
{% if accepted_pubs.size > 0 %}
