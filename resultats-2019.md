---
layout: widepage
title: Résultats 2019
permalink: /resultats/2019
banner_image: /media/banners/area.jpg
---

<div class="results-page" markdown="1">

<i class="fa fa-trophy" aria-hidden="true"></i>
Bravo à toutes les équipes pour vos excellents résultats !

Retrouvez les photos de la journée [sur notre album Flickr](https://www.flickr.com/photos/robots-ju/sets/72157706162685841)

## Classement général

|  # | Équipe            | Points |
| -- | ----------------- | ------ |
|  1 | **Jur'apollo 18** | 75     |
|  2 | **Capricorns**    | 69     |
|  3 | **Deep Mind**     | 57     |
|  4 | Jurapiter         | 41     |
|  5 | Saint Roch I      | 40     |
|  6 | Jurastronaute     | 31     |
|  7 | Saint Roch 3      | 30     |
|  8 | Falcon 9          | 28     |
|  9 | La 5              | 23     |
| 10 | Saint Roch II     | 19     |

## Classement Robot-Game

|  # | Équipe         | Manches | Demi-finales | Finales |
| -- | -------------- | ------- | ------------ | ------- |
|  1 | **Capricorns** | 650     | 173          | 522     |
|  2 | Jur'apollo 18  | 331     | 148          | 151     |
|  3 | Deep Mind      | 243     | 140          |
|  4 | Jurapiter      | 306     | 130          |
|  5 | Falcon 9       | 230     |
|  6 | La 5           | 172     |
|  7 | Jurastronaute  | 153     |
|  8 | Saint Roch 3   | 143     |
|  9 | Saint Roch I   | 141     |
| 10 | Saint Roch II  | 118     |

## Classement Live Challenge

|  # | Équipe            | Points |
| -- | ----------------- | ------ |
|  1 | **Jur'apollo 18** | 29     |
|  2 | Deep Mind         | 22     |
|  3 | Saint Roch I      | 17     |
|  4 | Capricorns        | 11     |
|  - | Jurastronaute     | 11     |
|  - | Saint Roch 3      | 11     |
|  7 | Jurapiter         | 10     |
|  8 | Falcon 9          | 6      |
|  - | La 5              | 6      |
|  - | Saint Roch II     | 6      |

## Détail des matches du Robot-Game

Le tableau présente les 49 matches (qualifications et finales) disputés lors de la Coupe.
Les 2 meilleurs matchs de qualification de chaque équipe (retenus pour le classement) sont mis en évidence.

<i class="fa fa-youtube-play" aria-hidden="true"></i>
Un replay avec commentaire de chaque match a été extrait depuis la [diffusion live sur YouTube](https://www.youtube.com/watch?v=PReKHsXvmO4) durant l'événement.
Cliquer sur l'icône pour visionner la vidéo du match correspondant.
[Consulter la playlist complète sur YouTube](https://www.youtube.com/playlist?list=PLJd3CiuQpT1wA8gVCHNc3w20uGFMI93P6).

<i class="fa fa-mouse-pointer" aria-hidden="true"></i>
Cliquer sur un score pour voir le détail des missions effectuées.

<table>
	<thead>
		<tr>
			<th>Match</th>
			<th>Heure</th>
			<th>Visionner</th>
			{% for team in site.data.resultats_2019.teams %}
			<th class="small-title">{{ team[1] }}</th>
			{% endfor %}
		</tr>
	</thead>
	<tbody>
	    {% for match in site.data.resultats_2019.matches %}
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
			{% for team in site.data.resultats_2019.teams %}
			{% assign team_key = team[0] %}
			{% assign table = match.teams[team_key] %}
	        {% if table %}
	        <td title="Match {{ match.number }} {{ match.time }}, table {{ table.table }}, équipe {{ team[1] }}{% if table.best %} (meilleur match de qualification){% endif %}"{% if table.best %} class="best-score"{% endif %}>
	            {% if table.scoreboard %}
              <a href="https://fll-scoreboard-2018.robots-ju.ch/#{{ table.scoreboard | jsonify | xml_escape }}" class="js-scoreboard">{{ table.score }}</a>
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
