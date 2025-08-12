// Elementos do jogo
const player = document.getElementById('player');
const obstacle = document.getElementById('obstacle');
const gameArea = document.getElementById('gameArea');

let isJumping = false;
let jumpHeight = 0;

// Função para controlar o pulo do jogador
function jump() {
    if (isJumping) return;

    isJumping = true;
    let upInterval = setInterval(() => {
        if (jumpHeight >= 100) {
            clearInterval(upInterval);
            let downInterval = setInterval(() => {
                if (jumpHeight <= 0) {
                    clearInterval(downInterval);
                    isJumping = false;
                } else {
                    jumpHeight -= 10;
                    player.style.bottom = jumpHeight + 'px';
                }
            }, 20);
        } else {
            jumpHeight += 10;
            player.style.bottom = jumpHeight + 'px';
        }
    }, 20);
}

// Detectar quando pressionar a tecla de pulo (barra de espaço)
document.addEventListener('keydown', (event) => {
    if (event.code === 'Space') {
        jump();
    }
});

// Colisão do jogador com o obstáculo
function checkCollision() {
    const playerRect = player.getBoundingClientRect();
    const obstacleRect = obstacle.getBoundingClientRect();

    if (playerRect.right > obstacleRect.left &&
        playerRect.left < obstacleRect.right &&
        playerRect.bottom > obstacleRect.top) {
        alert('Game Over!');
        resetGame();
    }
}

// Função para reiniciar o jogo
function resetGame() {
    jumpHeight = 0;
    player.style.bottom = '0px';
    obstacle.style.animation = 'none';
    setTimeout(() => {
        obstacle.style.animation = 'moveObstacle 2s linear infinite';
    }, 50);
}

// Verificar a colisão a cada 10ms
setInterval(checkCollision, 10);
