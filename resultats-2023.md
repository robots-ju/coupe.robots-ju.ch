---
layout: widepage
title: Résultats 2023
permalink: /resultats/2023
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à tous pour vos excellents résultats !

<i class="fa fa-youtube-play" aria-hidden="true"></i>
La rediffusion du [live stream du matin](https://www.youtube.com/watch?v=8hzC9Pi_qqg) (Live Challenge)
et du [live stream de l'après-midi](https://www.youtube.com/watch?v=cQJSnrGv_Aw) (Robot Game + Remise des prix) sont
disponibles sur YouTube.

## Classement général

| # | Équipe | Points |
| - | ------------------------ | ------ |
| 1 | **Ultra_powered.ju**     | 84 |
| 2 | **Jur'arc électrique**   | 80 |
| 3 | **Junior Smilebots**     | 76 |
| 4 | Back to the Block | 68 |
| 5 | Capricorns | 64 |
| 6 | Phoenix | 48 |
| 7 | CFR's Blok | 39 |
| 8 | Les Patates jurassiennes | 31 |

## Classement Robot-Game

| # | Équipe | Manches | Demi-finales | Finales |
| - | ------------------------ | ------- | ------------ | ------- |
| 1 | **Junior Smilebots**     | 680 | 350 | 655 |
| 2 | Capricorns | 560 | 320 | 635 |
| 3 | Back to the Block | 555 | 245 |
| 4 | Phoenix | 510 | 110 |
| 5 | Ultra_powered.ju | 465 |
| 6 | Jur'arc électrique | 445 |
| 7 | CFR's Blok | 350 |
| 8 | Les Patates jurassiennes | 245 |

## Classement Live Challenge

| # | Équipe | Points |
| - | ------------------------ | ------ |
| 1 | **Ultra_powered.ju**     | 31 |
| 2 | Jur'arc électrique | 29 |
| 3 | Back to the Block | 17 |
| 4 | Junior Smilebots | 16 |
| 5 | Capricorns | 14 |
| 6 | CFR's Blok | 8 |
| - | Les Patates jurassiennes | 8 |
| 8 | Phoenix | 6 |

## Esprit d'équipe

Le jury a attribué le prix d'esprit d'équipe à **Les Patates jurassiennes**.

## Détail des matches du Robot-Game

Le tableau présente les 40 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			<th>Visionner</th>
			{% for team in site.data.resultats_2023.teams %}
			<th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
	    {% for match in site.data.resultats_2023.matches %}
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
	        <td><a title="Replay" href="https://www.youtube.com/watch?v=cQJSnrGv_Aw&t={{ match.youtube }}s" data-youtube="{{ match.youtube }}">
	            <i class="fa fa-youtube-play" aria-hidden="true"></i>
	            Replay
            </a></td>
			{% for team in site.data.resultats_2023.teams %}
			{% assign team_key = team[0] %}
			{% assign table = match.teams[team_key] %}
	        {% if table %}
	        <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            {% if table.scoreboard %}
              <a href="https://fll-scoreboard.robots-ju.ch/super-powered#{{ table.scoreboard }}" class="js-scoreboard">{{ table.score }}</a>
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

    [].forEach.call(document.querySelectorAll('[data-youtube]'), function(a) {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            oc.innerHTML = '<iframe width="853" height="480" src="https://www.youtube.com/embed/cQJSnrGv_Aw?start=' + a.dataset.youtube + '" frameborder="0" allowfullscreen></iframe>';
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
