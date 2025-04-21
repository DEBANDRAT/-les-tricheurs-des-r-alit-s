<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Les Tricheurs des Réalités - Chapitre 1</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #111;
            color: white;
            text-align: center;
        }

        .cinematique {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('background-exoterique.jpg'); /* Remplacer par l'image mystique */
            background-size: cover;
            background-position: center;
            animation: fadeIn 4s ease-in-out;
        }

        h1, h2 {
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .text {
            margin-top: 20%;
            font-size: 1.5em;
            line-height: 1.5;
            text-shadow: 0 0 15px rgba(255, 0, 0, 0.7);
        }

        .dialogue {
            font-style: italic;
            color: #ffcc00;
            text-shadow: 1px 1px 10px rgba(255, 255, 255, 0.7);
        }

        .action {
            font-weight: bold;
            color: #00ffcc;
        }

        audio {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
        }
    </style>
</head>
<body>

    <!-- Musique de fond mystique -->
    <audio autoplay loop>
        <source src="music/mystic-background.mp3" type="audio/mpeg"> <!-- Remplacer par la musique mystique -->
        Votre navigateur ne supporte pas l'élément audio.
    </audio>

    <!-- Cinématique -->
    <div class="cinematique">
        <div class="text">
            <h1>Les Tricheurs des Réalités</h1>
            <h2>Chapitre 1 : Les Ombres du Centre Commercial</h2>
            <p class="dialogue">"Attends ! Je ne te veux aucun mal, Sorane!"</p>
            <p class="dialogue">"Allez-vous-en!"</p>
            <p class="action">Soudain, les lumières du centre commercial commencent à clignoter...</p>
            <p class="action">Les ombres surgissent des murs et du sol, formant des créatures hideuses...</p>
            <p class="dialogue">"On va devoir passer par les sous-sols… il n’y a plus d’échappatoire."</p>
            <p class="action">Sorane et Duality se préparent à fuir à travers un couloir sombre.</p>
        </div>
    </div>

</body>
</html>
