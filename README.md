let playerHealth = 100;
let enemyHealth = 50;
let inventory = ["pistolet", "kit_medical", "revolver"];
let equippedWeapon = "pistolet";  // Arme par défaut

// Fonction pour afficher des messages
function afficher(message) {
    console.log(message);
}

// Fonction pour attaquer avec une arme
function attaquer(arme) {
    let dégâts = 0;
    let vitesse = 1; // Par défaut, la vitesse d'attaque est de 1 tour

    if (arme === "pistolet") {
        dégâts = 20;
        afficher("Vous tirez avec le pistolet !");
    } else if (arme === "revolver") {
        dégâts = 20;
        afficher("Vous tirez avec le revolver !");
    } else if (arme === "uzi") {
        dégâts = 10;
        afficher("Vous tirez avec l'Uzi !");
        // L'Uzi tire 3 balles en un seul tour
        enemyHealth -= 3 * dégâts;
        afficher(`L'ennemi subit ${3 * dégâts} de dégâts. Santé de l'ennemi: ${enemyHealth}`);
        return vitesse;  // Retourne la vitesse d'attaque pour Uzi
    } else if (arme === "fusil_precision") {
        dégâts = 50;
        vitesse = 2;  // Prend 2 tours pour viser et tirer
        afficher("Vous visez avec le fusil de précision...");
    } else if (arme === "hache") {
        dégâts = 30;
        vitesse = 2;  // Attaque puissante mais lente
        afficher("Vous attaquez avec la hache !");
    } else if (arme === "couteau_combat") {
        dégâts = 15;
        afficher("Vous attaquez avec le couteau de combat !");
    } else if (arme === "griffes_acérées") {
        dégâts = 10;
        afficher("Vous attaquez avec les griffes acérées !");
        // Attaque multiple
        enemyHealth -= dégâts * 2;
        afficher(`L'ennemi subit ${dégâts * 2} de dégâts. Santé de l'ennemi: ${enemyHealth}`);
        return vitesse;  // Retourne la vitesse pour griffes acérées
    } else if (arme === "hachette_jet") {
        dégâts = 20;
        afficher("Vous lancez la hachette de jet !");
    } else if (arme === "bolas") {
        dégâts = 0;
        afficher("Vous lancez les bolas pour immobiliser l'ennemi !");
        immobiliserEnnemi();
        return vitesse;  // Retourne la vitesse pour bolas
    } else if (arme === "bâton_feu") {
        dégâts = 25;
        afficher("Vous lancez un sort de feu !");
    } else if (arme === "orbe_glace") {
        dégâts = 15;
        afficher("Vous lancez une orbe de glace !");
        ralentirEnnemi();
    } else if (arme === "grimoire_ténèbres") {
        dégâts = 30;
        vitesse = 2;  // Attaque puissante mais lente
        afficher("Vous invoquez les ténèbres pour frapper l'ennemi !");
    }

    // Appliquer les dégâts
    enemyHealth -= dégâts;
    afficher(`L'ennemi subit ${dégâts} de dégâts. Santé de l'ennemi: ${enemyHealth}`);

    if (enemyHealth <= 0) {
        afficher("L'ennemi a été vaincu !");
    }

    // Retourner la vitesse d'attaque
    return vitesse;
}

// Fonction pour utiliser un objet
function utiliserObjet(objet) {
    if (objet === "kit_medical") {
        playerHealth += 30;
        afficher(`Vous utilisez un kit médical. Santé actuelle: ${playerHealth}`);
    }
}

// Fonction pour afficher les résistances
function afficherRésistances() {
    const playerResistances = `Physique: ${player.physicalResistance * 100}%, Magique: ${player.magicalResistance * 100}%, Élémentaire: ${player.elementalResistance * 100}%`;
    const enemyResistances = `Physique: ${enemy.physicalResistance * 100}%, Magique: ${enemy.magicalResistance * 100}%, Élémentaire: ${enemy.elementalResistance * 100}%`;
    
    afficher(`Résistances du joueur : ${playerResistances}`);
    afficher(`Résistances de l'ennemi : ${enemyResistances}`);
}

// Fonction pour appliquer les dégâts en tenant compte des résistances
function appliquerDégâts(attacker, defender, type, dégâts) {
    let résistance = 0;

    // Choisir la résistance en fonction du type d'attaque
    if (type === "physique") {
        résistance = defender.physicalResistance;
    } else if (type === "magique") {
        résistance = defender.magicalResistance;
    } else if (type === "élémentaire") {
        résistance = defender.elementalResistance;
    }

    // Réduire les dégâts par la résistance
    let dégâtsRéduits = dégâts * (1 - résistance);
    
    // Appliquer les dégâts à l'ennemi ou au joueur
    defender.health -= dégâtsRéduits;
    
    // Affichage du message de combat
    afficher(`${attacker} attaque avec ${dégâtsRéduits.toFixed(2)} dégâts. Santé restante: ${defender.health.toFixed(2)}`);

    if (defender.health <= 0) {
        afficher(`${defender === player ? "Vous avez été vaincu !" : "L'ennemi a été vaincu !"}`);
    }
}

// Exemple d'événement de combat
document.getElementById("attackBtn").addEventListener("click", function() {
    attaquer("Joueur", enemy, "physique", 20);  // Attaque physique du joueur
    if (enemy.health > 0) {
        attaquer("Ennemi", player, "magique", 15);  // Attaque magique de l'ennemi
    }
});

document.getElementById("checkResistancesBtn").addEventListener("click", afficherRésistances);
