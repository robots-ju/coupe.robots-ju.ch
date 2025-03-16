---
layout: widepage
title: Résultats 2025
permalink: /resultats/2025
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à tous pour vos excellents résultats !

<i class="fa fa-youtube-play" aria-hidden="true"></i>
La rediffusion du [live stream](https://www.youtube.com/watch?v=P2NBR2CKaHA) est disponible sur YouTube.

## Catégorie Explorateur

| Prix                     | Équipe                            |
|--------------------------|-----------------------------------|
| Meilleur Poster          | Les robots marins étoiles du Jura |
| Meilleure Maquette       | Les régalecs éclairs du Jura XXL  |
| Meilleur Esprit d'équipe | Les monstres marins du Jura       |

## Catégorie Ingénieur

### Classement général

| #  | Équipe                  | Points |
|----|-------------------------|--------|
| 1  | **Yellow_Submarine.JU** | 92     |
| 2  | **Brik’ception**        | 87     |
| 3  | **Saint Roch’n’Roll**   | 80     |
| 4  | RoboHunter              | 49     |
| 5  | Jurabysses              | 37     |
| 6  | Poséidon.ju             | 36     |
| 7  | LET’S GO                | 34     |
| 8  | www.patataquatique.ju   | 32     |
| 9  | L’équi-pain jurassien   | 26     |
| 10 | AquaJura                | 24     |

### Classement Robot-Game

| #  | Équipe                | Qualifications | Demi-finales | Finales |
|----|-----------------------|----------------|--------------|---------|
| 1  | **Saint Roch’n’Roll** | 795            | 325          | 860     |
| 2  | Yellow_Submarine.JU   | 670            | 260 (235*)   | 630     |
| 3  | RoboHunter            | 585            | 260 (200*)   |         |
| 4  | Brik’ception          | 680            | 210          |         |
| 5  | LET’S GO              | 420            |              |         |
| 6  | L’équi-pain jurassien | 410            |              |         |
| 7  | Jurabysses            | 400            |              |         |
| 8  | AquaJura              | 355            |              |         |
| 9  | Poséidon.ju           | 320            |              |         |
| 10 | www.patataquatique.ju | 315            |              |         |

\* match de barrage

### Classement Live Challenge

| #  | Équipe                  | Points |
|----|-------------------------|--------|
| 1  | **Yellow_Submarine.JU** | 25     |
| 2  | Brik’ception            | 22     |
| 3  | Saint Roch’n’Roll       | 15     |
| 4  | Poséidon.ju             | 8      |
| 5  | RoboHunter              | 6      |
|    | www.patataquatique.ju   | 6      |
|    | Jurabysses              | 6      |
| 8  | LET’S GO                | 4      |
| 9  | AquaJura                | 1      |
| 10 | L’équi-pain jurassien   | 0      |

### Esprit d'équipe

Le jury a attribué le prix d'esprit d'équipe à **LET’s GO**.

### Détail des matches du Robot-Game

Le tableau présente les 50 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

Un match de barrage a dû être organisé pour départager l'égalité durant la demi-finale.

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			{% for team in site.data.resultats_2025.teams %}
			  <th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
    {% for match in site.data.resultats_2025.matches %}
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
			  {% for team in site.data.resultats_2025.teams %}
			    {% assign team_key = team[0] %}
			    {% assign table = match.teams[team_key] %}
	        {% if table %}
	          <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            {% if table.scoreboard %}
              <a href="https://fll-scoreboard.robots-ju.ch/submerged#{{ table.scoreboard }}" class="js-scoreboard">{{ table.score }}</a>
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
