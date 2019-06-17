---
title:  "Portfolio"
layout: archive
permalink: /Portfolio/
author_profile: true
comments: true
---

This page contains a selection of my data science projects.  I seek to produce analysis, visualization, prediction, and writing that enables key insights which allow people to make more informed decisions.

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
