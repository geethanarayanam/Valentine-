<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background-color: #ffeef2;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            text-align: center;
        }

        #container {
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            z-index: 10;
        }

        h1 { color: #d63384; margin-bottom: 2rem; }

        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
            height: 50px;
        }

        button {
            padding: 12px 25px;
            font-size: 1.2rem;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: transform 0.2s;
        }

        #yesBtn { background-color: #ff4d6d; color: white; }
        #noBtn { background-color: #adb5bd; color: white; position: relative; }

        .heart {
            position: absolute;
            color: #ff4d6d;
            font-size: 20px;
            user-select: none;
            pointer-events: none;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(100vh) rotate(360deg); }
        }

        #celebration { display: none; }
        .success-msg { color: #d63384; font-size: 1.5rem; font-weight: bold; }
    </style>
</head>
<body>

    <div id="container">
        <div id="question-side">
            <h1>Will you be my Valentine? 💖</h1>
            <div class="buttons">
                <button id="yesBtn" onclick="celebrate()">Yes!</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div id="celebration">
            <h1 class="success-msg">Yay! I knew you'd say yes! 🥰</h1>
            <p>See you on the 14th!</p>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const container = document.getElementById('question-side');
        const celebration = document.getElementById('celebration');

        // The "Runaway" No Button Logic
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'absolute';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        function celebrate() {
            container.style.display = 'none';
            celebration.style.display = 'block';
            setInterval(createHeart, 150);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(heart);
            
            setTimeout(() => { heart.remove(); }, 5000);
        }

        // Start a few hearts immediately for vibe
        setInterval(createHeart, 1000);
    </script>
</body>
</html>
