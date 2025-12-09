# Vox-on-your-sreem-Fr<!DOCTYPE html>
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Voxtek Animation</title>
<style>
    body {
        margin: 0;
        background: black;
        color: #0affff;
        font-family: "Courier New", monospace;
        overflow: hidden;
    }

    #loadingScreen, #mainScreen {
        position: absolute;
        top: 0; left: 0;
        width: 100%; height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    #mainScreen {
        display: none;
        color: #ff2a2a;
        text-align: center;
    }

    .glitch {
        font-size: 2.5em;
        color: #ff2a2a;
        position: relative;
        animation: glitch 0.8s infinite;
    }

    @keyframes glitch {
        0% { text-shadow: 2px 0 red, -2px 0 cyan; }
        20% { text-shadow: -2px 0 red, 2px 0 cyan; }
        40% { text-shadow: 2px 0 red, -2px 0 cyan; }
        60% { text-shadow: -2px 0 red, 2px 0 cyan; }
        100% { text-shadow: 2px 0 red, 2px 0 cyan; }
    }

    #console {
        font-size: 1.2em;
        white-space: pre-line;
        text-align: left;
        width: 60%;
        color: #0affff;
    }

    /* Silhouette numérique stylisée */
    #figure {
        margin-top: 40px;
        font-size: 6em;
        animation: flicker 1s infinite;
    }

    @keyframes flicker {
        0%, 100% { opacity: 1; }
        50% { opacity: 0.6; }
    }
</style>
</head>
<body>

<div id="loadingScreen">
    <div id="console"></div>
</div>

<div id="mainScreen">
    <div id="figure">▮▯▮</div>
    <div class="glitch" id="message"></div>
</div>

<script>
const consoleText = [
    "> Initialisation du système...",
    "> Chargement du noyau Voxtek v4.9…",
    "> Synchronisation des bases de données…",
    "> Analyse des signaux…",
    "> Connexion établie.",
];

let index = 0;
const consoleDiv = document.getElementById("console");

// Affichage ligne par ligne du chargement
function showNextLine() {
    if (index < consoleText.length) {
        consoleDiv.innerHTML += consoleText[index] + "\n";
        index++;
        setTimeout(showNextLine, 700);
    } else {
        setTimeout(startMainScreen, 800);
    }
}

showNextLine();

// Transition vers l’écran principal
function startMainScreen() {
    document.getElementById("loadingScreen").style.display = "none";
    document.getElementById("mainScreen").style.display = "flex";

    // Message d’apparition progressif
    const fullMessage = "Bienvenue à Voxtek technologie, faites nous confiance, nous veillerons sur vous...";
    const messageDiv = document.getElementById("message");

    let i = 0;
    function typeMessage() {
        if (i < fullMessage.length) {
            messageDiv.innerHTML = fullMessage.slice(0, i+1);
            i++;
            setTimeout(typeMessage, 40);
        }
    }
    typeMessage();
}
</script>

</body>
</html>

</html>
