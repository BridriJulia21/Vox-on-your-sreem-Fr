# Vox-on-your-sreem-Fr<!DOCTYPE html>
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Animation Vox</title>
<style>
    body {
        background: #0d0d0d;
        color: white;
        font-family: Arial, sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }

    .vox-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        animation: fadeIn 2s ease;
    }

    /* Cercle représentant Vox */
    .vox-face {
        width: 120px;
        height: 120px;
        background: #3a3aff;
        border-radius: 50%;
        box-shadow: 0 0 25px #3a3aff;
        position: relative;
        margin-bottom: 25px;
    }

    /* Bouche animée */
    .mouth {
        position: absolute;
        bottom: 25px;
        left: 50%;
        width: 40px;
        height: 10px;
        background: white;
        border-radius: 10px;
        transform: translateX(-50%);
        animation: talk 0.3s infinite alternate;
    }

    @keyframes talk {
        0% { height: 8px; }
        100% { height: 25px; }
    }

    /* Bulle de texte */
    .speech {
        background: white;
        color: black;
        padding: 15px 20px;
        border-radius: 15px;
        font-size: 1.2em;
        max-width: 300px;
        text-align: center;
        box-shadow: 0 0 20px rgba(255,255,255,0.3);
        position: relative;
    }

    .speech::after {
        content: "";
        position: absolute;
        top: 100%;
        left: 50%;
        transform: translateX(-50%);
        border-width: 12px;
        border-style: solid;
        border-color: white transparent transparent transparent;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: scale(.8); }
        to   { opacity: 1; transform: scale(1); }
    }

</style>
</head>
<body>

<div class="vox-container">
    <div class="vox-face">
        <div class="mouth"></div>
    </div>

    <div class="speech">
        Faites-nous confiance, nous veillons sur vous...
    </div>
</div>

</body>
</html>
