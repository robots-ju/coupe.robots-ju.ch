---
layout: widepage
title: Résultats 2018
permalink: /resultats/2018
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à toutes les équipes pour vos excellents résultats !

<i class="fa fa-link" aria-hidden="true"></i>
Consulter les Résultats [2016](/resultats/2016) ou [2017](/resultats/2017)

Retrouvez les photos de la journée [sur notre album Flickr](https://www.flickr.com/photos/robots-ju/sets/72157665226069147)

## Classement général

|  # | Équipe                  | Points |
| -- | ----------------------- | ------ |
|  1 | **Juratlantique**       | 94     |
|  2 | **Jur'Aqua**            | 75     |
|  3 | **Smilebots**           | 69     |
|  4 | Saint Roch              | 61     |
|  5 | Jur-à-l'eau             | 47     |
|  6 | NEoboticiens            | 45     |
|  - | Les piments d'Espelette | 45     |
|  8 | Jura flaque             | 41     |
|  9 | Lego Riz du Jura        | 38     |
| 10 | Les biennois en force   | 19     |

## Jury Special

**Saint Roch** reçoit le prix spécial du jury pour leur esprit d'équipe et leurs excellentes performances dans les différentes tâches.

## Classement Robot-Game

|  # | Équipe                  | Manches | Demi-finales | Finales |
| -- | ----------------------- | ------- | ------------ | ------- |
|  1 | **Smilebots**           | 620     | 280          | 620     |
|  2 | Juratlantique           | 540     | 280          | 500     |
|  3 | Jur-à-l'eau             | 350     | 130          |
|  4 | Saint Roch              | 340     | 80           |
|  5 | NEoboticiens            | 325     |
|  6 | Jur'Aqua                | 310     |
|  7 | Jura flaque             | 230     |
|  - | Lego Riz du Jura        | 230     |
|  9 | Les piments d'Espelette | 175     |
| 10 | Les biennois en force   | 125     |

## Classement Live Challenge

|  # | Équipe                  | Points |
| -- | ----------------------- | ------ |
|  1 | **Juratlantique**       | 16     |
|  - | **Jur'Aqua**            | 16     |
|  3 | Saint Roch              | 11     |
|  4 | Les piments d'Espelette | 10     |
|  5 | Jura flaque             | 7      |
|  6 | Smilebots               | 6      |
|  - | Jur-à-l'eau             | 6      |
|  - | NEoboticiens            | 6      |
|  - | Lego Riz du Jura        | 6      |
| 10 | Les biennois en force   | 3      |

## Détail des matches du Robot-Game

Le tableau présente les 49 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-youtube-play" aria-hidden="true"></i>
Un replay avec commentaire de chaque match a été extrait depuis la [diffusion live sur YouTube](https://www.youtube.com/watch?v=kOHMb3vtT3g) durant l'événement.
Cliquer sur l'icône pour visionner la vidéo du match correspondant.
[Consulter la playlist complète sur YouTube](https://www.youtube.com/playlist?list=PLJd3CiuQpT1zHwuOjspiPtOB4OFWZ0p0e).

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			<th>Visionner</th>
			{% for team in site.data.resultats_2018.teams %}
			<th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
	    {% for match in site.data.resultats_2018.matches %}
	    <tr>
	        <td>
	            {{ match.number }}
	            {% if match.game == 'semifinals' %}
	            (demi)
	            {% elsif match.game == 'finals' %}
	            (finale)
	            {% endif %}
            </td>
	        <td>{{ match.time }}</td>
	        <td><a title="Replay" href="https://www.youtube.com/watch?v={{ match.youtube }}" data-youtube="{{ match.youtube }}">
	            <i class="fa fa-youtube-play" aria-hidden="true"></i>
	            Replay
            </a></td>
			{% for team in site.data.resultats_2018.teams %}
			{% assign team_key = team[0] %}
			{% assign table = match.teams[team_key] %}
	        {% if table %}
	        <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            <a href="https://fll-scoreboard-2017.robots-ju.ch/#{{ table.scoreboard | jsonify | xml_escape }}" class="js-scoreboard">{{ table.score }}</a>
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

    [].forEach.call(document.querySelectorAll('[data-youtube]'), function(a) {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            oc.innerHTML = '<iframe width="853" height="480" src="https://www.youtube.com/embed/' + a.dataset.youtube + '" frameborder="0" allowfullscreen></iframe>';
            ol.href = a.href;
            o.style.display = 'block';
        });
    });

    [].forEach.call(document.querySelectorAll('.js-scoreboard'), function(a) {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            oc.innerHTML = '<iframe width="853" height="600" src="' + a.href + '" frameborder="0"></iframe>';
            ol.href = a.href;
            o.style.display = 'block';
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
