---
permalink: /trips/
title: Bicycle Touring
author_profile: false
header:
  overlay_image: ../images/glacier.jpg
  overlay_filter: 0.2 # same as adding an opacity of 0.5 to a black background
---

I enjoy bicycle touring. Here are some trip reports. 

<ul>
    {% assign sorted = (site.trips | sort: 'date') | reverse %}
    {% for trip in sorted %}
<li> {{ trip.date | date: '%B %d, %Y' }} <a href="{{ trip.url }}">{{ trip.title }}</a></li>
    {% endfor %}
</ul>
