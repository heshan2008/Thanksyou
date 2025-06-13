<html lang="si">
<head>
    <meta charset="UTF-8">
    <title>ස්තුතියි!</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Sinhala&display=swap');

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html, body {
            height: 100%;
            font-family: 'Noto Sans Sinhala', sans-serif;
            overflow: hidden;
        }

        body {
            background: linear-gradient(-45deg, #ffecd2, #fcb69f, #ffe9b8, #ffcccb);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            padding: 20px;
            position: relative;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(10px);
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 700px;
            width: 100%;
            z-index: 1;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            color: #e67e22;
            margin-bottom: 20px;
        }

        p {
            color: #444;
            font-size: 18px;
            margin-bottom: 15px;
        }

        input[type="text"] {
            padding: 12px 20px;
            width: 80%;
            border-radius: 10px;
            border: 1px solid #ccc;
            font-size: 16px;
            margin-bottom: 10px;
            outline: none;
            transition: 0.3s;
        }

        input[type="text"]:focus {
            border-color: #f39c12;
            box-shadow: 0 0 8px #f39c1260;
        }

        .error {
            color: red;
            font-size: 14px;
            margin-top: 5px;
            min-height: 20px;
        }

        button {
            padding: 12px 25px;
            background: #f39c12;
            border: none;
            color: white;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s ease;
            margin-top: 10px;
        }

        button:hover {
            background: #e67e22;
        }

        footer {
            position: absolute;
            bottom: 10px;
            font-size: 14px;
            color: #555;
            z-index: 1;
        }

        /* Floating bubbles */
        .bubble {
            position: absolute;
            bottom: -100px;
            background-color: rgba(255, 255, 255, 0.521);
            border-radius: 50%;
            animation: floatBubble 20s infinite ease-in;
        }

        @keyframes floatBubble {
            from {
                transform: translateY(0) scale(1);
                opacity: 0.8;
            }
            to {
                transform: translateY(-120vh) scale(1.5);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Floating bubbles -->
    <div class="bubble" style="left: 10%; width: 30px; height: 30px; animation-delay: 0s;"></div>
    <div class="bubble" style="left: 25%; width: 40px; height: 40px; animation-delay: 2s;"></div>
    <div class="bubble" style="left: 50%; width: 20px; height: 20px; animation-delay: 4s;"></div>
    <div class="bubble" style="left: 70%; width: 35px; height: 35px; animation-delay: 6s;"></div>
    <div class="bubble" style="left: 85%; width: 25px; height: 25px; animation-delay: 8s;"></div>

    <!-- Input Section -->
    <div class="container" id="inputSection">
        <h1>ඔබේ නම ඇතුළත් කරන්න:</h1>

        <input type="text" id="nameInput" placeholder="ඔබේ නම" oninput="filterLettersOnly(this)">
        <div class="error" id="errorText"></div>
        <button onclick="showMessage()">ඇතුළත් කරන්න</button>
    </div>

    <!-- Thank You Section -->
    <div class="container" id="thankYouSection" style="display: none;">
        <h1>💖ස්තූතියි!💖</h1>
        <p id="thankMessage"></p>
    </div>

    <!-- Footer -->
    <footer>© 2025 Heshan. All rights reserved.</footer>

    <!-- Script -->
    <script>
        function showMessage() {
            const name = document.getElementById("nameInput").value.trim();
            const error = document.getElementById("errorText");

            if (name.length >= 3) {
                document.getElementById("inputSection").style.display = "none";
                document.getElementById("thankYouSection").style.display = "block";
                document.getElementById("thankMessage").innerHTML = `
                    අවුරුද්දෙ මාස 12න් මම ඉපදුනු මාසය හා දවස මතක තියාගෙන<br>
                    මට සුභ පතපු <strong>${name}</strong> ඔබට ගොඩක් ස්තූතියි! 🙏<br><br>
                    ඔබේ මිත්‍රශීලිත්වය සහ නිහතමානී කම මම හැම විටම අගය කරනවා. 💛<br>Heshan✍️</br>
                `;
            } else {
                error.textContent = "කරුණාකර අක්ෂර 2කට වඩා දිග නමක් ඇතුළත් කරන්න 😊";
            }
        }

        function filterLettersOnly(input) {
            // Allow only Sinhala (Unicode range \u0D80-\u0DFF), English letters (a-zA-Z), and space
            input.value = input.value.replace(/[^a-zA-Z\u0D80-\u0DFF\s]/g, '');
        }
    </script>
</body>
</html>
