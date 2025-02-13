<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menu Free Fire - Tối ưu hóa & Nhạc Remix</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #222;
            color: white;
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Nút mở menu */
        button {
            padding: 12px 25px;
            font-size: 18px;
            cursor: pointer;
            background: linear-gradient(45deg, #ff416c, #ff4b2b);
            color: white;
            border: none;
            border-radius: 8px;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 10px rgba(255, 75, 43, 0.8);
        }

        /* Hiệu ứng menu */
        #menu {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            background: rgba(51, 51, 51, 0.9);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.2);
            width: 320px;
            text-align: left;
            transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
            opacity: 0;
            backdrop-filter: blur(10px);
        }

        #menu.visible {
            transform: translate(-50%, -50%) scale(1);
            opacity: 1;
        }

        .menu-header {
            background: #ff4b2b;
            padding: 12px;
            text-align: center;
            border-radius: 8px;
            margin-bottom: 15px;
        }

        .menu-title {
            font-weight: bold;
            color: white;
        }

        .menu-options label {
            display: block;
            margin: 10px 0;
            font-size: 16px;
        }

        /* Thanh trượt */
        .slider-container {
            margin: 15px 0;
        }

        input[type="range"] {
            width: 100%;
            cursor: pointer;
        }

        /* Hiệu ứng tuyết rơi */
        .snowflake {
            position: absolute;
            top: -10px;
            background: white;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            opacity: 0.7;
            animation: snowfall linear infinite;
        }

        @keyframes snowfall {
            0% {
                transform: translateY(0);
                opacity: 0.8;
            }
            100% {
                transform: translateY(100vh);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <button id="toggleMenu">Mở Menu</button>

    <div id="menu">
        <h3>Free Fire - MENU BY SPERNEW IOS 🍎</h3>
        <div class="menu-header">
            <span class="menu-title">MENU CHỨC NĂNG</span>
        </div>
        <p>Mua Panel Tại Zalo: <strong>0817058375</strong></p>
        
        <div class="menu-options">
            <label><input type="checkbox" id="aimlockmode"> AIMLOCK MODE</label>
            <label><input type="checkbox" id="nhaytam"> NHẠY TÂM</label>
            <label><input type="checkbox" id="cungtam"> CỨNG TÂM</label>
            <label><input type="checkbox" id="locktam"> LOCK TÂM</label>
            <label><input type="checkbox" id="buffman"> BUFF MÀN</label>
        </div>

        <div class="slider-container">
            <label for="sensitivity">Tăng Nhạy: <span id="sensitivityValue">50%</span></label>
            <input type="range" id="sensitivity" min="10" max="100" value="50">
        </div>

        <div class="slider-container">
            <label for="lightAim">Nhẹ Tâm: <span id="lightAimValue">50%</span></label>
            <input type="range" id="lightAim" min="10" max="100" value="50">
        </div>

        <button id="optimizeDevice">Tối Ưu Thiết Bị</button>

        <div class="music-container">
            <h3>🎵 Nhạc Remix 🎵</h3>
            <select id="musicSelector">
                <option value="https://thanhdieu.com/files/Em-Nào-Có-Tội.mp3">Em Nào Có Tội</option>
                <option value="https://files.catbox.moe/hkqk6x.mp3">Sky</option>
                <option value="https://files.catbox.moe/gvqgma.mp3">Em Đã Xa Anh</option>
            </select>
            <audio id="audioPlayer" controls>
                <source id="audioSource" src="https://thanhdieu.com/files/Em-Nào-Có-Tội.mp3" type="audio/mpeg">
            </audio>
        </div>
    </div>

    <script>
        const toggleMenuButton = document.getElementById("toggleMenu");
        const menu = document.getElementById("menu");

        toggleMenuButton.addEventListener("click", function() {
            menu.classList.toggle("visible");
            toggleMenuButton.textContent = menu.classList.contains("visible") ? "Đóng Menu" : "Mở Menu";
        });

        function updateSliderValue(sliderId, valueId) {
            const slider = document.getElementById(sliderId);
            const valueDisplay = document.getElementById(valueId);
            valueDisplay.innerText = slider.value + "%";
            slider.addEventListener("input", function() {
                valueDisplay.innerText = this.value + "%";
            });
        }

        updateSliderValue("sensitivity", "sensitivityValue");
        updateSliderValue("lightAim", "lightAimValue");

        document.getElementById("musicSelector").addEventListener("change", function() {
            let audioPlayer = document.getElementById("audioPlayer");
            let audioSource = document.getElementById("audioSource");

            audioSource.src = this.value;
            audioPlayer.load();
            audioPlayer.play();
        });

        // Tạo hiệu ứng tuyết rơi
        function createSnowflake() {
            const snowflake = document.createElement("div");
            snowflake.classList.add("snowflake");
            document.body.appendChild(snowflake);
            snowflake.style.left = Math.random() * window.innerWidth + "px";
            snowflake.style.animationDuration = (Math.random() * 5 + 5) + "s";
            snowflake.style.width = snowflake.style.height = Math.random() * 6 + 4 + "px";
            
            setTimeout(() => snowflake.remove(), 10000);
        }

        setInterval(createSnowflake, 200);
    </script>

</body>
</html>
