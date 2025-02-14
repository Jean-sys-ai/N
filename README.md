<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz Mesiversario</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }
        .screen {
            width: 100vw;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            position: absolute;
            top: 0;
            left: 0;
            transition: opacity 1s ease-in-out;
        }
        .hidden {
            opacity: 0;
            pointer-events: none;
        }
        /* Pantalla 1: Fondo negro con corazones */
        #screen1 {
            background: black;
            color: white;
            position: relative;
        }
        @keyframes sparkle {
            0% { opacity: 0.2; }
            50% { opacity: 1; }
            100% { opacity: 0.2; }
        }
        .heart {
            position: absolute;
            width: 10px;
            height: 10px;
            background: red;
            clip-path: polygon(50% 0%, 100% 40%, 80% 100%, 50% 80%, 20% 100%, 0% 40%);
            animation: sparkle 2s infinite alternate;
        }
        h1 {
            font-size: 3rem;
            animation: glow 2s infinite alternate;
        }
        @keyframes glow {
            0% { text-shadow: 0 0 10px red; }
            100% { text-shadow: 0 0 30px red; }
        }
        .small-text {
            font-size: 1.2rem;
            color: pink;
        }
        /* Pantalla 2: Flores y poema */
        #screen2 {
            background: #f8f0ff;
            color: #5a2a82;
            text-align: center;
        }
        .flowers {
            position: absolute;
            bottom: -100px;
            display: flex;
            justify-content: center;
            gap: 20px;
            width: 100%;
        }
        .flower {
            width: 50px;
            height: 80px;
            background: linear-gradient(to top, #c29fff, #8a2be2);
            border-radius: 50% 50% 0 0;
            transform: rotate(-10deg);
            animation: grow 2s ease-in-out forwards;
        }
        @keyframes grow {
            0% { transform: translateY(100px) scaleY(0); }
            100% { transform: translateY(0) scaleY(1); }
        }
        /* Botón */
        .next-button {
            padding: 10px 20px;
            background: red;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 1.2rem;
            margin-top: 20px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div id="screen1" class="screen">
        <div id="hearts"></div>
        <h1>Te amo mucho mi vida</h1>
        <p class="small-text">Feliz Mesiversario</p>
        <button class="next-button" onclick="nextScreen()">Siguiente</button>
    </div>
    <div id="screen2" class="screen hidden">
        <div class="flowers">
            <div class="flower"></div>
            <div class="flower"></div>
            <div class="flower"></div>
        </div>
        <p>En mi vida has llegado a ser la poesía más sincera, la más dulce de las melodías,
           eres un poema que se tatuó en mi corazón, la canción que mueve todo mi interior,
           has llegado a ser el mejor de los veranos en medio del más frío invierno, la brisa más suave
           entre mis más fuertes tormentas, has llegado a ser lo que nadie jamás podrá igualar.</p>
    </div>
    <script>
        function nextScreen() {
            document.getElementById('screen1').classList.add('hidden');
            document.getElementById('screen2').classList.remove('hidden');
        }
        function createHearts() {
            const heartsContainer = document.getElementById('hearts');
            for (let i = 0; i < 50; i++) {
                let heart = document.createElement('div');
                heart.className = 'heart';
                heart.style.top = Math.random() * 100 + 'vh';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (Math.random() * 2 + 1) + 's';
                heartsContainer.appendChild(heart);
            }
        }
        createHearts();
    </script>
</body>
</html>
