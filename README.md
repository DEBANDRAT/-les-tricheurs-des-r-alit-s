# Lecture du fichier HTML stylisé existant
html_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_stylise.html"
with open(html_path, "r", encoding="utf-8") as file:
    html_content = file.read()

# Bloc HTML à insérer pour une scène cinématique et une musique de fond
cinematic_music_block = """
<!-- Scène cinématique (exemple d'introduction) -->
<div class="section">
  <h2 class="mystic">Scène d'ouverture</h2>
  <p class="mystic-small">Un ciel de cendres recouvre la ville. Des ombres rampent dans les ruelles abandonnées tandis qu’une voix lointaine murmure les secrets d’un monde oublié. Le silence est brisé par un souffle…</p>
</div>

<!-- Musique de fond -->
<audio controls autoplay loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/28/audio_6fa119dd53.mp3?filename=dark-suspense-ambient-105788.mp3" type="audio/mpeg">
  Votre navigateur ne supporte pas l'audio HTML5.
</audio>
"""

# Ajouter le bloc juste après la balise <body>
html_content_updated = html_content.replace("<body>", f"<body>{cinematic_music_block}", 1)

# Sauvegarder la nouvelle version du fichier HTML
updated_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_cine_musique.html"
with open(updated_path, "w", encoding="utf-8") as file:
    file.write(html_content_updated)

updated_path
