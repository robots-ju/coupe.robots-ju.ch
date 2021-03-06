---
layout: default
title: Accueil
banner_image: /media/banners/robotgame.jpg
---

<section class="container-fluid home-section">
<div class="row">
<div class="col-md-3 col-md-push-3" markdown="1">

<h2 class="motto">La coupe de robotique jurassienne</h2>

<div class="alert alert-danger" markdown="1">
La Coupe Robots-JU 2020 est annulée. [Lire le communiqué](/2020/03/12/annulation-coupe-2020).
</div>

La 5e édition de la Coupe Robots-JU aurait dû avoir lieu le samedi 4 avril 2020 durant le salon de la formation à Delémont.

La Coupe est organisée par [Robots-JU](https://robots-ju.ch/), un club de robotique jurassien.
Des équipes de jeunes de 10 à 16 ans construisent et programment pendant plusieurs mois des robots LEGO Mindstorms.
Lors de la compétition, les robots remplissent en autonomie des missions très variées pour marquer des points.

<div class="links">
  <ul class="list-inline social">
      {% for link in site.social_links %}
      <li><a href="{{ link.url }}" title="{{ link.title }}"><span class="fa fa-{{ link.icon }}"></span></a></li>
      {% endfor %}
  </ul>
</div>

</div>
    <div class="col-md-6 col-md-push-3">
        <div class="picture-wall wall-right">
            <div class="pic-col">
                <div class="pic-line">
                    <div class="pic" style="background-image: url(/media/mosaic/home1.jpg);"></div>
                    <div class="pic g2" style="background-image: url(/media/mosaic/home2.jpg);"></div>
                </div>
                <div class="pic-line g2">
                    <div class="pic g2" style="background-image: url(/media/mosaic/home3.jpg);"></div>
                    <div class="pic" style="background-image: url(/media/mosaic/home4.jpg);"></div>
                </div>
                <div class="pic-line">
                    <div class="pic" style="background-image: url(/media/mosaic/home5.jpg);"></div>
                    <div class="pic" style="background-image: url(/media/mosaic/home6.jpg);"></div>
                </div>
            </div>
        </div>
    </div>
</div>
</section>

{% include sponsoring.html %}

<div class="container page">
    <div class="row">
        <section class="col-md-8">
            <h2>Dernières news</h2>
            <div class="row">
                {% for post in site.posts limit:6 %}
                <article class="col-md-6">
                    <h3><a href="{{ post.url }}">{{ post.title | escape }}</a></h3>
                    <p>Posté le {{ post.date | date: "%-d %b %Y" }}</p>
                    {{ post.excerpt }}
                    <p><a href="{{ post.url }}">Lire le message complet <i class="fa fa-arrow-right"></i></a></p>
                </article>
                {% cycle '', '</div><div class="row">' %}
                {% endfor %}
            </div>
            <div class="row">
                {% for post in site.posts offset:6 limit:6 %}
                <article class="col-md-6">
                    <h3><a href="{{ post.url }}">{{ post.title | escape }}</a></h3>
                    <p>Posté le {{ post.date | date: "%-d %b %Y" }}</p>
                    <p><a href="{{ post.url }}">Lire le message <i class="fa fa-arrow-right"></i></a></p>
                </article>
                {% cycle '', '</div><div class="row">' %}
                {% endfor %}
            </div>
            <h3><i class="fa fa-list"></i> <a href="/tous-les-posts">Tous les posts</a></h3>
        </section>
        <section class="col-md-4">
            <a class="twitter-timeline" data-lang="fr" data-height="2000" href="https://twitter.com/CoupeRobotsJU">Tweets by CoupeRobotsJU</a>
        </section>
    </div>
</div>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
