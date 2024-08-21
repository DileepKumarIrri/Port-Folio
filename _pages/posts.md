---
layout: archive
author_profile: false
permalink: /posts/
title: "Overflow"
excerpt: "Thoughts on neuroscience, statistics, computing"
header:
  overlay_image: ../images/computer.jpg
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
---

{% include base_path %}
{% capture written_year %}'None'{% endcapture %}
{% for post in site.posts %}
{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
{% if year != written_year %}
<h2 id="{{ year | slugify }}" class="archive__subtitle">{{ year }}</h2>
{% capture written_year %}{{ year }}{% endcapture %}
{% endif %}
{% include archive-single.html %}
{% endfor %}
