---
title: "publications"
layout: gridlay
sitemap: false
permalink: /publications/
years: [2022]
---

<div class="jumbotron">

### accepted
{% bibliography -f articles -q @*[published=True] %}

### preprints
{% bibliography -f articles -q @*[preprint=True] %}

</div>