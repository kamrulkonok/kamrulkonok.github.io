---
layout: page
permalink: /research/
title: research
description: This page showcases my research contributions (pre-print version) and ongoing work in the areas of Foundation Models, Retrieval-Augmented Generation (RAG), Geometric Deep Learning, Medical Imaging, and Knowledge Graphs. While I continue to develop and refine my research, I am actively working on several projects that will be published in the near future.
nav: false
nav_order: 2
---

<!-- _pages/publications.md --
<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<section aria-labelledby="preprints-heading">
	<h2 id="preprints-heading">Preprints</h2>

	<div class="publications">
		{% bibliography %}
	</div>

	<section aria-labelledby="workshop-poster-abstracts-heading">
		<h3 id="workshop-poster-abstracts-heading">Workshop Poster Abstracts</h3>
		<div class="publications">
			{% bibliography -f workshops %}
		</div>
	</section>
</section>
