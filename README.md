<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Jogo da Velha · Menu Topo · Cores</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #1e2b3a, #0f1a24);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .game-wrapper {
            width: 100%;
            max-width: 600px;
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
        }

        /* MENU SUPERIOR - SEPARADO DO TABULEIRO */
        .menu-top {
            background: rgba(20, 30, 45, 0.98);
            backdrop-filter: blur(10px);
            border-radius: 2rem;
            padding: 1.2rem;
            border: 3px solid #ffaa33;
            box-shadow: 0 0 30px rgba(255, 170, 51, 0.4);
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .menu-row {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .mode-btn, .diff-btn {
            flex: 1;
            min-width: 120px;
            background: rgba(0, 0, 0, 0.4);
            border: 2px solid #88ddff;
            color: #88ddff;
            font-size: 1.2rem;
            font-weight: 600;
            padding: 0.8rem 1rem;
            border-radius: 3rem;
            cursor: pointer;
            transition: 0.2s;
            text-align: center;
            letter-spacing: 1px;
        }

        .mode-btn.active {
            background: #88ddff;
            color: #0f1a24;
            border-color: #ffaa33;
            box-shadow: 0 0 25px #88ddff;
            transform: scale(1.02);
        }

        .diff-btn {
            border-color: #ff99cc;
            color: #ff99cc;
        }

        .diff-btn.active-diff {
            background: #ff99cc;
            color: #0f1a24;
            border-color: #ffaa33;
            box-shadow: 0 0 25px #ff99cc;
        }

        /* Nomes */
        .name-panel {
            background: rgba(20, 30, 45, 0.98);
            border-radius: 2rem;
            padding: 1.2rem;
            border: 3px solid #88ddff;
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .name-input {
            flex: 1;
            min-width: 120px;
            background: #1e2b3a;
            border: 2px solid #ffaa33;
            border-radius: 3rem;
            padding: 0.8rem 1.2rem;
            color: #ffffff;
            font-size: 1rem;
            font-weight: 500;
            outline: none;
        }

        .name-input::placeholder {
            color: #aaccff;
        }

        /* Status */
        .status-panel {
            background: rgba(20, 30, 45, 0.98);
            border-radius: 2rem;
            padding: 1.2rem 1.5rem;
            border: 3px solid #ff99cc;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .turn-box {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .player-label {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            background: #1e2b3a;
            padding: 0.5rem 1.5rem 0.5rem 1.2rem;
            border-radius: 3rem;
            border: 2px solid;
        }

        .player-label.X-turn {
            border-color: #00ffff;
            box-shadow: 0 0 20px #00ffff;
        }
        .player-label.O-turn {
            border-color: #ff69b4;
            box-shadow: 0 0 20px #ff69b4;
        }

        #currentSymbol {
            font-size: 2.2rem;
            font-weight: 700;
            width: 2.5rem;
            text-align: center;
        }

        .X-turn #currentSymbol { color: #00ffff; text-shadow: 0 0 20px #00ffff; }
        .O-turn #currentSymbol { color: #ff69b4; text-shadow: 0 0 20px #ff69b4; }

        #playerNameDisplay {
            color: white;
            font-size: 1.2rem;
            font-weight: 500;
        }

        .score-box {
            display: flex;
            gap: 1.5rem;
            background: #1e2b3a;
            padding: 0.5rem 1.5rem;
            border-radius: 3rem;
            border: 2px solid #ffaa33;
        }

        .score-box span {
            color: #ffaa33;
            font-size: 1.3rem;
            font-weight: 700;
            text-shadow: 0 0 10px #ffaa33;
        }

        .score-box span span {
            color: #88ddff;
            margin-left: 0.5rem;
            font-size: 1.5rem;
        }

        /* Tabuleiro */
        .board-container {
            position: relative;
            width: 100%;
            aspect-ratio: 1/1;
            background: rgba(20, 30, 45, 0.98);
            border-radius: 2.5rem;
            padding: 1.2rem;
            border: 3px solid #ffaa33;
            box-shadow: 0 0 40px rgba(255, 170, 51, 0.4);
        }

        .board {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 0.8rem;
            width: 100%;
            height: 100%;
        }

        .cell {
            background: #1e2b3a;
            border-radius: 2rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5rem;
            font-weight: 800;
            cursor: pointer;
            box-shadow: 0 8px 0 #0f1a24, 0 0 30px rgba(136, 221, 255, 0.5);
            aspect-ratio: 1/1;
            border: 2px solid #88ddff;
            transition: 0.1s;
            color: #88ddff;
            text-shadow: 0 0 20px #88ddff;
        }

        .cell.X {
            color: #00ffff;
            text-shadow: 0 0 30px #00ffff, 0 0 60px #0088ff;
            border-color: #00ffff;
        }

        .cell.O {
            color: #ff69b4;
            text-shadow: 0 0 30px #ff69b4, 0 0 60px #ff0088;
            border-color: #ff69b4;
        }

        .cell:active {
            transform: translateY(4px);
            box-shadow: 0 4px 0 #0f1a24;
        }

        /* Linha de vitória */
        .win-line-svg {
            position: absolute;
            top: 1.2rem;
            left: 1.2rem;
            width: calc(100% - 2.4rem);
            height: calc(100% - 2.4rem);
            pointer-events: none;
        }

        .win-line {
            stroke: #ffaa33;
            stroke-width: 10;
            stroke-linecap: round;
            filter: drop-shadow(0 0 15px #ffaa33) drop-shadow(0 0 30px #ff5500);
            stroke-dasharray: 200;
            stroke-dashoffset: 200;
            animation: draw 0.4s forwards;
        }

        @keyframes draw {
            to { stroke-dashoffset: 0; }
        }

        .reset-btn {
            background: #ffaa33;
            border: none;
            color: #0f1a24;
            font-size: 1.4rem;
            font-weight: 700;
            padding: 1rem;
            border-radius: 3rem;
            cursor: pointer;
            border: 3px solid #88ddff;
            box-shadow: 0 5px 0 #b37400, 0 0 30px #ffaa33;
            transition: 0.1s;
            letter-spacing: 2px;
            margin-top: 0.5rem;
        }

        .reset-btn:active {
            transform: translateY(5px);
            box-shadow: 0 1px 0 #b37400;
        }

        .footer-note {
            text-align: center;
            color: #88ddff;
            font-size: 1rem;
            text-shadow: 0 0 8px #88ddff;
        }
    </style>
</head>
<body>
<div class="game-wrapper">
    <!-- MENU SUPERIOR - SEPARADO DO TABULEIRO -->
    <div class="menu-top">
        <div class="menu-row">
            <button class="mode-btn active" data-mode="1p">🤖 1 vs IA</button>
            <button class="mode-btn" data-mode="2p">👥 2 jogadores</button>
        </div>
        <div class="menu-row">
            <button class="diff-btn" data-diff="easy">😌 FÁCIL</button>
            <button class="diff-btn" data-diff="medium">⚖️ MÉDIO</button>
            <button class="diff-btn active-diff" data-diff="hard">🤖 DIFÍCIL</button>
        </div>
    </div>

    <!-- Nomes -->
    <div class="name-panel">
        <input type="text" class="name-input" id="playerXName" placeholder="Jogador X" value="X">
        <input type="text" class="name-input" id="playerOName" placeholder="Jogador O" value="O">
    </div>

    <!-- Status -->
    <div class="status-panel">
        <div class="turn-box">
            <div class="player-label X-turn" id="playerBadge">
                <span id="currentSymbol">X</span>
                <span id="playerNameDisplay">X</span>
            </div>
            <span style="color:white; font-size:1.2rem;">vez</span>
        </div>
        <div class="score-box">
            <span>🏆 <span id="scoreX">0</span></span>
            <span>🏆 <span id="scoreO">0</span></span>
        </div>
    </div>

    <!-- TABULEIRO -->
    <div class="board-container">
        <div class="board" id="board">
            <div class="cell" data-index="0"></div>
            <div class="cell" data-index="1"></div>
            <div class="cell" data-index="2"></div>
            <div class="cell" data-index="3"></div>
            <div class="cell" data-index="4"></div>
            <div class="cell" data-index="5"></div>
            <div class="cell" data-index="6"></div>
            <div class="cell" data-index="7"></div>
            <div class="cell" data-index="8"></div>
        </div>
        <svg class="win-line-svg" viewBox="0 0 300 300">
            <path id="winLinePath" class="win-line" d="" fill="none"/>
        </svg>
    </div>

    <!-- Botão reset -->
    <button class="reset-btn" id="resetGame">⟳ REINICIAR PARTIDA</button>
    <div class="footer-note">início aleatório · cores vibrantes</div>
</div>

<script>
    (function() {
        // Estado
        let board = ['', '', '', '', '', '', '', '', ''];
        let currentPlayer = 'X';
        let gameActive = true;
        let mode = '1p';
        let difficulty = 'hard';
        let scoreX = 0, scoreO = 0;

        // Elementos
        const cells = document.querySelectorAll('.cell');
        const playerNameDisplay = document.getElementById('playerNameDisplay');
        const currentSymbol = document.getElementById('currentSymbol');
        const playerBadge = document.getElementById('playerBadge');
        const scoreXSpan = document.getElementById('scoreX');
        const scoreOSpan = document.getElementById('scoreO');
        const winLinePath = document.getElementById('winLinePath');
        const playerXName = document.getElementById('playerXName');
        const playerOName = document.getElementById('playerOName');
        const resetBtn = document.getElementById('resetGame');

        // Sons
        function playSound(type) {
            try {
                const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.value = type === 'win' ? 800 : (type === 'move' ? 440 : 330);
                gain.gain.value = 0.15;
                osc.connect(gain).connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + 0.15);
                if (audioCtx.state === 'suspended') audioCtx.resume();
            } catch(e) {}
        }

        // Atualizar display
        function updateDisplay() {
            cells.forEach((cell, i) => {
                cell.textContent = board[i];
                cell.className = `cell ${board[i]}`;
            });
            
            const xName = playerXName.value.trim() || 'X';
            const oName = playerOName.value.trim() || 'O';
            
            if (mode === '1p') {
                playerNameDisplay.textContent = currentPlayer === 'X' ? xName : 'IA';
            } else {
                playerNameDisplay.textContent = currentPlayer === 'X' ? xName : oName;
            }
            
            currentSymbol.textContent = currentPlayer;
            
            if (currentPlayer === 'X') {
                playerBadge.classList.add('X-turn');
                playerBadge.classList.remove('O-turn');
            } else {
                playerBadge.classList.add('O-turn');
                playerBadge.classList.remove('X-turn');
            }
        }

        // Verificar vencedor
        function checkWinner() {
            const patterns = [
                [0,1,2],[3,4,5],[6,7,8],
                [0,3,6],[1,4,7],[2,5,8],
                [0,4,8],[2,4,6]
            ];
            
            for (let p of patterns) {
                if (board[p[0]] && board[p[0]] === board[p[1]] && board[p[0]] === board[p[2]]) {
                    return { winner: board[p[0]], pattern: p };
                }
            }
            if (board.every(cell => cell)) return { winner: 'draw', pattern: null };
            return { winner: null, pattern: null };
        }

        // Desenhar linha
        function drawLine(pattern) {
            const centers = [[50,50],[150,50],[250,50],[50,150],[150,150],[250,150],[50,250],[150,250],[250,250]];
            const [a, , c] = pattern;
            winLinePath.setAttribute('d', `M${centers[a][0]},${centers[a][1]} L${centers[c][0]},${centers[c][1]}`);
        }

        // Fim de jogo
        function gameOver(winner, pattern) {
            gameActive = false;
            playSound(winner === 'draw' ? 'draw' : 'win');
            
            if (winner === 'X') scoreX++;
            else if (winner === 'O') scoreO++;
            
            scoreXSpan.textContent = scoreX;
            scoreOSpan.textContent = scoreO;
            
            if (pattern) drawLine(pattern);
            
            setTimeout(() => {
                resetGame();
                winLinePath.setAttribute('d', '');
            }, 1500);
        }

        // Reset com início ALEATÓRIO
        function resetGame() {
            for (let i = 0; i < 9; i++) board[i] = '';
            
            // SORTEIA QUEM COMEÇA (X ou O)
            const randomStart = Math.random() < 0.5 ? 'X' : 'O';
            currentPlayer = randomStart;
            
            gameActive = true;
            updateDisplay();
            
            // Se modo 1p e quem começar for O (IA), dispara IA
            if (mode === '1p' && currentPlayer === 'O') {
                setTimeout(makeAIMove, 500);
            }
        }

        // IA
        function makeAIMove() {
            if (!gameActive || currentPlayer !== 'O') return;
            
            const available = board.reduce((acc, cell, i) => cell === '' ? [...acc, i] : acc, []);
            if (!available.length) return;
            
            let move;
            
            if (difficulty === 'easy') {
                move = available[Math.floor(Math.random() * available.length)];
            } else if (difficulty === 'medium') {
                if (Math.random() < 0.5) {
                    move = getBestMove('O') ?? getBestMove('X') ?? available[0];
                } else {
                    move = available[Math.floor(Math.random() * available.length)];
                }
            } else {
                move = getBestMove('O') ?? getBestMove('X') ?? (board[4] === '' ? 4 : null) ?? 
                       [0,2,6,8].filter(i => board[i] === '')[0] ?? available[0];
            }
            
            if (move === undefined) move = available[0];
            
            board[move] = 'O';
            playSound('move');
            updateDisplay();
            
            const result = checkWinner();
            if (result.winner) {
                gameOver(result.winner, result.pattern);
                return;
            }
            
            currentPlayer = 'X';
            gameActive = true;
            updateDisplay();
        }

        function getBestMove(player) {
            const patterns = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
            for (let p of patterns) {
                if (board[p[0]] === player && board[p[1]] === player && board[p[2]] === '') return p[2];
                if (board[p[0]] === player && board[p[2]] === player && board[p[1]] === '') return p[1];
                if (board[p[1]] === player && board[p[2]] === player && board[p[0]] === '') return p[0];
            }
            return null;
        }

        // Clique nas células
        cells.forEach(cell => {
            cell.addEventListener('click', () => {
                if (!gameActive) return;
                
                const index = parseInt(cell.dataset.index);
                if (board[index] !== '') return;
                
                // Em modo 1p, só permite jogar se for a vez do jogador (não IA)
                if (mode === '1p' && currentPlayer === 'O') return;
                
                board[index] = currentPlayer;
                playSound('move');
                updateDisplay();
                
                const result = checkWinner();
                if (result.winner) {
                    gameOver(result.winner, result.pattern);
                    return;
                }
                
                // Alterna jogador
                currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
                updateDisplay();
                
                // Se modo 1p e agora é O (IA), chama IA
                if (mode === '1p' && currentPlayer === 'O' && gameActive) {
                    setTimeout(makeAIMove, 300);
                }
            });
        });

        // Botões de modo (menu superior)
        document.querySelectorAll('.mode-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.mode-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
                mode = this.dataset.mode;
                resetGame();
            });
        });

        // Botões de dificuldade (menu superior)
        document.querySelectorAll('.diff-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.diff-btn').forEach(b => b.classList.remove('active-diff'));
                this.classList.add('active-diff');
                difficulty = this.dataset.diff;
                if (mode === '1p') resetGame();
            });
        });

        // Reset button
        resetBtn.addEventListener('click', resetGame);

        // Inputs
        playerXName.addEventListener('input', updateDisplay);
        playerOName.addEventListener('input', updateDisplay);

        // Iniciar
        resetGame();
    })();
</script>
</body>
</html>
