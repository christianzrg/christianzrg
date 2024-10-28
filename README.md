<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atrapa los Círculos</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { display: flex; justify-content: center; align-items: center; height: 100vh; background-color: #f4f4f4; font-family: Arial, sans-serif; }
        #game-container { position: relative; width: 80vw; height: 80vh; background: #fff; overflow: hidden; border: 2px solid #333; border-radius: 8px; }
        #circle { width: 50px; height: 50px; border-radius: 50%; background-color: #3498db; position: absolute; cursor: pointer; }
        #score { font-size: 1.5em; margin: 10px; color: #333; }
    </style>
</head>
<body>
    <div id="game-container">
        <div id="score">Puntos: 0</div>
        <div id="circle"></div>
    </div>

    <script>
        let score = 0;
        const circle = document.getElementById("circle");
        const scoreDisplay = document.getElementById("score");
        const gameContainer = document.getElementById("game-container");

        function moveCircle() {
            const x = Math.random() * (gameContainer.clientWidth - circle.offsetWidth);
            const y = Math.random() * (gameContainer.clientHeight - circle.offsetHeight);
            circle.style.left = `${x}px`;
            circle.style.top = `${y}px`;
        }

        function startGame() {
            score = 0;
            scoreDisplay.textContent = `Puntos: ${score}`;
            circle.style.display = "block";
            const gameInterval = setInterval(() => {
                moveCircle();
            }, 800);

            circle.addEventListener("click", () => {
                score++;
                scoreDisplay.textContent = `Puntos: ${score}`;
            });

            setTimeout(() => {
                clearInterval(gameInterval);
                alert(`Juego terminado. Puntos: ${score}`);
                circle.style.display = "none";
            }, 15000); // El juego dura 15 segundos
        }

        window.onload = startGame;
    </script>
</body>
</html>
