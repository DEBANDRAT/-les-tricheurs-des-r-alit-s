# Je vais recréer le processus pour insérer les scènes cinématiques dans le fichier HTML, en prenant en compte la perte de session.

# Définir le contenu cinématique à insérer
cinematic_block = """
<section class="cinematic">
  <h2>Cinématique - L'Apparition</h2>
  <p>Une scène d'une intensité rare, où les personnages se retrouvent face à un ennemi mystérieux, un monstre des ténèbres, surgissant des ombres. La lumière vacille et l'air semble devenir plus épais. Les héros se préparent au combat alors que le monstre avance lentement, ses yeux brillants dans la pénombre...</p>
  <p>La tension est palpable. Les premiers coups pleuvent, mais le monstre semble résister. Les héros doivent ruser pour l'affaiblir. Un combat de volonté et de stratégie s'engage, un moment clé de l'intrigue qui les mènera à la prochaine étape de leur quête...</p>
</section>
"""

# Lire le contenu du fichier HTML actuel
html_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_stylise.html"
with open(html_path, "r", encoding="utf-8") as file:
    html_content = file.read()

# Vérifier si l'intrigue principale existe et insérer les scènes cinématiques à cet endroit
if "<h1>Intrigue Principale</h1>" in html_content:
    # Insérer le bloc cinématique juste après l'intrigue principale
    html_content_with_cinematic = html_content.replace("<h1>Intrigue Principale</h1>", f"<h1>Intrigue Principale</h1>{cinematic_block}", 1)
else:
    # Si l'intrigue principale n'est pas trouvée, ajouter une section avec l'intrigue principale et la cinématique
    html_content_with_cinematic = f"<h1>Intrigue Principale</h1>{cinematic_block}\n{html_content}"

# Sauvegarder le fichier HTML mis à jour
updated_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_avec_cinematique.html"
with open(updated_path, "w", encoding="utf-8") as file:
    file.write(html_content_with_cinematic)

updated_path
Cell In[1], line 14
     12 # Lire le contenu du fichier HTML actuel
     13 html_path = "/mnt/data/chapitre1_les_tricheurs_des_realites_stylise.html"
---> 14 with open(html_path, "r", encoding="utf-8") as file:
     15     html_content = file.read()
     17 # Vérifier si l'intrigue principale existe et insérer les scènes cinématiques à cet endroit

File ~/.local/lib/python3.11/site-packages/IPython/core/interactiveshell.py:324, in _modified_open(file, *args, **kwargs)
    317 if file in {0, 1, 2}:
    318     raise ValueError(
    319         f"IPython won't let you open fd={file} by default "
    320         "as it is likely to crash IPython. If you know what you are doing, "
    321         "you can use builtins' open."
    322     )
--> 324 return io_open(file, *args, **kwargs)

FileNotFoundError: [Errno 2] No such file or directory: '/mnt/data/chapitre1_les_tricheurs_des_realites_stylise.html'
