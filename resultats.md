---
layout: page
title: Résultats 2017
permalink: /resultats
banner_image: /media/banners/area.jpg
section_large: true
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à **MADAORPLULA** qui remporte le trophée du Robot-Game et de la Coupe Robots-JU !

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à **TEAM JUR'ALLIES** qui remporte le trophée du meilleur Live Challenge !

<i class="fa fa-link" aria-hidden="true"></i>
Consulter les [Résultats 2016](/resultats-2016)

## Classement général

| # | Équipe              | Points |
| - | ------------------- | ------ |
| 1 | **MADAORPLULA**     | 95     |
| 2 | **TEAM JUR'ALLIES** | 66     |
| 3 | **ROBOT DESTINY**   | 64     |
| 4 | NEOBOTICIENS        | 54     |
| - | TEAM JURA 2         | 54     |
| 6 | ST ROCH             | 52     |
| 7 | ROBOTEENS 2.0       | 39     |
| 8 | CUB-X               | 34     |
| 9 | RHINO               | 33     |

## Classement Robot-Game

| # | Équipe          | Manches | Demi-finales | Finales |
| - | --------------- | ------- | ------------ | ------- |
| 1 | **MADAORPLULA** | 406     | 102          | 287     |
| 2 | ROBOT DESTINY   | 351     | 191          | 196     |
| 3 | NEOBOTICIENS    | 264     | 62           |
| 4 | TEAM JURA 2     | 217     | 0            |
| 5 | ROBOTEENS 2.0   | 143     |
| 6 | TEAM JUR'ALLIES | 133     |
| 7 | RHINO           | 125     |
| 8 | ST ROCH         | 112     |
| 9 | CUB-X           | 106     |

<i class="fa fa-info" aria-hidden="true"></i>
Le détail des manches du Robot-Game sera publié prochainement

## Classement Live Challenge

| # | Équipe              | Points |
| - | ------------------- | ------ |
| 1 | **TEAM JUR'ALLIES** | 28     |
| 2 | MADAORPLULA         | 25     |
| 3 | ST ROCH             | 21     |
| 4 | TEAM JURA 2         | 15     |
| 5 | CUB-X               | 12     |
| - | NEOBOTICIENS        | 12     |
| - | ROBOT DESTINY       | 12     |
| - | ROBOTEENS 2.0       | 12     |
| 9 | RHINO               | 10     |

### Détail des matches

Le tableau présente les 40 matches (qualification et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-youtube-play" aria-hidden="true"></i>
Un replay avec commentaire de chaque match a été extrait depuis le flux que nous avons diffusé en live sur YouTube durant l'événement.
Cliquer sur l'icône pour visionner la vidéo du match correspondant.
[Consulter la playlist complète sur YouTube](https://www.youtube.com/playlist?list=PLJd3CiuQpT1z9fcnwxogYAnv6D_0vftHb).

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			<th>Visionner</th>
			{% for team in site.data.resultats_2017.teams %}
			<th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
	    {% for match in site.data.resultats_2017.matches %}
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
			{% for team in site.data.resultats_2017.teams %}
			{% assign team_key = team[0] %}
			{% assign table = match.teams[team_key] %}
	        {% if table %}
	        <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            <a href="https://fll-scoreboard-2016.robots-ju.ch/#{{ table.scoreboard | jsonify | xml_escape }}" class="js-scoreboard">{{ table.score }}</a>
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
