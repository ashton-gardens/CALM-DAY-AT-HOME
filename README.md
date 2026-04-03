# qwertyuiooiuytrsasrtyuiopoiuytrewertyui543ertyuicvbnmnbvdtyujnbvcdtyujhvcdrtyujnbvfrtyuydsxcvbnmjhgfdertyuytrsxcvbnjhgfdrtyuhgfvbnmmcxdftygfdsw4rdszzdfbvcdrtyhjkliuhgfdserthjkiuytfdsert
be calm
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Midnight Desktop - Calm Music Edition</title>
    <style>
        :root {
            --monitor-frame: #1a1a1a;
            --screen-idle: #050505;
        }

        @keyframes rgb-cycle {
            0% { --accent-glow: #bc13fe; }
            20% { --accent-glow: #ff0055; }
            40% { --accent-glow: #ffaa00; }
            60% { --accent-glow: #00ff88; }
            80% { --accent-glow: #00d4ff; }
            100% { --accent-glow: #bc13fe; }
        }

        body {
            margin: 0;
            height: 100vh;
            background-color: #050505;
            display: flex;
            justify-content: center;
            align-items: flex-end;
            font-family: 'Segoe UI', sans-serif;
            overflow: hidden;
            user-select: none;
            animation: rgb-cycle 10s infinite linear;
        }

        .room {
            position: relative;
            width: 100%; height: 100%;
            display: flex; justify-content: center; align-items: center;
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(0,0,0,0) 20%, #050505 100%),
                radial-gradient(circle at 50% 50%, var(--accent-glow) 0%, transparent 60%),
                linear-gradient(30deg, #0f0f1a 12%, transparent 12.5%, transparent 87%, #0f0f1a 87.5%, #0f0f1a),
                linear-gradient(150deg, #0f0f1a 12%, transparent 12.5%, transparent 87%, #0f0f1a 87.5%, #0f0f1a),
                linear-gradient(60deg, #161625 25%, transparent 25.5%, transparent 75%, #161625 75%, #161625);
            background-size: 100% 100%, 100% 100%, 80px 140px, 80px 140px, 80px 140px;
        }

        .desk-surface {
            position: absolute; bottom: 0; width: 100%; height: 60px;
            background: #080808; border-top: 3px solid var(--accent-glow);
            box-shadow: 0 -10px 30px var(--accent-glow); opacity: 0.8;
        }

        .monitor-container { position: relative; z-index: 10; display: flex; flex-direction: column; align-items: center; }
        .monitor-frame { width: 650px; height: 400px; background: var(--monitor-frame); padding: 15px; border-radius: 8px; border: 2px solid #333; }
        .screen { width: 100%; height: 100%; background: var(--screen-idle); border-radius: 4px; position: relative; overflow: hidden; display: flex; flex-direction: column; }
        .desktop-area { flex: 1; position: relative; background: linear-gradient(to bottom, #0a0b1e, #16213e); background-size: cover; background-position: center; }

        .folder-icon { position: absolute; top: 30px; right: 30px; display: flex; flex-direction: column; align-items: center; cursor: pointer; color: white; transition: 0.2s; }
        .folder-emoji { font-size: 50px; }
        .folder-text { font-size: 14px; font-weight: bold; margin-top: 5px; text-shadow: 0 0 8px var(--accent-glow), 0 2px 4px black; }

        .taskbar { height: 38px; background: rgba(0,0,0,0.95); display: flex; align-items: center; padding: 0 10px; gap: 12px; border-top: 1px solid rgba(255,255,255,0.1); z-index: 100; }
        .app-icon { width: 26px; height: 26px; cursor: pointer; transition: 0.2s; display: flex; align-items: center; justify-content: center; font-size: 18px; }
        .app-icon:hover { transform: scale(1.2) translateY(-3px); }

        .window { position: absolute; top: 10px; left: 10px; right: 10px; bottom: 10px; background: #000; border-radius: 8px; display: none; flex-direction: column; border: 1px solid #444; box-shadow: 0 10px 30px rgba(0,0,0,0.8); z-index: 20; }
        .win-header { padding: 6px 12px; background: #222; display: flex; justify-content: space-between; font-size: 11px; color: #aaa; border-bottom: 1px solid #333; }
        .win-body { flex: 1; padding: 15px; color: white; overflow-y: auto; font-size: 13px; }

        #live-clock { margin-left: auto; font-size: 11px; color: #eee; font-family: monospace; }

        .setting-row { margin-bottom: 20px; border-bottom: 1px solid #222; padding-bottom: 10px; }
        .btn { background: #4ea8de; border: none; color: white; padding: 5px 15px; border-radius: 4px; cursor: pointer; }
        .instructions { font-size: 11px; color: #aaa; margin-top: 5px; line-height: 1.4; }

        .game-canvas { flex: 1; background: #000; position: relative; overflow: hidden; }
        .star { position: absolute; width: 2px; height: 2px; background: white; border-radius: 50%; }
        .neon-plant { position: absolute; bottom: 0; width: 2px; transition: height 1s; }
        .drop { position: absolute; background: rgba(255,255,255,0.4); width: 1px; height: 10px; animation: fall linear infinite; }
        @keyframes fall { to { transform: translateY(350px); } }
        canvas { width: 100%; height: 100%; cursor: crosshair; }
        .tile { width: 40px; height: 40px; border-radius: 4px; cursor: pointer; display: inline-block; margin: 5px; }
        .leaf { position: absolute; font-size: 14px; pointer-events: none; transition: 2s linear; }

        .monitor-stand { width: 60px; height: 50px; background: #111; }
        .monitor-base { width: 200px; height: 10px; background: #000; box-shadow: 0 -2px 15px var(--accent-glow); }
        #file-input { display: none; }
    </style>
</head>
<body>

<audio id="bgMusic" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<div class="room">
    <div class="monitor-container">
        <div class="monitor-frame">
            <div class="screen">
                <div class="desktop-area" id="desktop">
                    <div class="folder-icon" onclick="openApp('wallpaper-win')">
                        <span class="folder-emoji">📁</span>
                        <span class="folder-text">Wallpapers</span>
                    </div>

                    <div id="settings-win" class="window">
                        <div class="win-header"><span>System Settings</span><span style="cursor:pointer" onclick="closeApp('settings-win')">✖</span></div>
                        <div class="win-body">
                            <div class="setting-row">
                                <h3>🎵 Calm Music</h3>
                                <button class="btn" onclick="toggleMusic()" id="musicBtn">Play Music</button>
                                <div style="margin-top:10px;">
                                    Volume: <input type="range" min="0" max="1" step="0.1" value="0.5" onchange="updateVolume(this.value)">
                                </div>
                            </div>
                            <div class="setting-row">
                                <h3>🎮 Game Guides</h3>
                                <p class="instructions">✨ <b>Star Weave:</b> Click to weave stars.</p>
                                <p class="instructions">🌵 <b>Neon Grow:</b> Click to grow neon plants.</p>
                                <p class="instructions">🌧️ <b>Rain:</b> Click to toggle the downpour.</p>
                                <p class="instructions">🎨 <b>Sketch:</b> Drag mouse to draw.</p>
                                <p class="instructions">🧩 <b>Tiles:</b> Click tiles to change color.</p>
                                <p class="instructions">🍃 <b>Breeze:</b> Click to release leaves.</p>
                            </div>
                        </div>
                    </div>

                    <div id="wallpaper-win" class="window">
                        <div class="win-header"><span>Wallpaper Settings</span><span style="cursor:pointer" onclick="closeApp('wallpaper-win')">✖</span></div>
                        <div class="win-body"><label for="file-input" style="background:#4ea8de; padding:10px; border-radius:4px; cursor:pointer; color:white; display:block; text-align:center;">📁 Upload Image</label>
                        <input type="file" id="file-input" accept="image/*" onchange="uploadWallpaper(event)"></div>
                    </div>

                    <div id="star-win" class="window"><div class="win-header"><span>StarWeave.sys</span><span onclick="closeApp('star-win')">✖</span></div><div class="game-canvas" onclick="addStar(event)"></div></div>
                    <div id="neon-win" class="window"><div class="win-header"><span>NEON_GROW.app</span><span onclick="closeApp('neon-win')">✖</span></div><div id="neon-game" class="game-canvas" onclick="growNeon(event)"></div></div>
                    <div id="rain-win" class="window"><div class="win-header"><span>RAIN_CHILL.exe</span><span onclick="closeApp('rain-win')">✖</span></div><div id="rain-game" class="game-canvas" onclick="toggleRain()"></div></div>
                    <div id="sketch-win" class="window"><div class="win-header"><span>MidnightSketch.pad</span><span onclick="closeApp('sketch-win')">✖</span></div><canvas id="sketchCanvas"></canvas></div>
                    <div id="logic-win" class="window"><div class="win-header"><span>LogicTiles.bin</span><span onclick="closeApp('logic-win')">✖</span></div><div id="logic-game" class="game-canvas" style="padding:20px; text-align:center;"></div></div>
                    <div id="breeze-win" class="window"><div class="win-header"><span>Breeze.toy</span><span onclick="closeApp('breeze-win')">✖</span></div><div id="breeze-game" class="game-canvas" onclick="spawnLeaf(event)"></div></div>
                </div>

                <div class="taskbar">
                    <span class="app-icon" onclick="openApp('settings-win')">⚙️</span>
                    <span class="app-icon" onclick="openApp('star-win')">✨</span>
                    <span class="app-icon" onclick="openApp('neon-win')">🌵</span>
                    <span class="app-icon" onclick="openApp('rain-win')">🌧️</span>
                    <span class="app-icon" onclick="openApp('sketch-win')">🎨</span>
                    <span class="app-icon" onclick="openApp('logic-win')">🧩</span>
                    <span class="app-icon" onclick="openApp('breeze-win')">🍃</span>
                    <div id="live-clock">00:00:00</div>
                </div>
            </div>
        </div>
        <div class="monitor-stand"></div><div class="monitor-base"></div>
    </div>
    <div class="desk-surface"></div>
</div>

<script>
    const music = document.getElementById('bgMusic');
    let isPlaying = false;

    function toggleMusic() {
        if (isPlaying) { music.pause(); document.getElementById('musicBtn').innerText = "Play Music";
        } else { music.play(); document.getElementById('musicBtn').innerText = "Stop Music"; }
        isPlaying = !isPlaying;
    }
    function updateVolume(val) { music.volume = val; }

    function updateTime() {
        const now = new Date();
        document.getElementById('live-clock').innerText = now.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit', second: '2-digit' });
    }
    setInterval(updateTime, 1000); updateTime();

    function openApp(id) {
        document.querySelectorAll('.window').forEach(w => w.style.display = 'none');
        document.getElementById(id).style.display = 'flex';
        if(id === 'sketch-win') initSketch();
        if(id === 'logic-win') initLogic();
    }
    function closeApp(id) { document.getElementById(id).style.display = 'none'; }

    function uploadWallpaper(event) {
        const file = event.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = e => document.getElementById('desktop').style.backgroundImage = `url('${e.target.result}')`;
            reader.readAsDataURL(file);
        }
    }

    // GAME LOGICS
    function addStar(e) {
        const s = document.createElement('div'); s.className = 'star';
        s.style.left = e.offsetX + 'px'; s.style.top = e.offsetY + 'px';
        e.target.appendChild(s);
    }
    function growNeon(e) {
        const p = document.createElement('div'); p.className = 'neon-plant';
        p.style.left = e.offsetX + 'px'; p.style.height = '0px';
        const color = `hsl(${Math.random()*360}, 80%, 60%)`;
        p.style.background = color; p.style.boxShadow = `0 0 10px ${color}`;
        e.target.appendChild(p);
        setTimeout(() => p.style.height = (Math.random()*150 + 50) + 'px', 50);
    }
    let rainOn = false;
    function toggleRain() {
        rainOn = !rainOn; const container = document.getElementById('rain-game');
        if(rainOn) { for(let i=0; i<60; i++) {
            const d = document.createElement('div'); d.className = 'drop';
            d.style.left = Math.random()*100+'%'; d.style.animationDuration = (Math.random()*0.5+0.5)+'s';
            container.appendChild(d);
        }} else { container.innerHTML = ""; }
    }
    function initSketch() {
        const canvas = document.getElementById('sketchCanvas'); const ctx = canvas.getContext('2d');
        canvas.width = canvas.offsetWidth; canvas.height = canvas.offsetHeight;
        let drawing = false;
        canvas.onmousedown = () => drawing = true; canvas.onmouseup = () => { drawing = false; ctx.beginPath(); };
        canvas.onmousemove = (e) => {
            if(!drawing) return; ctx.lineWidth = 2; ctx.lineCap = 'round'; ctx.strokeStyle = '#bc13fe';
            ctx.lineTo(e.offsetX, e.offsetY); ctx.stroke(); ctx.beginPath(); ctx.moveTo(e.offsetX, e.offsetY);
        };
    }
    function initLogic() {
        const g = document.getElementById('logic-game'); g.innerHTML = "";
        const colors = ['#bc13fe', '#4ea8de', '#00f2ff', '#ff00ff'];
        for(let i=0; i<12; i++) {
            const t = document.createElement('div'); t.className = 'tile';
            t.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
            t.onclick = () => t.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
            g.appendChild(t);
        }
    }
    function spawnLeaf(e) {
        const l = document.createElement('div'); l.className = 'leaf';
        l.innerText = '🍃'; l.style.left = e.offsetX + 'px'; l.style.top = e.offsetY + 'px';
        document.getElementById('breeze-game').appendChild(l);
        setTimeout(() => { l.style.left = (e.offsetX + 300) + 'px'; l.style.top = (e.offsetY + 100) + 'px'; l.style.opacity = '0'; }, 100);
        setTimeout(() => l.remove(), 2100);
    }
</script>

</body>
</html>
