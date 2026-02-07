# Propose-day-
<!DOCTYPE MISSION IMPRESS JANNN >
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For My Moon 🌙</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@400;600&display=swap');
        body { font-family: 'Poppins', sans-serif; background: #ffe4e6; overflow: hidden; touch-action: manipulation; }
        
        .spiral {
            width: 280px; height: 280px;
            background: repeating-conic-gradient(#ff4d6d 0 15deg, #fff 15deg 30deg);
            border-radius: 50%;
            animation: spin 1.5s linear infinite;
            margin: 0 auto;
            border: 8px solid #590d22;
        }
        @keyframes spin { 100% { transform: rotate(360deg); } }

        .glitch { font-size: 2.5rem; position: relative; color: #ff0000; font-weight: 900; }
        .glitch::before, .glitch::after { content: "SYSTEM ERROR"; position: absolute; top: 0; left: 0; width: 100%; height: 100%; }
        .glitch::before { left: 3px; text-shadow: -2px 0 #00ffff; clip: rect(24px, 550px, 90px, 0); animation: glitch-anim 2s infinite linear alternate-reverse; }
        .glitch::after { left: -3px; text-shadow: -2px 0 #ff00ff; clip: rect(85px, 550px, 140px, 0); animation: glitch-anim 3s infinite linear alternate-reverse; }
        @keyframes glitch-anim { 0% { clip: rect(10px, 9999px, 80px, 0); } 100% { clip: rect(5px, 9999px, 30px, 0); } }

        .game-item { position: absolute; font-size: 2.2rem; cursor: pointer; transition: transform 0.1s; user-select: none; }
        .screen { display: none; width: 100vw; height: 100vh; flex-direction: column; align-items: center; justify-content: center; position: absolute; top: 0; left: 0; padding: 20px; }
        .active { display: flex; }
        
        #toast { visibility: hidden; min-width: 250px; background-color: #ff4d6d; color: #fff; text-align: center; border-radius: 50px; padding: 16px; position: fixed; z-index: 100; bottom: 30px; font-weight: bold; box-shadow: 0 4px 15px rgba(0,0,0,0.2); }
        #toast.show { visibility: visible; animation: fadein 0.5s, fadeout 0.5s 2.5s; }
        @keyframes fadein { from {bottom: 0; opacity: 0;} to {bottom: 30px; opacity: 1;} }
        @keyframes fadeout { from {bottom: 30px; opacity: 1;} to {bottom: 0; opacity: 0;} }
    </style>
</head>
<body class="text-center">

    <audio id="bgMusic" src="https://files.catbox.moe/97808s.mp3" loop></audio>
    <div id="toast">Message</div>

    <div id="screen1" class="screen active bg-white">
        <div class="max-w-md">
            <h1 class="text-2xl text-[#590d22] font-bold leading-relaxed mb-6 italic">
                "You’re the moon that lights up my darkest nights and the melody that my heart refuses to stop humming. Will you stay by my side and turn every moment into a love song? 🌙✨💍"
            </h1>
            <div class="flex gap-4 relative w-full justify-center h-24 items-center">
                <button id="yesBtn" onclick="handleYesClick()" class="bg-[#ff4d6d] text-white px-8 py-3 rounded-full font-bold shadow-xl z-20">YES</button>
                <button id="noBtn" onclick="handleNo()" class="bg-gray-500 text-white px-8 py-3 rounded-full font-bold shadow-lg absolute right-10">NO</button>
            </div>
        </div>
    </div>

    <div id="screen2" class="screen bg-black text-white">
        <div class="spiral mb-10"></div>
        <h2 class="text-2xl font-bold animate-pulse text-[#ff4d6d]">Focus on the center... 🌀</h2>
        <p class="mt-4 text-lg">You are falling for me... again.</p>
        <p id="hypnoTimer" class="mt-8 text-5xl font-mono text-[#ff4d6d]">18</p>
    </div>

    <div id="screen3" class="screen bg-[#fff0f3]">
        <h1 class="text-4xl font-bold text-[#590d22] mb-12">I knew it! ❤️</h1>
        <div class="flex flex-col gap-6 w-full max-w-xs">
            <button onclick="showScreen('screen4')" class="bg-[#ff4d6d] text-white py-4 rounded-2xl font-bold text-xl shadow-lg">YES! 😍</button>
            <button onclick="showScreen('screen4')" class="bg-[#ff4d6d] text-white py-4 rounded-2xl font-bold text-xl shadow-lg">YES! 😘</button>
        </div>
    </div>

    <div id="screen4" class="screen bg-gray-50 overflow-hidden">
        <div class="fixed top-0 left-0 w-full bg-white p-4 shadow-md z-50 text-center">
            <p class="font-bold text-[#590d22]">Find 10 Hidden Rings! 💍</p>
            <p class="text-[#ff4d6d] font-bold">Found: <span id="score">0</span>/10</p>
        </div>
        <div id="gameArea" class="w-full h-full relative mt-16"></div>
    </div>

    <div id="screen5" class="screen bg-[#590d22] text-white">
        <div class="p-6 border-2 border-[#ff4d6d] rounded-3xl bg-[#4a0a1a] shadow-2xl">
            <h2 class="text-4xl font-['Dancing_Script'] text-[#ff4d6d] mb-6">Meri Jaan... ❤️</h2>
            <p class="text-2xl leading-relaxed mb-8">
                "Tum meri wo khushi ho jiske bina meri duniya adhuri hai. <br>
                Bas tera haath chahiye, zindagi bhar ke liye. <br>
                <b>Kya tum hamesha meri banogi?</b>" 💍
            </p>
            <button onclick="triggerGlitch()" class="bg-[#ff4d6d] text-white px-10 py-4 rounded-full font-bold text-xl animate-bounce">HAAN! 💋</button>
        </div>
    </div>

    <div id="screen6" class="screen bg-black text-green-500 font-mono">
        <div class="glitch">SYSTEM ERROR</div>
        <p class="text-white mt-10 text-xl">PLEASE WAIT 24 HOURS...</p>
        <div class="my-10 p-6 bg-gray-900 border-2 border-[#ff4d6d] rounded-xl text-center">
            <p class="text-[#ff4d6d] font-bold mb-2">NEXT SURPRISE IN:</p>
            <div id="countdown" class="text-4xl text-white font-bold tracking-widest">00:00:00</div>
            <p class="mt-4 text-sm text-gray-400">🍫 Chocolate Day Special 🍫</p>
        </div>
    </div>

    <script>
        let noClicks = 0;
        let ringsFound = 0;
        const bgMusic = document.getElementById('bgMusic');
        const noMessages = [
            "Are you sure? My heart is waiting! ❤️",
            "Don't be shy, say yes! ✨",
            "You know you want to... 😉",
            "I promise to make you smile every day! 🌹",
            "We are made for each other! 💍",
            "One more try? My love is infinite. 🌙",
            "You're my favorite person in the world! 💖",
            "Okay, I'm not giving up on you! 🔥"
        ];

        function showToast(msg) {
            const t = document.getElementById("toast");
            t.innerText = msg;
            t.className = "show";
            setTimeout(() => { t.className = t.className.replace("show", ""); }, 3000);
        }

        function showScreen(id) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            if(id === 'screen4') startRingGame();
        }

        function handleYesClick() {
            if (noClicks < 8) {
                showToast("Nice try! But you have to mean it... try again! 😉");
                // Reset slightly to make her play the game
                noClicks = 0;
                const noBtn = document.getElementById('noBtn');
                noBtn.style.position = 'static';
                noBtn.innerText = "NO";
            } else {
                startHypnosis();
            }
        }

        function handleNo() {
            if (noClicks < 8) {
                showToast(noMessages[noClicks]);
                const noBtn = document.getElementById('noBtn');
                const x = Math.random() * (window.innerWidth - 120);
                const y = Math.random() * (window.innerHeight - 80);
                noBtn.style.position = 'fixed';
                noBtn.style.left = x + 'px';
                noBtn.style.top = y + 'px';
                noClicks++;
            }
            if (noClicks === 8) {
                const noBtn = document.getElementById('noBtn');
                noBtn.style.position = 'static';
                noBtn.innerText = "YES";
                noBtn.classList.replace('bg-gray-500', 'bg-[#ff4d6d]');
                noBtn.onclick = startHypnosis;
            }
        }

        function startHypnosis() {
            bgMusic.play();
            showScreen('screen2');
            let time = 18;
            const hTimer = setInterval(() => {
                time--;
                document.getElementById('hypnoTimer').innerText = time;
                if(time <= 0) { clearInterval(hTimer); showScreen('screen3'); }
            }, 1000);
        }

        function startRingGame() {
            const area = document.getElementById('gameArea');
            area.innerHTML = '';
            const items = ['🧸','🌹','🍫','🎁','🍷','🎀','💖','🧁','💌','🎸'];
            for(let i=0; i<60; i++){
                let d = document.createElement('div');
                d.className = 'game-item opacity-40 grayscale';
                d.innerText = items[Math.floor(Math.random()*items.length)];
                setPos(d);
                area.appendChild(d);
            }
            for(let i=0; i<10; i++){
                let r = document.createElement('div');
                r.className = 'game-item ring';
                r.innerText = '💍';
                setPos(r);
                r.onclick = function() {
                    this.style.visibility = 'hidden';
                    ringsFound++;
                    document.getElementById('score').innerText = ringsFound;
                    if(ringsFound === 10) setTimeout(() => showScreen('screen5'), 500);
                };
                area.appendChild(r);
            }
        }

        function setPos(el) {
            el.style.left = Math.random() * (window.innerWidth - 60) + 'px';
            el.style.top = Math.random() * (window.innerHeight - 150) + 'px';
        }

        function triggerGlitch() {
            showScreen('screen6');
            updateCountdown();
            setInterval(updateCountdown, 1000);
        }

        function updateCountdown() {
            // Target: Feb 9th 2026 Midnight
            const target = new Date('February 9, 2026 00:00:00').getTime();
            const now = new Date().getTime();
            const diff = target - now;

            if (diff < 0) {
                document.getElementById('countdown').innerText = "HAPPY CHOCOLATE DAY! 🍫";
            } else {
                const d = Math.floor(diff / (1000 * 60 * 60 * 24));
                const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                const s = Math.floor((diff % (1000 * 60)) / 1000);
                
                // If more than 24 hours, show Days. If not, show H:M:S
                if (d > 0) {
                    document.getElementById('countdown').innerText = `${d}d ${h}h ${m}m`;
                } else {
                    document.getElementById('countdown').innerText = `${h}h ${m}m ${s}s`;
                }
            }
        }
    </script>
</body>
</html>
