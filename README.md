<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajakan Ngegame</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Indie+Flower&display=swap');

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0e6d2;
            font-family: 'Indie Flower', cursive;
            margin: 0;
            transition: all 0.3s ease;
        }

        .container {
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            padding: 30px;
            text-align: center;
            max-width: 500px;
            width: 90%;
            position: relative;
            border: 2px solid #8B4513;
            background-image: linear-gradient(to bottom, transparent 95%, #8B4513 95%);
            background-size: 100% 10px;
            background-repeat: no-repeat;
            background-position: bottom;
        }

        .letter-header {
            display: flex;
            justify-content: space-between;
            border-bottom: 2px dashed #8B4513;
            padding-bottom: 10px;
            margin-bottom: 20px;
            font-family: 'Caveat', cursive;
            font-size: 1.2em;
        }

        .input-container {
            margin-top: 20px;
        }

        input {
            padding: 10px;
            width: 100%;
            margin-bottom: 15px;
            border: 2px dashed #8B4513;
            border-radius: 5px;
            font-family: 'Indie Flower', cursive;
            text-align: center;
        }

        button {
            padding: 10px 20px;
            background-color: #8B4513;
            color: #f0e6d2;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Indie Flower', cursive;
            font-weight: bold;
        }

        button:hover {
            background-color: #5D2E1A;
        }

        .button-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }

        #noButton {
            position: relative;
            background-color: #D2691E;
        }

        #yesButton {
            background-color: #228B22;
        }

        .gif-container {
            margin-top: 20px;
        }

        .hidden {
            display: none;
        }

        .signature {
            position: absolute;
            bottom: 20px;
            right: 20px;
            font-family: 'Caveat', cursive;
            font-size: 1.5em;
            color: #8B4513;
        }

        .watermark {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(-45deg);
            opacity: 0.1;
            font-size: 3em;
            font-family: 'Caveat', cursive;
            color: #8B4513;
        }
    </style>
</head>
<body>
    <!-- Tampilan 1: Halaman Awal -->
    <div class="container" id="welcomeScreen">
        <div class="letter-header">
            <div>📮 Surat Rahasia</div>
            <div id="currentDate"></div>
        </div>
        <h1>Halo! <i class="fas fa-envelope"></i></h1>
        <div class="input-container">
            <input type="text" id="nameInput" placeholder="Siapa nama kamu?">
            <button onclick="startLetter()">Buka Surat</button>
        </div>
        <div class="signature">From: We</div>
        <div class="watermark">RAHASIA</div>
    </div>

    <!-- Tampilan 2: Surat Ajakan -->
    <div class="container hidden" id="letterScreen">
        <div class="letter-header">
            <div>📮 Surat Rahasia</div>
            <div id="letterDate"></div>
        </div>
        <h2>Halo <span id="nameDisplay"></span>!</h2>
        <p>Lu lagi senggang gak ya? Hari minggu gue mau ngegame, lu mau ikut gak?</p>
        
        <div class="button-container">
            <button id="yesButton">MAU BANGET!</button>
            <button id="noButton">Gak Dulu</button>
        </div>

        <div class="gif-container">
            <img src="https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExYm1rN20wNzJrd3hvdGZmdzNlZTRqMG05eWI0NWFvaGlxaW9maDl2dCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/62cZr4Et8Mu8Mlrweh/giphy.gif" 
                 alt="Game GIF" width="250">
        </div>
        <div class="signature">From: We</div>
        <div class="watermark">RAHASIA</div>
    </div>

    <!-- Tampilan 3: Penutup -->
    <div class="container hidden" id="thankYouScreen">
        <div class="letter-header">
            <div>📮 Surat Rahasia</div>
            <div id="finalDate"></div>
        </div>
        <h1>Terima Kasih! 🎮</h1>
        <p>Oke siap, ditunggu hari minggu tengs!</p>
        <div class="gif-container">
            <img src="https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ3k4cW9rcXdjcjRybmZxb3JmOGQ3bWJvdjg3eXN3c2I5bGgwNm83NSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l1J3CbFgn5o7DGRuE/giphy.gif" 
                 alt="Thank You GIF" width="250">
        </div>
        <div class="signature">From: We</div>
        <div class="watermark">RAHASIA</div>
    </div>

    <script>
        const welcomeScreen = document.getElementById('welcomeScreen');
        const letterScreen = document.getElementById('letterScreen');
        const thankYouScreen = document.getElementById('thankYouScreen');
        const nameInput = document.getElementById('nameInput');
        const nameDisplay = document.getElementById('nameDisplay');
        const noButton = document.getElementById('noButton');
        const yesButton = document.getElementById('yesButton');
	        const currentDateEl = document.getElementById('currentDate');
        const letterDateEl = document.getElementById('letterDate');
        const finalDateEl = document.getElementById('finalDate');

        let yesButtonScale = 1;
        let moving = false;

        // Set tanggal saat ini di setiap layar
        function setCurrentDate() {
            const now = new Date();
            const options = { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            };
            const formattedDate = now.toLocaleDateString('id-ID', options);
            
            currentDateEl.textContent = formattedDate;
            letterDateEl.textContent = formattedDate;
            finalDateEl.textContent = formattedDate;
        }

        // Panggil fungsi set tanggal saat halaman dimuat
        setCurrentDate();

        function startLetter() {
            if (nameInput.value.trim() === '') {
                alert('Tolong masukkan namamu!');
                return;
            }
            
            nameDisplay.textContent = nameInput.value;
            welcomeScreen.classList.add('hidden');
            letterScreen.classList.remove('hidden');
        }

        noButton.addEventListener('click', () => {
            moving = true;
            moveButton();
            
            // Menambah ukuran tombol MAU BANGET!
            yesButtonScale += 0.2;
            yesButton.style.transform = `scale(${yesButtonScale})`;
            yesButton.style.transformOrigin = 'center';
        });

        yesButton.addEventListener('click', () => {
            letterScreen.classList.add('hidden');
            thankYouScreen.classList.remove('hidden');
        });

        function moveButton() {
            if (moving) {
                const randomX = Math.floor(Math.random() * (window.innerWidth - 100));
                const randomY = Math.floor(Math.random() * (window.innerHeight - 50));
                
                // Pastikan tombol tetap dalam layar
                noButton.style.position = 'fixed';
                noButton.style.left = randomX + 'px';
                noButton.style.top = randomY + 'px';
                
                setTimeout(moveButton, 1000);
            }
        }

        // Tambahan interaksi responsif
        window.addEventListener('resize', () => {
            // Reset posisi tombol jika layar diresize
            if (noButton.style.position === 'fixed') {
                noButton.style.left = '0px';
                noButton.style.top = '0px';
            }
        });
    </script>
</body>
</html>
