<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juegos para Clase - Unblocked</title>
    <style>
        /* ESTILOS CSS (Diseño) */
        :root {
            --primary: #00ff88;
            --bg: #1a1a1a;
            --card-bg: #2d2d2d;
            --text: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        header {
            background-color: #000;
            width: 100%;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
        }

        h1 { margin: 0; color: var(--primary); text-transform: uppercase; letter-spacing: 2px; }
        p { color: #aaa; margin-top: 5px; }

        .container {
            max-width: 1000px;
            width: 90%;
            margin: 30px auto;
        }

        /* Grid de Juegos */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .game-card {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
            border: 1px solid #444;
        }

        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 255, 136, 0.2);
            border-color: var(--primary);
        }

        .game-icon {
            font-size: 40px;
            margin-bottom: 10px;
            display: block;
        }

        .game-title {
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 10px;
            display: block;
        }

        .play-btn {
            background-color: var(--primary);
            color: #000;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
        }

        /* Área de Juego (Modal) */
        #game-area {
            display: none; /* Oculto por defecto */
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.95);
            z-index: 1000;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        #game-canvas {
            background-color: #000;
            border: 2px solid var(--primary);
            box-shadow: 0 0 20px var(--primary);
        }

        .close-btn {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 40px;
            color: white;
            cursor: pointer;
            background: none;
            border: none;
        }

        .controls-hint {
            margin-top: 10px;
            color: #ccc;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>

    <header>
        <h1>🎮 Zona de Juegos</h1>
        <p>Juegos rápidos para jugar en clase (Sin descargas)</p>
    </header>

    <div class="container">
        <div class="games-grid">
            <!-- Juego 1: Snake (Programado en JS) -->
            <div class="game-card" onclick="startSnake()">
                <span class="game-icon">🐍</span>
                <span class="game-title">Snake Clásico</span>
                <button class="play-btn">Jugar Ahora</button>
            </div>

            <!-- Juego 2: Ejemplo de sitio externo (Iframe) -->
            <div class="game-card" onclick="alert('Para agregar juegos externos, necesitas un enlace directo a un juego compatible con iframes.')">
                <span class="game-icon">🚀</span>
                <span class="game-title">Juego Externo</span>
                <p style="font-size: 0.8rem; color: #888;">(Requiere configuración)</p>
                <button class="play-btn">Configurar</button>
            </div>

            <!-- Juego 3: Ejemplo -->
            <div class="game-card">
                <span class="game-icon">🧱</span>
                <span class="game-title">Tetris</span>
                <button class="play-btn">Próximamente</button>
            </div>
        </div>
    </div>

    <!-- Área donde se ejecuta el juego -->
    <div id="game-area">
        <button class="close-btn" onclick="closeGame()">&times;</button>
        <canvas id="game-canvas" width="400" height="400"></canvas>
        <div class="controls-hint">Usa las flechas del teclado para moverte</div>
    </div>

    <script>
        // LÓGICA JAVASCRIPT

        const gameArea = document.getElementById('game-area');
        const canvas = document.getElementById('game-canvas');
        const ctx = canvas.getContext('2d');

        // Variables del juego Snake
        let snake = [];
        let food = {};
        let direction = 'RIGHT';
        let gameInterval;
        const gridSize = 20;
        const tileCount = canvas.width / gridSize;

        function startSnake() {
            gameArea.style.display = 'flex';
            resetSnakeGame();
            gameInterval = setInterval(updateSnake, 100);
            document.addEventListener('keydown', keyDownEvent);
        }

        function closeGame() {
            gameArea.style.display = 'none';
            clearInterval(gameInterval);
            document.removeEventListener('keydown', keyDownEvent);
        }

        function resetSnakeGame() {
            snake = [{x: 10, y: 10}];
            direction = 'RIGHT';
            placeFood();
        }

        function placeFood() {
            food = {
                x: Math.floor(Math.random() * tileCount),
                y: Math.floor(Math.random() * tileCount)
            };
        }

        function keyDownEvent(e) {
            switch(e.keyCode) {
                case 37: if(direction !== 'RIGHT') direction = 'LEFT'; break;
                case 38: if(direction !== 'DOWN') direction = 'UP'; break;
                case 39: if(direction !== 'LEFT') direction = 'RIGHT'; break;
                case 40: if(direction !== 'UP') direction = 'DOWN'; break;
            }
        }

        function updateSnake() {
            // Mover cabeza
            const head = {x: snake[0].x, y: snake[0].y};
            if(direction === 'LEFT') head.x--;
            if(direction === 'UP') head.y--;
            if(direction === 'RIGHT') head.x++;
            if(direction === 'DOWN') head.y++;

            // Colisión con paredes (Game Over simple)
            if(head.x < 0 || head.x >= tileCount || head.y < 0 || head.y >= tileCount) {
                alert("¡Perdiste! Puntuación: " + (snake.length - 1));
                closeGame();
                return;
            }

            // Colisión con el cuerpo
            for(let i = 0; i < snake.length; i++) {
                if(head.x === snake[i].x && head.y === snake[i].y) {
                    alert("¡Perdiste! Puntuación: " + (snake.length - 1));
                    closeGame();
                    return;
                }
            }

            snake.unshift(head);

            // Comer comida
            if(head.x === food.x && head.y === food.y) {
                placeFood();
            } else {
                snake.pop();
            }

            drawSnake();
        }

        function drawSnake() {
            // Limpiar pantalla
            ctx.fillStyle = 'black';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Dibujar comida
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x * gridSize, food.y * gridSize, gridSize - 2, gridSize - 2);

            // Dibujar serpiente
            ctx.fillStyle = '#00ff88';
            for(let i = 0; i < snake.length; i++) {
                ctx.fillRect(snake[i].x * gridSize, snake[i].y * gridSize, gridSize - 2, gridSize - 2);
            }
        }
    </script>
</body>
</html>
