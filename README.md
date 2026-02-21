# My-love-for-you
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Heart in a Link</title>
    <style>
        :root {
            --primary-pink: #ffafcc;
            --deep-red: #ff0a54;
            --soft-white: #fff0f3;
        }

        body {
            margin: 0;
            padding: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ffafcc 0%, #ff85a1 100%);
            font-family: 'Georgia', serif;
            overflow-x: hidden;
        }

        /* Floating Hearts Background Animation */
        .heart-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .container {
            position: relative;
            z-index: 10;
            background: rgba(255, 255, 255, 0.9);
            padding: 3rem;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            text-align: center;
            max-width: 500px;
            width: 90%;
            border: 5px solid white;
        }

        h1 { color: var(--deep-red); font-size: 2.5rem; margin-bottom: 20px; }
        
        .btn-group { margin-top: 30px; display: flex; justify-content: center; gap: 20px; }

        button {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s;
            font-weight: bold;
        }

        #yesBtn { background: var(--deep-red); color: white; box-shadow: 0 5px 15px rgba(255, 10, 84, 0.4); }
        #yesBtn:hover { transform: scale(1.1); }

        #noBtn { background: #ced4da; color: #495057; position: relative; }

        .hidden { display: none; }

        /* Notes Styling */
        .notes-container {
            max-height: 400px;
            overflow-y: auto;
            margin-top: 20px;
            padding-right: 10px;
        }

        .note-card {
            background: white;
            padding: 15px;
            margin-bottom: 15px;
            border-bottom: 2px solid var(--primary-pink);
            transform: rotate(-1deg);
            transition: 0.3s;
            color: #590d22;
            font-size: 1.1rem;
            line-height: 1.4;
        }

        .note-card:nth-child(even) { transform: rotate(1deg); }
        .note-card:hover { transform: rotate(0deg) scale(1.02); background: var(--soft-white); }

        /* Custom Scrollbar */
        .notes-container::-webkit-scrollbar { width: 5px; }
        .notes-container::-webkit-scrollbar-thumb { background: var(--primary-pink); border-radius: 10px; }

        @keyframes heartFloat {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="heart-bg" id="heartBg"></div>

    <div class="container" id="app">
        <div id="page1">
            <h1>Do you love me? ❤️</h1>
            <p style="color: #666;">Choose wisely...</p>
            <div class="btn-group">
                <button id="yesBtn" onclick="goToLove()">Yes</button>
                <button id="noBtn" onclick="moveNo()" onmouseover="moveNo()">No</button>
            </div>
        </div>

        <div id="page2" class="hidden">
            <h1>I Knew It! 🥰</h1>
            <p style="color: #d63384; font-weight: bold;">Here is why you are my everything:</p>
            <div class="notes-container">
                <div class="note-card">❤️ I love you more than words could ever express.</div>
                <div class="note-card">🌹 You are my "another half" – the piece that makes me whole.</div>
                <div class="note-card">👀 I can see my entire future in your eyes.</div>
                <div class="note-card">👨‍👩‍👧‍👦 I want you to be the mother of my kids one day.</div>
                <div class="note-card">✨ You are the brightest part of my every single day.</div>
                <div class="note-card">🌍 To the world you may be one person, but to me you are the world.</div>
                <div class="note-card">💍 I can't wait for all the "forevers" we're going to have.</div>
                <div class="note-card">🏠 Home isn't a place, it's you.</div>
                <div class="note-card">🫂 Your hug is the only medicine I'll ever need.</div>
                <div class="note-card">💫 Every love story is beautiful, but ours is my favorite.</div>
                <div class="note-card">🌈 You make my life colorful even on the grayest days.</div>
                <div class="note-card">🍓 You are the sweetest thing that ever happened to me.</div>
                <div class="note-card">🔒 My heart is locked, and you have the only key.</div>
            </div>
        </div>
    </div>

    <script>
        // Make the "No" button run away!
        function moveNo() {
            const noBtn = document.getElementById('noBtn');
            const container = document.querySelector('.container');
            
            // Random position within the screen
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            
            // Optional: Alert if they somehow manage to click it
            noBtn.onclick = () => alert("Nice try! But you have to say Yes! 😉");
        }

        function goToLove() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            startHeartAnimation();
        }

        // Animated floating hearts
        function startHeartAnimation() {
            const bg = document.getElementById('heartBg');
            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.innerHTML = '❤️';
                    heart.style.position = 'absolute';
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.bottom = '-50px';
                    heart.style.fontSize = (Math.random() * 20 + 20) + 'px';
                    heart.style.animation = `heartFloat ${Math.random() * 3 + 2}s linear forwards`;
                    bg.appendChild(heart);
                    
                    // Remove heart after animation
                    setTimeout(() => heart.remove(), 5000);
                }, i * 200);
            }
        }
    </script>
</body>
</html>
