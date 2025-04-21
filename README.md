<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Les Tricheurs des Réalités - Chapitre 1</title>
  <link href="https://fonts.googleapis.com/css2?family=EB+Garamond&family=UnifrakturCook:wght@700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'EB Garamond', serif;
      background-color: #0b0b0b;
      color: #e0e0e0;
      line-height: 1.6;
      padding: 20px;
    }
    h1, h2, h3, .mystic {
      font-family: 'UnifrakturCook', cursive;
      color: #caa96a;
      letter-spacing: 1px;
      text-shadow: 1px 1px 4px #000;
    }
    .mystic-small {
      font-family: 'UnifrakturCook', cursive;
      font-size: 1.2em;
      color: #a0865e;
    }
    p {
      margin-bottom: 1.5em;
    }
    .section {
      margin-bottom: 3em;
    }
    .cinematic {
      color: #f4f4f4;
      background-color: #333;
      padding: 20px;
      margin-top: 20px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.8);
    }
    .choice {
      margin-top: 10px;
      padding: 10px;
      background-color: #444;
      border-radius: 5px;
      cursor: pointer;
    }
    .inventory {
      margin-top: 20px;
    }
    .status {
      margin-top: 20px;
      color: #a0a0a0;
    }
    #combat-log {
      margin-top: 20px;
      background-color: #222;
      padding: 10px;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <h1 class="mystic">Les Tricheurs des Réalités - Chapitre 1</h1>

  <!-- Cinématique d'introduction -->
  <div class="cinematic">
    <h2 class="mystic">Prologue : L'Appel des Ombres</h2>
    <p>
      Sorane s'aventure dans le centre commercial abandonné, une atmosphère étrange et oppressante enveloppe les lieux. Les murs sont recouverts de graffiti et de symboles mystiques, témoignant de l'activité étrange qui s'y déroule.
    </p>
    <p>
      <strong>Une ombre se profile.</strong> Des créatures surgissent dans les recoins sombres, des monstres d'ombre aux yeux luisants. Sorane se prépare à affronter l'inconnu.
    </p>
    <audio controls autoplay>
      <source src="musique_intro.mp3" type="audio/mp3">
      Votre navigateur ne supporte pas la lecture audio.
    </audio>
  </div>

  <!-- Choix du joueur -->
  <div class="section">
    <h3 class="mystic">Choisis ton action :</h3>
    <div class="choice" onclick="choisirCombat()">Affronter les monstres</div>
    <div class="choice" onclick="choisirFuir()">Fuir dans les égouts</div>
  </div>

  <!-- Scène cinématique du combat ou de la fuite -->
  <div class="cinematic" id="combat-scene" style="display:none;">
    <h2 class="mystic">Le Combat Commence</h2>
    <p>
      Sorane brandit sa batte de baseball, prêt à affronter les créatures d'ombre qui l'entourent. Les monstres grognent et se précipitent sur lui. Le combat est inévitable.
    </p>
    <audio controls autoplay>
      <source src="musique_combat.mp3" type="audio/mp3">
    </audio>
    <button onclick="combat()">Lancer le combat</button>
  </div>

  <div class="cinematic" id="fuite-scene" style="display:none;">
    <h2 class="mystic">La Fuite dans les Égouts</h2>
    <p>
      Sorane prend une décision risquée et plonge dans les égouts sombres, échappant aux monstres. Mais des bruits étranges résonnent dans les tunnels. D'autres créatures rôdent, prêtes à surgir de l'ombre.
    </p>
    <audio controls autoplay>
      <source src="musique_fuite.mp3" type="audio/mp3">
    </audio>
  </div>

  <!-- Statut du joueur -->
  <div class="status">
    <h3 class="mystic">Statut du Joueur</h3>
    <p id="player-status">Santé: <span id="health">100</span> | Magie: <span id="magic">50</span> | Endurance: <span id="endurance">75</span></p>
  </div>

  <!-- Inventaire -->
  <div class="inventory">
    <h3 class="mystic">Inventaire</h3>
    <ul>
      <li>Bat de baseball (arme de base)</li>
      <li>Potion de guérison (utiliser pour récupérer de la santé)</li>
      <li>Masque d'ombre (augmente la discrétion et la résistance aux ténèbres)</li>
    </ul>
  </div>

  <!-- Combat Log -->
  <div id="combat-log"></div>

  <!-- Quêtes secondaires -->
  <div class="section">
    <h3 class="mystic">Quêtes secondaires disponibles :</h3>
    <ul>
      <li>Explorer le centre commercial pour des ressources perdues.</li>
      <li>Rencontrer un survivant caché et obtenir une arme légendaire.</li>
    </ul>
  </div>

  <!-- Boss caché -->
  <div class="section">
    <h3 class="mystic">Boss Caché :</h3>
    <p>
      Un boss puissant se cache dans les égouts, une créature mythologique, jadis scellée. La défaite de ce monstre pourrait changer le cours de l'histoire...
    </p>
  </div>

  <!-- Système de Sauvegarde -->
  <div class="section">
    <button onclick="sauvegarder()">Sauvegarder le jeu</button>
    <button onclick="charger()">Charger la sauvegarde</button>
  </div>

  <script>
    // Variables du joueur
    let health = 100;
    let magic = 50;
    let endurance = 75;

    // Fonction de choix d'action
    function choisirCombat() {
      document.getElementById("combat-scene").style.display = "block";
      document.getElementById("fuite-scene").style.display = "none";
    }

    function choisirFuir() {
      document.getElementById("fuite-scene").style.display = "block";
      document.getElementById("combat-scene").style.display = "none";
    }

    // Fonction de combat
    function combat() {
      let monsterHealth = 50;  // Santé du monstre
      let damage = Math.floor(Math.random() * 20) + 10;  // Dégâts du joueur

      // Attaque
      monsterHealth -= damage;
      health -= Math.floor(Math.random() * 15);  // Dégâts du monstre

      // Mise à jour du statut
      document.getElementById("health").innerText = health;
      let combatLog = `Vous avez infligé ${damage} de dégâts. Monstre restant: ${monsterHealth} HP.`;
      document.getElementById("combat-log").innerText = combatLog;

      if (health <= 0) {
        alert("Vous êtes mort. Fin du jeu.");
        resetGame();
      } else if (monsterHealth <= 0) {
        alert("Le monstre est vaincu !");
        resetGame();
      }
    }

    // Fonction de sauvegarde
    function sauvegarder() {
      localStorage.setItem
