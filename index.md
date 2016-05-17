---
layout: default
title: Accueil
---

<div class="area-content-top" style="background-image: url(/media/banners/robotgame.jpg);">
<div class="container-main">
<section class="section-popup" markdown="1">

Robots-JU présente la Coupe Robots-JU. La première édition se déroulera le 21 mai 2016 à Delémont.

Des équipes de jeunes filles et garçons de 10 à 16 ans construisent et programment pendant plusieurs mois des robots LEGO Mindstorms.

Lors de la compétition, les robots doivent remplir en autonomie des missions très variées pour remporter un maximum de points.

<a class="btn btn-center" href="/programme">Voir le Programme</a>

</section>
</div>
</div>
<div class="area-content-body">
	<div class="container-main">
		<section class="section-only-title">
			<h1>News</h1>
		</section>
		{% for post in site.news reversed %}
		<section class="section-popup">
			<h1>{{ post.title }} <small>{{ post.date | date_to_string }}</small></h1>
			{{ post.content }}
		</section>
		{% endfor %}
	</div>
	<div class="container-secondary">
		{% include sponsors.html %}
	</div>
</div>

