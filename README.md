# Lire le contenu HTML stylisé déjà modifié
html_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_stylise.html"
with open(html_path, "r", encoding="utf-8") as file:
    html_content = file.read()

# Définir le bloc à insérer dans le <body> pour ajouter une scène cinématique + musique
cinematic_block = """
<!-- Cinématique d'ouverture -->
<div class="section">
  <h2 class="mystic">Cinématique d'Ouverture</h2>
  <p>Un voile de brume s'étend sur le centre commercial déserté. Les néons clignotants projettent des ombres étranges, tandis que des murmures imperceptibles résonnent entre les murs.</p>
  <video width="100%" controls autoplay muted loop style="margin-top: 20px;">
    <source src="cinematique_intro.mp4" type="video/mp4">
    Votre navigateur ne supporte pas la vidéo.
  </video>
</div>

<!-- Musique d'ambiance -->
<audio autoplay loop>
  <source src="musique_ambiance.mp3" type="audio/mpeg">
  Votre navigateur ne supporte pas l'audio.
</audio>
"""

# Ajouter le bloc cinématique juste avant la fermeture de la balise </body>
if "</body>" in html_content:
    html_content_with_cinematic = html_content.replace("</body>", cinematic_block + "\n</body>")
else:
    html_content_with_cinematic = html_content + cinematic_block

# Sauvegarder la nouvelle version avec les cinématiques et musique
final_html_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_complet.html"
with open(final_html_path, "w", encoding="utf-8") as file:
    file.write(html_content_with_cinematic)

final_html_path
