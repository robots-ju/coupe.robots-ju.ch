---
layout: default
title: Accueil
---

<div class="area-content-top" style="background-image: url(/media/banners/robotgame.jpg);">
<div class="container-main">
<section class="section-popup" markdown="1">

La 3e édition de la Coupe Robots-JU se déroulera le samedi **24 mars** 2018 à Delémont !

La Coupe est organisée par [Robots-JU](https://robots-ju.ch/), un club de robotique jurassien.
Des équipes de jeunes de 10 à 16 ans construisent et programment pendant plusieurs mois des robots LEGO Mindstorms.
Lors de la compétition, les robots remplissent en autonomie des missions très variées pour marquer des points.

<a class="btn btn-center" href="/programme"><i class="fa fa-tasks" aria-hidden="true"></i> Le programme sera prochainement disponible</a>

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

