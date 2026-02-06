<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Valentine 💖</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        background: #fff0f5;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-family: 'Arial', sans-serif;
        overflow: hidden;
        text-align: center;
    }

    h1 {
        font-size: 48px;
        font-weight: bold;
        margin-bottom: 40px;
    }

    .buttons {
        position: relative;
    }

    button {
        font-size: 20px;
        padding: 15px 30px;
        margin: 10px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
    }

    #yesBtn {
        background-color: #2ecc71;
        color: white;
    }

    #noBtn {
        background-color: #e74c3c;
        color: white;
        position: absolute;
    }

    /* Popup */
    #popup {
        display: none;
        position: fixed;
        inset: 0;
        background: rgba(0,0,0,0.6);
        color: white;
        font-size: 28px;
        align-items: center;
        justify-content: center;
        z-index: 10;
    }

    /* Petals */
    .petal {
        position: fixed;
        top: -20px;
        font-size: 24px;
        animation: fall linear forwards;
        pointer-events: none;
    }

    @keyframes fall {
        to {
            transform: translateY(110vh) rotate(360deg);
        }
    }

    #warning {
        margin-top: 20px;
        font-size: 20px;
        color: #c0392b;
        font-weight: bold;
    }
</style>
</head>

<body>

<h1>Will you be my Valentine forever?</h1>

<div class="buttons">
    <button id="yesBtn">Yes 💚</button>
    <button id="noBtn">No ❤️</button>
</div>

<div id="warning"></div>

<div id="popup">
    <div>
        💖💐<br>
        I love you so much baby,<br>
        I will love you forever ever and ever....
    </div>
</div>

<script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const popup = document.getElementById("popup");
    const warning = document.getElementById("warning");

    let noClicks = 0;

    noBtn.style.left = "120px";

    noBtn.addEventListener("click", () => {
        noClicks++;

        const x = Math.random() * (window.innerWidth - 150);
        const y = Math.random() * (window.innerHeight - 150);

        noBtn.style.left = x + "px";
        noBtn.style.top = y + "px";

        if (noClicks >= 4) {
            warning.textContent = "Press yes or I will bite you, honey.";
        }
    });

    yesBtn.addEventListener("click", () => {
        popup.style.display = "flex";
        createPetals();
    });

    function createPetals() {
        for (let i = 0; i < 40; i++) {
            const petal = document.createElement("div");
            petal.className = "petal";
            petal.textContent = "🌸";
            petal.style.left = Math.random() * window.innerWidth + "px";
            petal.style.animationDuration = (3 + Math.random() * 3) + "s";
            document.body.appendChild(petal);

            setTimeout(() => petal.remove(), 6000);
        }
    }
</script>

</body>
</html>
