<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Combat RPG Gothique Urbain</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #121212;
      color: white;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    #game {
      background-color: #333;
      border-radius: 10px;
      padding: 20px;
      width: 60%;
      max-width: 800px;
      box-shadow: 0 0 10px rgba(255, 255, 255, 0.2);
    }

    h1 {
      text-align: center;
      font-size: 2rem;
      margin-bottom: 20px;
    }

    #status {
      display: flex;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    #status h3 {
      margin-bottom: 10px;
    }

    .character-image {
      width: 100px;
      height: 100px;
      object-fit: cover;
      border-radius: 50%;
      margin-bottom: 10px;
    }

    button {
      background-color: #444;
      color: white;
      border: none;
      padding: 10px;
      width: 45%;
      margin: 10px 2.5%;
      cursor: pointer;
      border-radius: 5px;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #666;
    }

    #log {
      margin-top: 20px;
      max-height: 150px;
      overflow-y: auto;
    }

    #combat-log ul {
      list-style-type: none;
      padding-left: 0;
    }

    #combat-log li {
      margin: 5px 0;
    }
  </style>
</head>
<body>
  <div id="game">
    <h1>Combat RPG - Gothique Urbain</h1>

    <!-- Statut du joueur -->
    <div id="status">
      <div id="player-status">
        <h3>Joueur</h3>
        <p id="player-health">Santé: 100</p>
        <img id="player-image" src="images/player.jpg" alt="Joueur" class="character-image">
        <p id="player-weapon">Arme: Épée de l'ombre</p>
      </div>

      <!-- Statut de l'ennemi -->
      <div id="enemy-status">
        <h3>Ennemi</h3>
        <p id="enemy-health">Santé: 50</p>
        <img id="enemy-image" src="images/monster.jpg" alt="Ennemi" class="character-image">
        <p id="enemy-weapon">Arme: Lance de feu</p>
      </div>
    </div>

    <!-- Boutons pour les actions -->
    <div>
      <button id="attackBtn">Attaquer</button>
      <button id="checkResistancesBtn">Vérifier Résistances</button>
    </div>

    <!-- Journal de combat -->
    <div id="log">
      <h3>Journal de Combat</h3>
      <ul id="combat-log-ul"></ul>
    </div>
  </div>

  <script>
    // Script pour gérer le combat

    document.addEventListener('DOMContentLoaded', function () {
      const attackBtn = document.getElementById('attackBtn');
      const checkResistancesBtn = document.getElementById('checkResistancesBtn');
      const playerHealth = document.getElementById('player-health');
      const enemyHealth = document.getElementById('enemy-health');
      const combatLogUl = document.getElementById('combat-log-ul');

      let playerHealthPoints = 100;
      let enemyHealthPoints = 50;

      // Fonction pour afficher un message dans le journal
      function updateCombatLog(message) {
        const logItem = document.createElement('li');
        logItem.textContent = message;
        combatLogUl.appendChild(logItem);
        combatLogUl.scrollTop = combatLogUl.scrollHeight; // Pour faire défiler le journal
      }

      // Fonction pour attaquer
      function attack() {
        const damage = Math.floor(Math.random() * 20) + 1; // Dommages aléatoires entre 1 et 20
        enemyHealthPoints -= damage;
        if (enemyHealthPoints <= 0) {
          enemyHealthPoints = 0;
          updateCombatLog(`Le joueur attaque ! L'ennemi est vaincu.`);
        } else {
          updateCombatLog(`Le joueur attaque ! L'ennemi perd ${damage} points de santé.`);
        }
        enemyHealth.textContent = `Santé: ${enemyHealthPoints}`;
        checkGameOver();
      }

      // Fonction pour vérifier les résistances
      function checkResistances() {
        updateCombatLog("Résistances du joueur: Physique: 50%, Magique: 30%, Élémentaire: 20%");
        updateCombatLog("Résistances de l'ennemi: Physique: 40%, Magique: 10%, Élémentaire: 50%");
      }

      // Fonction pour gérer la fin du jeu
      function checkGameOver() {
        if (playerHealthPoints <= 0) {
          updateCombatLog("Le joueur a été vaincu !");
          attackBtn.disabled = true;
          checkResistancesBtn.disabled = true;
        } else if (enemyHealthPoints <= 0) {
          updateCombatLog("L'ennemi a été vaincu !");
          attackBtn.disabled = true;
          checkResistancesBtn.disabled = true;
        }
      }

      // Événements des boutons
      attackBtn.addEventListener('click', attack);
      checkResistancesBtn.addEventListener('click', checkResistances);
    });
  </script>
</body>
</html>
