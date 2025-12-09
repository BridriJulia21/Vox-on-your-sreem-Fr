# Vox-on-your-sreem-Fr<!DOCTYPE html>
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

    #console {
        font-size: 1.2em;
        white-space: pre-line;
        text-align: left;
        width: 60%;
        color: #0affff;
    }

    /* --- Avatar numérique inspiré Vox --- */
    #avatar {
        font-size: 120px;
        line-height: 0.8;
        display: inline-block;
        position: relative;
        color: #ff2a2a;
        animation: avatarFlicker 0.12s infinite;
        text-shadow: 0 0 6px #ff1a1a, 0 0 12px #ff1a1a;
        white-space: pre-line;
    }

    @keyframes avatarFlicker {
        0% { opacity: 1; transform: scale(1); }
        20% { opacity: 0.8; transform: scale(1.02) skewX(1deg); }
        40% { opacity: 1; transform: scale(0.98) skewX(-1deg); }
        60% { opacity: 0.7; }
        80% { opacity: 1; transform: scale(1.03); }
        100% { opacity: 1; }
    }

    #avatar::before, #avatar::after {
        content: attr(data-face);
        position: absolute;
        top: 0; left: 0;
        white-space: pre-line;
    }

    #avatar::before {
        color: cyan;
        animation: avatarGlitch1 0.2s infinite;
    }

    #avatar::after {
        color: magenta;
        animation: avatarGlitch2 0.15s infinite;
    }

    @keyframes avatarGlitch1 {
        0% { transform: translate(0,0); opacity: 0.3; }
        50% { transform: translate(4px,-2px); opacity: 0.6; }
        100% { transform: translate(-3px,2px); opacity: 0.3; }
    }

    @keyframes avatarGlitch2 {
        0% { transform: translate(0,0); opacity: 0.3; }
        50% { transform: translate(-3px,1px); opacity: 0.7; }
        100% { transform: translate(3px,-1px); opacity: 0.4; }
    }

    /* --- Glitch TV avancé pour le texte --- */
    .tv-glitch {
        position: relative;
        font-size: 2.5em;
        text-transform: uppercase;
        color: #ff2a2a;
    }

    .tv-glitch::before,
    .tv-glitch::after {
        content: attr(data-text);
        position: absolute;
        top: 0; left: 0;
        width: 100%; height: 100%;
    }

    .tv-glitch::before {
        color: cyan;
        animation: glitchSlice1 0.4s infinite linear alternate-reverse;
    }

    .tv-glitch::after {
        color: magenta;
        animation: glitchSlice2 0.3s infinite linear alternate-reverse;
    }

    @keyframes glitchSlice1 {
        0% { clip-path: inset(10% 0 60% 0); }
        25% { clip-path: inset(40% 0 20% 0); }
        50% { clip-path: inset(5% 0 70% 0); }
        75% { clip-path: inset(70% 0 5% 0); }
        100% { clip-path: inset(30% 0 40% 0); }
    }

    @keyframes glitchSlice2 {
        0% { clip-path: inset(60% 0 10% 0); }
        25% { clip-path: inset(20% 0 50% 0); }
        50% { clip-path: inset(40% 0 30% 0); }
        75% { clip-path: inset(10% 0 70% 0); }
        100% { clip-path: inset(50% 0 10% 0); }
    }
</style>
</head>
<body>

<div id="loadingScreen">
    <div id="console"></div>
</div>

<div id="mainScreen">

    <!-- AVATAR ANIMÉ INSÉRÉ ICI -->
    <div id="avatar" data-face="◣■◢
▼▲▼">◣■◢
▼▲▼</div>

    <!-- TEXTE AVEC GLITCH TV -->
    <div class="tv-glitch" id="message" data-text=""></div>

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

// Affichage progressif du terminal
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

    const fullMessage = "Bienvenue à Voxtek technologie, faites nous confiance, nous veillerons sur vous...";
    const messageDiv = document.getElementById("message");

    let i = 0;
    function typeMessage() {
        if (i < fullMessage.length) {
            const currentText = fullMessage.slice(0, i+1);
            messageDiv.innerHTML = currentText;
            messageDiv.setAttribute("data-text", currentText);
            i++;
            setTimeout(typeMessage, 40);
        }
    }
    typeMessage();
}
</script>

</body>
</html>
