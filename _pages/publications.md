---
layout: page
permalink: /publications/
title: Publications
description: Authors marked by * contributed equally.
years: [2021, 2020] # prepend new years here
nav: true
---

<div class="publications">

{% for y in page.years %}

  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
