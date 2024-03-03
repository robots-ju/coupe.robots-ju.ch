---
layout: widepage
title: Résultats 2024
permalink: /resultats/2024
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à tous pour vos excellents résultats !

<i class="fa fa-youtube-play" aria-hidden="true"></i>
La rediffusion du [live stream](https://www.youtube.com/watch?v=zFT-6BUkNtk) est disponible sur YouTube.
Une rediffusion en plus haute qualité suivra.

## Classement général

| # | Équipe                    | Points |
|---|---------------------------|--------|
| 1 | **Back to the Block**     | 76     |
| 2 | **Saint-Roch I**          | 75     |
| 3 | **Master Pare_chocs.JU**  | 73     |
| 4 | CFR’s Brik                | 70     |
| 5 | Phoenix                   | 50     |
| 6 | Jurartiste                | 36     |
| 7 | Patatartiner jurassiennes | 32     |

## Classement Robot-Game

| # | Équipe                    | Qualifications | Demi-finales | Finales |
|---|---------------------------|----------------|--------------|---------|
| 1 | **Saint-Roch I**          | 895            | 340          | 760     |
| 2 | CFR’s Brik                | 680            | 340          | 465     |
| 3 | Back to the Block         | 745            | 325          |         |
| 4 | Phoenix                   | 600            | 250          |         |
| 5 | Master Pare_chocs.JU      | 410            |              |         |
| 6 | Jurartiste                | 360            |              |         |
| 7 | Patatartiner jurassiennes | 290            |              |         |

## Classement Live Challenge

| # | Équipe                    | Points |
|---|---------------------------|--------|
| 1 | **Master Pare_chocs.JU**  | 22     |
| 2 | Back to the Block         | 15     |
| 3 | CFR’s Brik                | 14     |
| 4 | Saint-Roch I              | 11     |
| 5 | Phoenix                   | 7      |
| 5 | Patatartiner jurassiennes | 7      |
| 5 | Jurartiste                | 7      |

## Esprit d'équipe

Le jury a attribué le prix d'esprit d'équipe à **CFR’s Brik**.

## Détail des matches du Robot-Game

Le tableau présente les 25 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			{% for team in site.data.resultats_2024.teams %}
			<th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
	    {% for match in site.data.resultats_2024.matches %}
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
			{% for team in site.data.resultats_2024.teams %}
			{% assign team_key = team[0] %}
			{% assign table = match.teams[team_key] %}
	        {% if table %}
	        <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            {% if table.scoreboard %}
              <a href="https://fll-scoreboard.robots-ju.ch/masterpiece#{{ table.scoreboard }}" class="js-scoreboard">{{ table.score }}</a>
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
