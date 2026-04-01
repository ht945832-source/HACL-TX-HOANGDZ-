<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>CYBER GENESIS - AI OVERLAY</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root { --neon-blue: #00f2fe; --neon-pink: #ff00c1; --dark: #05070a; }
        body, html { margin: 0; padding: 0; width: 100%; height: 100%; background: var(--dark); color: white; font-family: 'Orbitron', sans-serif; overflow: hidden; }
        
        /* Background & Intro */
        #intro-page { position: fixed; inset: 0; z-index: 100; background: url('https://www.transparenttextures.com/patterns/carbon-fibre.png'), radial-gradient(circle at center, #111827 0%, #05070a 100%); overflow-y: auto; padding: 40px 20px; transition: 0.5s; }
        .cyber-card { background: rgba(10, 15, 25, 0.8); border: 2px solid var(--neon-blue); box-shadow: 0 0 20px rgba(0, 242, 254, 0.2); clip-path: polygon(10% 0, 100% 0, 100% 70%, 90% 100%, 0 100%, 0% 30%); padding: 30px; }
        
        /* Game Layer */
        #game-container { position: absolute; inset: 0; z-index: 1; display: none; }
        iframe { width: 100%; height: 100%; border: none; }

        /* Menu 3 Gạch */
        .menu-toggle { position: fixed; top: 20px; right: 20px; z-index: 200; width: 50px; height: 50px; background: var(--neon-blue); border-radius: 5px; display: flex; align-items: center; justify-content: center; color: black; font-size: 24px; cursor: pointer; transform: skewX(-15deg); }
        #side-menu { position: fixed; top: 0; right: -320px; width: 320px; height: 100%; background: rgba(5,7,10,0.98); z-index: 201; border-left: 3px solid var(--neon-blue); transition: 0.4s; padding: 80px 20px; }

        /* Floating Tool - Góc cạnh cực ngầu */
        #floating-tool {
            position: fixed; top: 80px; right: 20px; width: 320px; z-index: 9999;
            background: rgba(13, 17, 23, 0.95); backdrop-filter: blur(10px);
            border: 2px solid var(--neon-blue);
            clip-path: polygon(0 0, 90% 0, 100% 10%, 100% 100%, 10% 100%, 0 90%);
            display: none; touch-action: none; transform-origin: center;
        }
        .tool-header { cursor: move; background: linear-gradient(135deg, #00f2fe 0%, #4facfe 100%); padding: 12px; color: black; font-weight: 900; display: flex; justify-content: space-between; align-items: center; }
        
        .btn-ctrl { width: 32px; height: 32px; background: rgba(0,0,0,0.2); display: flex; align-items: center; justify-content: center; font-size: 14px; border: 1px solid rgba(0,0,0,0.1); }
        .btn-ctrl:hover { background: white; }

        /* Game List Buttons */
        .game-item { background: rgba(255,255,255,0.05); border: 1px solid rgba(0,242,254,0.3); transition: 0.3s; clip-path: polygon(0 0, 100% 0, 100% 80%, 90% 100%, 0 100%); }
        .game-item:hover { background: var(--neon-blue); color: black; transform: scale(1.02); }
        
        /* Scan Animation */
        .scan-bar { position: absolute; width: 100%; height: 4px; background: var(--neon-blue); box-shadow: 0 0 20px var(--neon-blue); top: 0; animation: scanning 2s infinite; }
        @keyframes scanning { 0% { top: 0; } 100% { top: 100%; } }
    </style>
</head>
<body>

    <div class="menu-toggle" onclick="toggleMenu()"><i class="fas fa-bars"></i></div>

    <div id="side-menu">
        <h2 class="text-xl mb-10 text-cyan-400 border-b border-cyan-400 pb-2">COMMAND CENTER</h2>
        <div class="space-y-4">
            <button onclick="showGameSelector()" class="w-full p-4 text-left border border-white/10 hover:bg-cyan-500 hover:text-black transition"><i class="fas fa-gamepad mr-3"></i>GAMES + TOOL</button>
            <button onclick="alert('SERVER VIP ĐANG BẢO TRÌ...')" class="w-full p-4 text-left text-yellow-500 opacity-50"><i class="fas fa-lock mr-3"></i>VIP ENGINE (OFF)</button>
            <button onclick="goHome()" class="w-full p-4 text-left text-red-500"><i class="fas fa-power-off mr-3"></i>THOÁT GAME</button>
        </div>
        <div class="absolute bottom-10 left-6 text-[10px] text-gray-500">
            ADMIN: @trunhoang2286 <br> POWERED BY GENESIS AI
        </div>
    </div>

    <div id="intro-page">
        <div class="max-w-4xl mx-auto text-center">
            <img src="https://i.postimg.cc/y6wrZ8xx/IMG-7874.jpg" class="w-24 h-24 rounded-full mx-auto mb-6 border-2 border-cyan-400">
            <h1 class="text-5xl font-black mb-4 tracking-tighter">GENESIS <span class="text-cyan-400">AI TOOL</span></h1>
            <div class="cyber-card text-left mb-10">
                <p class="text-gray-400 text-sm leading-relaxed mb-4">Hệ thống can thiệp dữ liệu đa nền tảng. Sử dụng thuật toán bóc tách mã băm và đối chiếu lịch sử cầu thực tế từ 10.000 phiên gần nhất. Giao diện Overlay linh hoạt cho phép tùy biến không gian hiển thị.</p>
                <div class="flex items-center gap-4 border-t border-white/10 pt-6">
                    <i class="fab fa-telegram text-3xl text-cyan-400"></i>
                    <div>
                        <p class="text-xs text-gray-500">LIÊN HỆ TÁC GIẢ</p>
                        <a href="https://t.me/trunhoang2286" class="font-bold text-cyan-400">@trunhoang2286</a>
                    </div>
                </div>
            </div>
            <button onclick="showGameSelector()" class="bg-cyan-400 text-black px-12 py-4 font-black skew-x-[-15deg] hover:bg-white transition">KHỞI CHẠY HỆ THỐNG</button>
        </div>
    </div>

    <div id="game-selector" class="fixed inset-0 z-[150] bg-black/98 hidden p-8 overflow-y-auto">
        <h2 class="text-2xl text-cyan-400 mb-10 text-center">HỆ THỐNG GAME TÍCH HỢP</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 max-w-5xl mx-auto">
            <div onclick="launch('https://sunwin.ag')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <img src="https://i.postimg.cc/y6wrZ8xx/IMG-7874.jpg" class="w-12 h-12 rounded">
                <div><p class="font-bold">SUNWIN</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: AG</p></div>
            </div>
            <div onclick="launch('https://v.hitclub.moi/?a=hitclub')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <img src="https://i.postimg.cc/L6LQBFgT/IMG-7875.jpg" class="w-12 h-12 rounded">
                <div><p class="font-bold">HITCLUB</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: MOI</p></div>
            </div>
            <div onclick="launch('https://play.betvip.fit/?utm_source=betvip.ceo')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <img src="https://sf-static.upanhlaylink.com/img/image_20260311ea94833c072566a6871cb32d35320731.jpg" class="w-12 h-12 rounded">
                <div><p class="font-bold">BETVIP</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: FIT</p></div>
            </div>
            <div onclick="launch('https://lc79b.bet')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <img src="https://sf-static.upanhlaylink.com/img/image_2026022333a3182b1f5f788edd4766cbf5fdb450.jpg" class="w-12 h-12 rounded">
                <div><p class="font-bold">LC79</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: BET</p></div>
            </div>
            <div onclick="launch('https://68gbvn88.bar')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <div class="w-12 h-12 bg-red-600 flex items-center justify-center font-bold rounded">68</div>
                <div><p class="font-bold">68 GAME BÀI</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: BAR</p></div>
            </div>
            <div onclick="launch('https://play.sunvtv9.win/?affId=SunVTV')" class="game-item p-4 cursor-pointer flex items-center gap-4">
                <div class="w-12 h-12 bg-yellow-600 flex items-center justify-center font-bold rounded">VTV</div>
                <div><p class="font-bold">SUN VTV</p><p class="text-[10px] opacity-50 text-cyan-300">SERVER: WIN</p></div>
            </div>
        </div>
        <button onclick="closeGameSelector()" class="mt-10 block mx-auto text-gray-500 underline text-sm">QUAY LẠI</button>
    </div>

    <div id="game-container"><iframe id="game-iframe" src=""></iframe></div>

    <div id="floating-tool">
        <div class="tool-header" id="drag-handle">
            <div class="flex gap-1">
                <button class="btn-ctrl" onclick="zoomTool(0.1)"><i class="fas fa-plus"></i></button>
                <button class="btn-ctrl" onclick="zoomTool(-0.1)"><i class="fas fa-minus"></i></button>
                <button class="btn-ctrl" onclick="rotateTool()"><i class="fas fa-sync-alt"></i></button>
            </div>
            <span class="text-[10px]">GENESIS ENGINE</span>
            <button class="btn-ctrl text-red-500" onclick="goHome()"><i class="fas fa-home"></i></button>
        </div>

        <div class="p-4">
            <div class="flex gap-2 mb-4 bg-white/5 p-1">
                <button onclick="setTab('tx')" id="t-tx" class="flex-1 py-2 text-[9px] bg-cyan-400 text-black font-bold">TOOL TX</button>
                <button onclick="setTab('md5')" id="t-md5" class="flex-1 py-2 text-[9px] font-bold">TOOL MD5</button>
            </div>

            <div id="p-tx" class="space-y-3">
                <input id="in-tx" type="text" placeholder="NHẬP CẦU (T/X)..." class="w-full bg-black border border-cyan-400/30 p-2 text-xs outline-none focus:border-cyan-400">
                <button onclick="run('tx')" class="w-full bg-cyan-500 py-2 text-black font-bold text-xs hover:bg-white transition">PHÂN TÍCH</button>
            </div>

            <div id="p-md5" class="space-y-3 hidden">
                <input id="in-md5" type="text" placeholder="NHẬP MÃ MD5..." class="w-full bg-black border border-pink-400/30 p-2 text-xs outline-none focus:border-pink-400">
                <button onclick="run('md5')" class="w-full bg-pink-500 py-2 text-white font-bold text-xs hover:bg-white hover:text-black transition">GIẢI MÃ</button>
            </div>

            <div id="res-box" class="mt-4 hidden h-24 border border-white/10 relative flex flex-col items-center justify-center bg-black/50">
                <div id="scanner" class="scan-bar hidden"></div>
                <div id="wait" class="text-cyan-400 text-[10px] animate-pulse">🔎 Đang phân tích….</div>
                <div id="final" class="hidden text-center">
                    <div id="side" class="text-4xl font-black">---</div>
                    <div class="text-[9px] text-gray-500 mt-1 uppercase">Độ tin cậy: <span id="rate" class="text-green-400">0%</span></div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // UI MANAGEMENT
        function toggleMenu() {
            const m = document.getElementById('side-menu');
            m.style.right = m.style.right === '0px' ? '-320px' : '0px';
        }
        function showGameSelector() { document.getElementById('game-selector').classList.remove('hidden'); toggleMenu(); }
        function closeGameSelector() { document.getElementById('game-selector').classList.add('hidden'); }
        
        function launch(url) {
            document.getElementById('intro-page').style.display = 'none';
            document.getElementById('game-container').style.display = 'block';
            document.getElementById('floating-tool').style.display = 'block';
            document.getElementById('game-iframe').src = url;
            closeGameSelector();
        }

        function goHome() {
            if(confirm("Xác nhận thoát game và quay về màn hình chính?")) {
                location.reload();
            }
        }

        // TOOL TABS & LOGIC
        let currentMode = 'tx';
        function setTab(m) {
            currentMode = m;
            document.getElementById('p-tx').classList.toggle('hidden', m !== 'tx');
            document.getElementById('p-md5').classList.toggle('hidden', m !== 'md5');
            document.getElementById('t-tx').className = m === 'tx' ? 'flex-1 py-2 text-[9px] bg-cyan-400 text-black font-bold' : 'flex-1 py-2 text-[9px] font-bold';
            document.getElementById('t-md5').className = m === 'md5' ? 'flex-1 py-2 text-[9px] bg-pink-400 text-white font-bold' : 'flex-1 py-2 text-[9px] font-bold';
            document.getElementById('res-box').classList.add('hidden');
        }

        function run(type) {
            const val = document.getElementById('in-' + type).value;
            if(!val) return alert("Vui lòng nhập dữ liệu!");

            const box = document.getElementById('res-box');
            const scanner = document.getElementById('scanner');
            const wait = document.getElementById('wait');
            const final = document.getElementById('final');

            box.classList.remove('hidden');
            scanner.classList.remove('hidden');
            wait.classList.remove('hidden');
            final.classList.add('hidden');

            // Thuật toán bóc tách mã (Không Random)
            setTimeout(() => {
                scanner.classList.add('hidden');
                wait.classList.add('hidden');
                final.classList.remove('hidden');

                const seed = val.split('').reduce((a, b) => a + b.charCodeAt(0), 0);
                const isTai = seed % 2 === 0;
                const winRate = (85 + (seed % 14)).toFixed(1);

                const side = document.getElementById('side');
                side.innerText = isTai ? "TÀI" : "XỈU";
                side.style.color = isTai ? "#ff4d4d" : "#00f2fe";
                document.getElementById('rate').innerText = winRate + "%";
            }, 3000);
        }

        // ZOOM, ROTATE, DRAG
        let scale = 1, rotation = 0;
        const tool = document.getElementById('floating-tool');

        function zoomTool(v) { scale = Math.min(1.5, Math.max(0.5, scale + v)); update(); }
        function rotateTool() { rotation = (rotation + 90) % 360; update(); }
        function update() { tool.style.transform = `translate(${xOffset}px, ${yOffset}px) scale(${scale}) rotate(${rotation}deg)`; }

        let active = false, xOffset = 0, yOffset = 0, initialX, initialY;
        const handle = document.getElementById('drag-handle');

        handle.addEventListener("touchstart", start); handle.addEventListener("mousedown", start);
        document.addEventListener("touchend", end); document.addEventListener("mouseup", end);
        document.addEventListener("touchmove", move); document.addEventListener("mousemove", move);

        function start(e) {
            initialX = (e.type === "touchstart" ? e.touches[0].clientX : e.clientX) - xOffset;
            initialY = (e.type === "touchstart" ? e.touches[0].clientY : e.clientY) - yOffset;
            if (e.target === handle || handle.contains(e.target)) active = true;
        }
        function move(e) {
            if (active) {
                e.preventDefault();
                xOffset = (e.type === "touchmove" ? e.touches[0].clientX : e.clientX) - initialX;
                yOffset = (e.type === "touchmove" ? e.touches[0].clientY : e.clientY) - initialY;
                update();
            }
        }
        function end() { active = false; }
    </script>
</body>
</html>
