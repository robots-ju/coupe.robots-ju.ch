---
layout: widepage
title: Résultats 2026
permalink: /resultats/2026
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à tous pour vos excellents résultats !

<i class="fa fa-youtube-play" aria-hidden="true"></i>
La rediffusion du [live stream](https://www.youtube.com/watch?v=HXkNsDfRIv8) est disponible sur YouTube.

## Catégorie Explorateur

| Prix                      | Équipe                               |
|---------------------------|--------------------------------------|
| Modèle d'équipe           | Les archéologues sous-marins du Jura |
| Recherche poster d'équipe | Robots archéoloques du Jura          |
| Travail d'équipe          | Les capybaras romains du Jura XXL    |

## Catégorie Ingénieur

### Classement général

| # | Équipe                                        | Points |
|---|-----------------------------------------------|--------|
| 1 | **E-Arts**                                    | 86     |
| 2 | **Raptors.JU**                                | 84     |
| 3 | **Capricorns**                                | 64     |
| 4 | Capricorns Juniors                            | 40     |
| 5 | RoboHunter                                    | 38     |
| 6 | Jurartéfact                                   | 36     |
| 7 | Jura’rchéo                                    | 32     |
| 8 | Projet LBJ                                    | 26     |
| 9 | Les patatarchéologues                         | 19     |
|   | Les dinosaures robots têtes de pioche du Jura | 19     |

### Classement Robot-Game

| #  | Équipe                                        | Qualifications | Demi-finales | Finales |
|----|-----------------------------------------------|----------------|--------------|---------|
| 1  | **E-Arts**                                    | 845            | 400          | 985     |
| 2  | Capricorns                                    | 840            | 455          | 760     |
| 3  | RoboHunter                                    | 525            | 245          |         |
| 4  | Raptors.JU                                    | 580            | 220          |         |
| 5  | Capricorns Juniors                            | 400            |              |         |
| 6  | Jurartéfact                                   | 350            |              |         |
| 7  | Jura’rchéo                                    | 315            |              |         |
| 8  | Les dinosaures robots têtes de pioche du Jura | 275            |              |         |
| 9  | Projet LBJ                                    | 210            |              |         |
| 10 | Les patatarchéologues                         | 190            |              |         |

### Classement Live Challenge

| #  | Équipe                                        | Points |
|----|-----------------------------------------------|--------|
| 1  | **Raptors.JU**                                | 46     |
| 2  | E-Arts                                        | 33     |
| 3  | Capricorns Juniors                            | 15     |
| 4  | Jurartéfact                                   | 14     |
| 5  | Capricorns                                    | 13     |
|    | Projet LBJ                                    | 13     |
| 7  | Jura’rchéo                                    | 12     |
| 8  | Les patatarchéologues                         | 7      |
| 9  | RoboHunter                                    | 6      |
| 10 | Les dinosaures robots têtes de pioche du Jura | 3      |

### Esprit d'équipe

Le jury a attribué le prix d'esprit d'équipe à **Les dinosaures robots têtes de pioche du Jura**.

### Détail des matches du Robot-Game

Le tableau présente les 24 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			{% for team in site.data.resultats_2026.teams %}
			  <th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
    {% for match in site.data.resultats_2026.matches %}
	    <tr>
        <td>
          {{ match.number }}
          {% if match.game == 'semifinals' %}
          (demi)
          {% elsif match.game == 'semifinals-tiebreaker' %}
          (tiebreaker)
          {% elsif match.game == 'finals' %}
          (finale)
          {% endif %}
        </td>
        <td>{{ match.time }}</td>
			  {% for team in site.data.resultats_2026.teams %}
			    {% assign team_key = team[0] %}
			    {% assign table = match.teams[team_key] %}
	        {% if table %}
	          <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            {% if table.scoreboard %}
              <a href="https://fll-scoreboard.robots-ju.ch/unearthed#{{ table.scoreboard }}" class="js-scoreboard">{{ table.score }}</a>
	            {% else %}
	            <a href="#" class="js-missing-scoreboard">{{ table.score }}</a>
	            {% endif %}
            </td>
	        {% else %}
	          <td></td>
	        {% endif %}
        {% endfor %}
	    </tr>
    {% endfor %}
	</tbody>
</table>

<div class="content-overlay" id="js-overlay" style="display:none;">
    <div class="overlay-modal">
        <div class="overlay-header">
            <div class="close">Fermer <i class="fa fa-close"></i></div>
        </div>
        <div class="overlay-content" id="js-overlay-content"></div>
        <div class="overlay-footer">
            <a id="js-overlay-link" href="#" target="_blank">Ouvrir dans un nouvel onglet <i class="fa fa-external-link"></i></a>
        </div>
   </div>
</div>

<script>

(function() {
    var o = document.getElementById('js-overlay');
    var oc = document.getElementById('js-overlay-content');
    var ol = document.getElementById('js-overlay-link');

    function closeModal() {
        oc.innerHTML = '';
        o.style.display = 'none';
    }

    [].forEach.call(document.querySelectorAll('.js-scoreboard'), function(a) {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            oc.innerHTML = '<iframe width="853" height="600" src="' + a.href + '" frameborder="0"></iframe>';
            ol.href = a.href;
            o.style.display = 'block';
        });
    });
    
    [].forEach.call(document.querySelectorAll('.js-missing-scoreboard'), function(a) {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            alert('Malheureusement le détail de ce match n\'a pas été sauvegardé. Seul le score est disponible.');
        });
    });

    document.querySelector('#js-overlay .close').addEventListener('click', closeModal);
    o.addEventListener('click', function(e) {
        if (e.target === o) {
            closeModal();
        }
    });
})();

</script>

</div>
