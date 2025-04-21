<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Terminal des Tricheurs - Catalogue d'Armes</title>
  <style>
    body {
      background: #121212;
      color: #00FF00;
      font-family: 'Courier New', Courier, monospace;
      margin: 0;
      padding: 0;
    }
    h1 {
      text-align: center;
      margin-top: 20px;
    }
    #hall {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .menu {
      display: flex;
      flex-direction: column;
      gap: 20px;
      text-align: center;
    }
    .menu button {
      background-color: #333;
      color: #00FF00;
      border: 1px solid #444;
      padding: 15px;
      font-size: 18px;
      cursor: pointer;
      transition: 0.3s;
    }
    .menu button:hover {
      background-color: #444;
    }
    .weapons-section {
      display: flex;
      flex-direction: column;
      gap: 1.5em;
      margin-top: 2em;
    }
    .weapon {
      background-color: #333;
      border: 1px solid #444;
      padding: 20px;
      text-align: center;
      font-size: 18px;
      cursor: pointer;
      transition: 0.3s;
    }
    .weapon:hover {
      background-color: #444;
    }
    .weapon-details {
      margin-top: 1em;
      background-color: #222;
      padding: 20px;
      border: 1px solid #444;
      display: none;
      text-align: center;
    }
    .weapon-details.active {
      display: block;
    }
  </style>
</head>
<body>

  <div id="hall">
    <h1>Terminal des Tricheurs - Catalogue d'Armes</h1>
    <div class="menu">
      <button onclick="voirArmes()">📜 Voir le Catalogue d'Armes</button>
      <button onclick="accéderAuHall()">🖥 Retour au Hall Principal</button>
    </div>

    <div id="weapons" class="weapons-section" style="display: none;">
      <div class="weapon" onclick="afficherDetails('batte')">⚾ Batte de Baseball</div>
      <div class="weapon" onclick="afficherDetails('pistolet')">🔫 Pistolet à Répétition</div>
      <div class="weapon" onclick="afficherDetails('arc')">🏹 Arc Magique</div>
    </div>

    <div id="weapon-details" class="weapon-details"></div>
  </div>

  <script>
    // Liste des armes avec leurs détails
    const armes = {
      batte: {
        nom: "Batte de Baseball",
        type: "Mêlée",
        dégâts: "50",
        portée: "Courte",
        description: "Une batte solide, idéale pour les attaques rapprochées."
      },
      pistolet: {
        nom: "Pistolet à Répétition",
        type: "À distance",
        dégâts: "30",
        portée: "Moyenne",
        description: "Un pistolet semi-automatique efficace pour les combats à distance."
      },
      arc: {
        nom: "Arc Magique",
        type: "À distance",
        dégâts: "40",
        portée: "Longue",
        description: "Un arc enchanté, capable de tirer des flèches magiques puissantes."
      }
    };

    function voirArmes() {
      document.getElementById('weapons').style.display = 'flex';
    }

    function afficherDetails(arme) {
      const details = armes[arme];
      const detailsSection = document.getElementById('weapon-details');
      
      detailsSection.innerHTML = `
        <h2>${details.nom}</h2>
        <p><strong>Type :</strong> ${details.type}</p>
        <p><strong>Dégâts :</strong> ${details.dégâts}</p>
        <p><strong>Portée :</strong> ${details.portée}</p>
        <p><strong>Description :</strong> ${details.description}</p>
        <button onclick="équiperArme('${arme}')">Équiper cette arme</button>
      `;

      detailsSection.classList.add('active');
    }

    function équiperArme(arme) {
      alert(`L'arme ${armes[arme].nom} a été équipée.`);
      document.getElementById('weapon-details').classList.remove('active');
    }

    function accéderAuHall() {
      alert("Retour au Hall Principal.");
      window.location.href = 'hall.html';  // Change ce lien si tu veux un redirection vers un autre fichier
    }
  </script>

</body>
</html>
