<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Les Tricheurs des Réalités – Interface Centrale</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
        body {
            margin: 0;
            background: #121212;
            color: #00FF00;
            font-family: 'Courier New', Courier, monospace;
            background-color: #000;
            color: #0f0;
            padding: 0;
        }
        h1 {
            text-align: center;
            margin-top: 20px;
        }
        /* STYLE : Hall Central */
        #hall {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            padding: 2em;
            background-color: #0e0e0e;
            color: #e0e0e0;
        }
        .menu {
            display: flex;
            flex-direction: column;
            gap: 1em;
            margin-bottom: 2em;
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
        .zones {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 20px;
        }
        .zone {
            background-color: #1a1a1a;
            border: 1px solid #555;
            padding: 1em;
            width: 200px;
            text-align: center;
            cursor: pointer;
        }
        .zone:hover {
            background-color: #333;
        }
        /* STYLE : Terminal */
        #terminal {
            display: none;
            padding: 2em;
        }
        .console {
            background-color: #111;
            border: 1px solid #0f0;
            padding: 1em;
            font-size: 18px;
            color: #0f0;
            white-space: pre-wrap;
        }
        .weapon-details {
            margin-top: 1em;
            height: 400px;
            overflow-y: auto;
            background-color: #222;
            padding: 20px;
            border: 1px solid #444;
            display: none;
            text-align: center;
        }
        .weapon-details.active {
            display: block;
        }
        input {
            background-color: #000;
            color: #0f0;
            border: none;
            width: 100%;
            font-size: 1em;
            font-family: inherit;
            padding: 10px;
        }
        .weapons-section {
            display: flex;
            flex-direction: row;
            gap: 2em;
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
            color: #e0e0e0;
        }
        .weapon:hover {
            background-color: #444;
        }
    </style>
</head>
<body>
    <!-- HALL CENTRAL -->
    <div id="hall">
        <h1>Hall Central des Tricheurs des Réalités</h1>
        <div class="menu">
            <button onclick="allerA('sorane')">▶ Entrer dans le chapitre de Sorane</button>
            <button onclick="allerA('cyber')">🔒 Chapitre de Cyber</button>
            <button onclick="allerA('mathieu')">🔒 Chapitre de Mathieu</button>
            <button onclick="allerA('archiverses')">🔒 Explorer l'Archiverses</button>
            <button onclick="allerA('megavers')">🔒 Plonger dans le Megavers</button>
        </div>
        <div class="zones">
            <div class="zone" onclick="afficherTerminal()">🖥 Terminal de Commandement</div>
            <div class="zone" onclick="alert('Carte du Multivers en cours de synchronisation...')">🗺 Carte du Multivers</div>
            <div class="zone" onclick="alert('Dialogue mystérieux enregistré...')">🧍 Hallucination résiduelle</div>
        </div>
    </div>

    <!-- Terminal -->
    <div id="terminal">
        <h1>🖥 Terminal de Commandement</h1>
        <p>Bienvenue, utilisateur non-identifié. Entrez une commande pour interagir avec les systèmes secrets de l’Omnivers de la Vierge.</p>
        <div class="console" id="console">> help : liste des commandes disponibles<br></div>
        <input type="text" id="commande" placeholder="Entrez une commande..." onkeydown="if(event.key==='Enter'){executerCommande()}" autofocus>
    </div>

    <!-- Catalogue d'Armes -->
    <div id="weapons" class="weapons-section" style="display: none;">
        <div class="weapon" onclick="afficherDetails('batte')">⚾ Batte de Baseball</div>
        <div class="weapon" onclick="afficherDetails('pistolet')">🔫 Pistolet à Répétition</div>
        <div class="weapon" onclick="afficherDetails('arc')">🏹 Arc Magique</div>
    </div>

    <script>
        function allerA(destination) {
            if (destination === 'sorane') {
                window.location.href = 'Les_Tricheurs_des_Realites_Prologue_Sorane.html';
            } else {
                alert("Zone encore en développement.");
            }
        }

        function afficherTerminal() {
            document.getElementById('hall').style.display = 'none';
            document.getElementById('terminal').style.display = 'block';
        }

        const consoleDiv = document.getElementById('console');
        const commandeInput = document.getElementById('commande');

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

        function afficher(message) {
            consoleDiv.innerHTML += `> ${message}<br>`;
            consoleDiv.scrollTop = consoleDiv.scrollHeight;
        }

        function afficherDetails(arme) {
            const details = armes[arme];
            const detailsSection = document.createElement('div');
            detailsSection.classList.add('weapon-details');
            detailsSection.innerHTML = `
                <h2>${details.nom}</h2>
                <p><strong>Type :</strong> ${details.type}</p>
                <p><strong>Dégâts :</strong> ${details.dégâts}</p>
                <p><strong>Portée :</strong> ${details.portée}</p>
                <p><strong>Description :</strong> ${details.description}</p>
                <button onclick="équiperArme('${arme}')">Équiper cette arme</button>
            `;
            document.body.appendChild(detailsSection);
            detailsSection.classList.add('active');
        }

        function équiperArme(arme) {
            alert(`L'arme ${armes[arme].nom} a été équipée.`);
            document.querySelector('.weapon-details').classList.remove('active');
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
                    afficher('Inventaire vide.');
                    break;
                case 'loot 1':
                    afficherDetails('batte');
                    break;
                case 'loot 2':
                    afficherDetails('pistolet');
                    break;
                case 'loot 3':
                    afficherDetails('arc');
                    break;
                default:
                    afficher('Commande inconnue. Tapez "help" pour assistance.');
            }
        }
    </script>
</body>
</html>
