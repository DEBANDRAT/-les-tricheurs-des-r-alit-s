/* Global styles */
body {
    margin: 0;
    padding: 0;
    background-color: #1a1a1a;
    color: #fff;
    font-family: Arial, sans-serif;
    overflow: hidden;
}

/* Conteneur principal */
#gameContainer {
    position: relative;
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

/* Console mystique */
#console {
    width: 100%;
    height: 200px;
    overflow: hidden;
    background: rgba(0, 0, 0, 0.7);
    border: 1px solid #333;
    margin-top: 20px;
    padding: 10px;
}

/* Animation de l'image */
.mystic-image {
    transition: all 0.5s ease-in-out;
    opacity: 0;
}

/* Style des boutons */
button {
    background-color: #333;
    color: #fff;
    border: none;
    padding: 15px 30px;
    font-size: 18px;
    cursor: pointer;
    border-radius: 10px;
    margin-top: 20px;
    box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.3);
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: #555;
}

/* Filtre sombre appliqué */
body.sombre {
    filter: brightness(50%) contrast(150%);
}

/* Styles de base */
h1 {
    color: #ff3333;
    font-size: 36px;
    margin-top: 20px;
}

/* Corps du jeu */
#game {
    padding: 20px;
    border-radius: 15px;
    background: rgba(0, 0, 0, 0.75);
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.9);
    color: #fff;
}

#status {
    margin-bottom: 20px;
}

#combat-log {
    background: rgba(0, 0, 0, 0.7);
    border-radius: 5px;
    padding: 10px;
    max-height: 200px;
    overflow-y: scroll;
    margin-top: 20px;
    color: #d1d1d1;
}

#combat-log ul {
    list-style-type: none;
    padding-left: 0;
}

/* Image de fond et éléments */
body {
    background-color: #222;
    color: #f4f4f4;
    background-image: url('images/gothic-background.jpg');
    background-size: cover;
    background-attachment: fixed;
}

/* Titre principal */
h1 {
    color: #ff3366;
    font-size: 40px;
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.7);
}

/* Images des personnages */
.character-image {
    width: 150px;
    height: 150px;
    margin: 10px;
    border-radius: 10px;
    box-shadow: 0 0 15px rgba(0, 0, 0, 0.7);
    transition: transform 0.3s ease-in-out;
}

.character-image:hover {
    transform: scale(1.1);
}

/* Style des boutons */
button {
    background-color: #444;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 18px;
    margin: 10px;
    transition: all 0.3s ease;
}

button:hover {
    background-color: #ff3366;
    box-shadow: 0 0 10px rgba(255, 51, 102, 0.7);
}

/* Journal de combat */
#combat-log {
    background: rgba(0, 0, 0, 0.7);
    border-radius: 5px;
    padding: 10px;
    max-height: 200px;
    overflow-y: scroll;
    margin-top: 20px;
}

/* Style pour les statuts */
#player-status, #enemy-status {
    margin-bottom: 20px;
    padding: 10px;
    background: rgba(0, 0, 0, 0.6);
    border-radius: 10px;
}
