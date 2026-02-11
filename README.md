index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Suttumani ❤️</title>
    <style>
        body, html {
            margin: 0; padding: 0;
            font-family: 'Poppins', sans-serif;
            background-color: #fff0f3;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* --- LOCK SCREEN (Step 1) --- */
        #lock-screen {
            position: fixed; width: 100%; height: 100%;
            background: white; z-index: 1000;
            display: flex; flex-direction: column;
            justify-content: center; align-items: center;
        }
        #lock-screen input {
            padding: 15px; font-size: 1.2rem;
            border: 2px solid #ff4d6d; border-radius: 50px;
            text-align: center; outline: none; width: 250px;
        }

        /* --- POPUP MESSAGE (Step 2) --- */
        #popup-msg {
            display: none; position: fixed; top: 0; left: 0;
            width: 100%; height: 100%; background: white;
            z-index: 2000; justify-content: center; align-items: center;
            font-size: 2.2rem; color: #ff4d6d; font-weight: bold;
            text-align: center; padding: 20px;
        }

        #main-content { display: none; }
    </style>
</head>
<body>

    <div id="lock-screen">
        <h2>Enter Code ❤️</h2>
        <input type="password" id="passInput" placeholder="DDMMYYYY" oninput="checkPassword()">
    </div>

    <div id="popup-msg">ammede ponnu araaa💋💋</div>

    <div id="main-content">
        <h1>Site Loaded</h1>
    </div>

    <audio id="bgMusic" loop>
        <source src="music.mp3" type="audio/mpeg">
    </audio>

    <script>
        function checkPassword() {
            const input = document.getElementById('passInput').value;
            // The password check
            if (input === "01032025") {
                document.getElementById('lock-screen').style.display = 'none';
                const popup = document.getElementById('popup-msg');
                popup.style.display = 'flex';
                
                // Play music
                const music = document.getElementById('bgMusic');
                music.play().catch(()=>{});
                
                // Show popup for 3 seconds then load content
                setTimeout(() => {
                    popup.style.display = 'none';
                    document.getElementById('main-content').style.display = 'block';
                }, 3000);
            }
        }
    </script>
</body>
</html>
