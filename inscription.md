---
layout: page
title: Inscription
permalink: /inscription
banner_image: /media/banners/ev3.jpg
section_popup: true
---

Utilisez ce formulaire pour inscrire votre équipe à la Coupe Robots-JU.
Nous prendrons contact avec vous.

Les inscriptions sont ouvertes jusqu'au 15 avril 2016.

<form action="https://forms.robots-ju.ch/forms/coupe-inscription" method="post">
	<div class="form-table">
		<div class="form-group">
			<label for="team_name">Nom de l'équipe <span class="required-field">*</span></label>
			<input class="form-control" type="text" name="team_name" id="team_name" required>
		</div>

		<div class="form-group">
			<label for="coach_name">Nom du coach <span class="required-field">*</span></label>
			<input class="form-control" type="text" name="coach_name" id="coach_name" required>
		</div>

		<div class="form-group">
			<label for="address">Adresse complète <span class="required-field">*</span></label>
			<textarea class="form-control" name="address" id="address" required></textarea>
		</div>

		<div class="form-group">
			<label for="email">Email <span class="required-field">*</span></label>
			<input class="form-control" type="email" name="email" id="email" required>
		</div>

		<div class="form-group">
			<label for="phone">Téléphone</label>
			<input class="form-control" type="text" name="phone" id="phone">
		</div>

		<div class="form-group">
			<label for="other_coach">Coach(s) adjoint(s)</label>
			<textarea class="form-control" name="other_coach" id="other_coach"></textarea>
		</div>

		<div class="form-group">
			<label for="total_people">Nb total de personnes (y-c. coach/s) <span class="required-field">*</span></label>
			<input class="form-control" type="number" min="0" name="total_people" id="total_people" required>
		</div>

		<div class="form-group">
			<label for="comments">Commentaires</label>
			<textarea class="form-control" name="comments" id="comments"></textarea>
		</div>
	</div>

	<p>La finance d’inscription de Frs {{ site.concours.finance_inscription }}.- est à verser sur le compte:</p>

	<pre>Robots-JU, BCJ, CH46 0078 9042 5634 0652 8, mention: Coupe JU</pre>

	<div class="form-group actions">
		<button class="btn" type="submit">Envoyer</button>
	</div>
</form>