<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Terminal de Commandement</title>
  <style>
    body {
      background-color: #000;
      color: #0f0;
      font-family: 'Courier New', Courier, monospace;
      padding: 2em;
    }
    .console {
      background-color: #111;
      border: 1px solid #0f0;
      padding: 1em;
      margin-top: 1em;
      height: 400px;
      overflow-y: auto;
    }
    input {
      background-color: #000;
      color: #0f0;
      border: none;
      width: 100%;
      font-size: 1em;
      font-family: inherit;
    }
  </style>
</head>
<body>
  <h1>🖥 Terminal de Commandement</h1>
  <p>Bienvenue, utilisateur non-identifié. Entrez une commande pour interagir avec les systèmes secrets de l’Omnivers de la Vierge.</p>
  <div class="console" id="console">
    > help : liste des commandes disponibles<br>
  </div>
  <input type="text" id="commande" placeholder="Entrez une commande..." onkeydown="if(event.key==='Enter'){executerCommande()}" autofocus>

  <script>
    const consoleDiv = document.getElementById('console');
    const commandeInput = document.getElementById('commande');

    const items = {
      "blade_omega": {
        nom: "Lame Omega",
        description: "Épée capable de trancher les réalités. +15 Dégâts",
        rarete: "légendaire"
      },
      "neuro_cloak": {
        nom: "Cape Neurophantom",
        description: "Rend invisible aux entités du Megavers. +30% esquive",
        rarete: "épique"
      },
      "injector_x": {
        nom: "Injecteur X-Vita",
        description: "Restaure toute l'énergie vitale. Utilisable une fois par mission.",
        rarete: "rare"
      }
    };

    const zones = {
      "zone_1": "Égouts de Terreurville",
      "zone_2": "Chapiteau Maudit",
      "zone_3": "Laboratoire Fantôme",
      "hub": "Hall Central de Commandement"
    };

    let inventaire = [];
    let vie = 100;

    function afficher(message) {
      consoleDiv.innerHTML += `> ${message}<br>`;
      consoleDiv.scrollTop = consoleDiv.scrollHeight;
    }

    function afficherItem(code) {
      const item = items[code];
      if (item) {
        inventaire.push(item);
        afficher(`Objet récupéré : ${item.nom} \nDescription : ${item.description} \nRareté : ${item.rarete}`);
      } else {
        afficher("Objet inconnu.");
      }
    }

    function combat() {
      const degats = Math.floor(Math.random() * 25) + 5;
      vie -= degats;
      if (vie <= 0) {
        afficher(`⚠️ Vous avez été vaincu par une entité du Megavers... Votre terminal redémarre.`);
        vie = 100;
        inventaire = [];
      } else {
        afficher(`💥 Attaque ennemie ! Dégâts subis : ${degats}. Points de vie restants : ${vie}`);
      }
    }

    function executerCommande() {
      const cmd = commandeInput.value.trim().toLowerCase();
      afficher(cmd);
      commandeInput.value = '';

      switch(cmd) {
        case 'help':
          afficher('Commandes : scan, fichier sorane, fichier anomalies, statut multivers, inventaire, loot 1-3, combat, explorer zone_1-3, hub');
          break;
        case 'scan':
          afficher('Analyse des réalités... Anomalies détectées dans le Megavers. Flux instable.');
          break;
        case 'fichier sorane':
          afficher('Accès au dossier : Sorane\nNom : Sorane Uriel\nStatut : fugitif\nObservation : sujet porteur d’une anomalie classée Yoline.');
          break;
        case 'fichier anomalies':
          afficher('Anomalies enregistrées : Ombres rampantes, Clown X-473, Nexus inconnu dans les égouts.');
          break;
        case 'statut multivers':
          afficher('Synchronisation des mondes...\n- Vierge : actif\n- Megavers : instable\n- Archiverses : accès restreint');
          break;
        case 'inventaire':
          if (inventaire.length === 0) {
            afficher("Inventaire vide.");
          } else {
            afficher("Inventaire actuel :");
            inventaire.forEach(obj => afficher(`- ${obj.nom} (${obj.rarete}) : ${obj.description}`));
          }
          break;
        case 'loot 1':
          afficherItem('blade_omega');
          break;
        case 'loot 2':
          afficherItem('neuro_cloak');
          break;
        case 'loot 3':
          afficherItem('injector_x');
          break;
        case 'combat':
          combat();
          break;
        case 'explorer zone_1':
        case 'explorer zone_2':
        case 'explorer zone_3':
        case 'hub':
          const code = cmd.replace('explorer ', '').replace('hub', 'hub');
          afficher(`🚪 Entrée dans : ${zones[code] || 'zone inconnue'}... Préparez-vous à l’imprévu.`);
          break;
        default:
          afficher('Commande inconnue. Tapez "help" pour assistance.');
      }
    }
  </script>
</body>
</html>
