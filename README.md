<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Les Tricheurs des Réalités - Chapitre 1</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #1a1a1a;
            color: white;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }
        header {
            background-color: #2c3e50;
            padding: 20px;
            text-align: center;
            font-size: 24px;
        }
        .chapitre-container {
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            align-items: center;
            padding: 20px;
            overflow-y: auto;
            height: calc(100vh - 100px);
        }
        .chapitre-content {
            background-color: #34495e;
            padding: 20px;
            border-radius: 8px;
            width: 80%;
            max-width: 800px;
            overflow-y: auto;
            margin-bottom: 20px;
        }
        .terminal {
            background-color: #1e272e;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            width: 80%;
            max-width: 800px;
            color: #00ff00;
            font-family: 'Courier New', Courier, monospace;
        }
        .weapon-selector {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .weapon-button {
            padding: 10px 20px;
            background-color: #16a085;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .weapon-button:hover {
            background-color: #1abc9c;
        }
        .weapon-selected {
            background-color: #e74c3c;
        }
        .weapon-info {
            margin-top: 20px;
        }
        .image-section {
            margin-top: 20px;
            width: 80%;
            max-width: 800px;
        }
        .image-section img {
            width: 100%;
            border-radius: 8px;
        }
        footer {
            background-color: #2c3e50;
            padding: 10px;
            text-align: center;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

<header>
    Chapitre 1 - *Les Tricheurs des Réalités*
</header>

<div class="chapitre-container">
    <div class="chapitre-content">
        <h2>Les Monstres d'Ombres au Centre Commercial</h2>
        <p>
            Le centre commercial était plongé dans un chaos indescriptible. Des silhouettes de monstres d'ombres se faufilaient entre les étals,
            et les bruits de leurs pas résonnaient dans l'air lourd. Sorane, brandissant sa batte de baseball, se tenait prêt à affronter l'inconnu...
        </p>
        <p>
            Les soldats de l'armée avaient envahi les lieux, mais ils semblaient incapables de maîtriser la situation. L'attaque des créatures
            surnaturelles s'intensifiait à chaque instant. L'atmosphère était imprégnée de mystère et de peur. Sorane n'était pas du genre à se laisser intimider...
        </p>
        <p>
            Tandis que le chaos régnait à la surface, une trappe métallique menait aux égouts. Sorane y descendit à la recherche d'indices. Une odeur nauséabonde emplit l'air,
            et un frisson lui parcourut l'échine lorsqu'un bruit visqueux résonna. Un monstre reptilien surgit des ombres, ses yeux rouges brillant dans la pénombre...
        </p>
    </div>

    <div class="terminal">
        <p><strong>Terminal de Commande:</strong></p>
        <p id="terminal-output">> Chargement des données du centre commercial...</p>
    </div>

    <div class="weapon-selector">
        <button class="weapon-button" id="batte-btn">Batte de Baseball</button>
        <button class="weapon-button" id="pistolet-btn">Pistolet</button>
        <button class="weapon-button" id="lance-flammes-btn">Lance-Flammes</button>
    </div>

    <div class="weapon-info">
        <p id="weapon-description">Sélectionnez une arme pour en savoir plus...</p>
    </div>

    <div class="image-section">
        <img src="https://via.placeholder.com/800x400.png?text=Centre+Commercial+%2B+Monstres+d%27Ombres" alt="Centre commercial attaqué par des ombres">
    </div>
</div>

<footer>
    *Les Tricheurs des Réalités* - Chapitre 1
</footer>

<script>
    const terminalOutput = document.getElementById('terminal-output');
    const batteBtn = document.getElementById('batte-btn');
    const pistoletBtn = document.getElementById('pistolet-btn');
    const lanceFlammesBtn = document.getElementById('lance-flammes-btn');
    const weaponDescription = document.getElementById('weapon-description');

    batteBtn.addEventListener('click', () => {
        terminalOutput.innerHTML = "> Armes : Batte de baseball sélectionnée. Prête à l'emploi.";
        updateWeaponDescription("Batte de Baseball : Une arme simple mais efficace. Son impact peut désorienter un ennemi.");
        setWeaponSelected(batteBtn);
    });

    pistoletBtn.addEventListener('click', () => {
        terminalOutput.innerHTML = "> Armes : Pistolet sélectionné. Munition en cours d'activation.";
        updateWeaponDescription("Pistolet : Une arme à feu classique. Peut tuer à distance avec précision.");
        setWeaponSelected(pistoletBtn);
    });

    lanceFlammesBtn.addEventListener('click', () => {
        terminalOutput.innerHTML = "> Armes : Lance-flammes prêt à brûler tout sur son passage.";
        updateWeaponDescription("Lance-Flammes : Une arme dévastatrice qui peut incinérer de larges zones.");
        setWeaponSelected(lanceFlammesBtn);
    });

    function updateWeaponDescription(description) {
        weaponDescription.innerHTML = description;
    }

    function setWeaponSelected(selectedBtn) {
        const buttons = [batteBtn, pistoletBtn, lanceFlammesBtn];
        buttons.forEach(button => {
            button.classList.remove('weapon-selected');
        });
        selectedBtn.classList.add('weapon-selected');
    }
</script>

</body>
</html>
