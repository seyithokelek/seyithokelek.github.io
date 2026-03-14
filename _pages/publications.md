---
layout: page
permalink: /publications/
title: publications
description: Thaaaaaaaaaats all.
nav: true
nav_order: 3
social: true
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<div class="publications">

<h2>Refereed Journal Articles</h2>
{% bibliography --query @*[keywords~=journal] %}

<h2>Conference Proceedings</h2>
{% bibliography --query @*[keywords~=conference] %}

</div>
