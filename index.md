---
layout: default
title: Accueil
banner_image: /media/banners/robotgame.jpg
---

<section class="container-fluid home-section">
<div class="row">
<div class="col-md-3 col-md-push-3" markdown="1">

<h2 class="motto">La coupe de robotique jurassienne</h2>

La 5e édition de la Coupe Robots-JU a eu lieu le samedi 18 mars 2023 à Delémont.

La Coupe est organisée par [Robots-JU](https://robots-ju.ch/), un club de robotique jurassien.
Des équipes de jeunes de 9 à 16 ans construisent et programment pendant plusieurs mois des robots LEGO Mindstorms.
Lors de la compétition, les robots remplissent en autonomie des missions très variées pour marquer des points.

<div class="links">
  <a class="btn btn-lg btn-primary" href="/programme"><i class="fa fa-tasks" aria-hidden="true"></i> Programme de la journée</a>
</div>

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
        <section class="col-md-8 col-md-push-2">
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
    </div>
</div>
