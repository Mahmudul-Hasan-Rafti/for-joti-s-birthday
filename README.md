<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Surprise</title>
<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        font-family: Arial, sans-serif;
        overflow: hidden;
    }

    .container { text-align: center; }

    .gift-box {
        width: 150px;
        height: 150px;
        background: red;
        position: relative;
        cursor: pointer;
        margin: auto;
        border-radius: 10px;
        transition: transform 0.3s;
    }

    .gift-box:hover { transform: scale(1.1); }

    .lid {
        width: 150px;
        height: 40px;
        background: darkred;
        position: absolute;
        top: -40px;
        left: 0;
        border-radius: 10px 10px 0 0;
        transition: transform 0.8s ease;
    }

    .ribbon-vertical, .ribbon-horizontal {
        position: absolute;
        background: gold;
    }

    .ribbon-vertical { width: 20px; height: 150px; left: 65px; }
    .ribbon-horizontal { height: 20px; width: 150px; top: 65px; }

    .message {
        display: none;
        margin-top: 20px;
        font-size: 26px;
        color: white;
        background: rgba(0,0,0,0.6);
        padding: 20px;
        border-radius: 10px;
        animation: fadeIn 2s ease forwards;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    .confetti {
        position: absolute;
        width: 10px;
        height: 10px;
        background: red;
        top: -10px;
        animation: fall linear forwards;
    }

    @keyframes fall {
        to {
            transform: translateY(100vh) rotate(360deg);
            opacity: 0;
        }
    }
</style>
</head>
<body>

<div class="container">
    <div class="gift-box" onclick="openGift()">
        <div class="lid" id="lid"></div>
        <div class="ribbon-vertical"></div>
        <div class="ribbon-horizontal"></div>
    </div>

    <div class="message" id="message">
        🎉 Happy Birthday Joti 🎁<br>
        ❤️ I love you my love ❤️
    </div>
</div>

<!-- Sound -->
<audio id="music" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>

<script>
function openGift() {
    document.getElementById('lid').style.transform = 'translateY(-100px) rotate(-25deg)';
    document.getElementById('message').style.display = 'block';

    // Play music
    let music = document.getElementById('music');
    music.play();

    // Confetti
    for (let i = 0; i < 100; i++) {
        let confetti = document.createElement('div');
        confetti.classList.add('confetti');
        confetti.style.left = Math.random() * window.innerWidth + 'px';
        confetti.style.background = `hsl(${Math.random()*360},100%,50%)`;
        confetti.style.animationDuration = (2 + Math.random() * 3) + 's';
        document.body.appendChild(confetti);

        setTimeout(() => confetti.remove(), 5000);
    }
}
</script>

</body>
</html>
