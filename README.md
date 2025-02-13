<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            text-align: center;
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background: linear-gradient(180deg, #b19cd9, #d8b9ff);
            overflow: hidden;
            margin: 0;
            padding: 0;
            position: relative;
        }

        h1 {
            margin-top: 50px;
            font-size: 2.5em;
            color: #6a0dad;
            text-shadow: 2px 2px 5px white;
        }

        .cat-container {
            margin-top: 20px;
            min-height: 200px; /* Space for text replacement */
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .cat-img, .response-text {
            width: 200px;
            height: auto;
            transition: 0.3s;
        }

        .response-text {
            font-size: 2em;
            color: #6a0dad;
            font-weight: bold;
            text-shadow: 2px 2px 5px white;
            display: none;
        }

        .container {
            margin-top: 20px;
        }

        button {
            font-size: 18px;
            padding: 12px 24px;
            margin: 10px;
            border: none;
            cursor: pointer;
            border-radius: 10px;
            transition: 0.3s;
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
        }

        #yes {
            background-color: #6a0dad;
            color: white;
        }

        #no {
            background-color: #cccccc;
            color: black;
        }

        /* Falling Sad Emojis Effect */
        @keyframes rainEmojis {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(100vh); opacity: 0; }
        }

        .emoji {
            position: fixed;
            top: -50px;
            font-size: 30px;
            animation: rainEmojis 2.5s linear infinite;
        }
    </style>
</head>
<body>
    <h1 id="caption">Will you be my Valentine? 💜</h1>
    
    <div class="cat-container">
        <img id="catImage" class="cat-img" src="C:\Users\Asus\OneDrive\Desktop\valentine\happy-cat.jpg" alt="Cute Cat">
        <p id="responseText" class="response-text"></p>
    </div>

    <div class="container">
        <button id="yes" onclick="sayYes()">Yes</button>
        <button id="no" onclick="sayNo()">No</button>
    </div>

    <script>
        let noClickCount = 0;
        const noMessages = [
            "WHYYY PLEASEEE NOOO PLSSPLSS 😭", 
            "You're breaking my heart! 💔", 
            "I can't believe this... 😢", 
            "Last chance! 💜"
        ];
        const sadEmojis = ["😢", "🥺", "💔", "😞", "😭"];

        function sayYes() {
            document.getElementById("caption").innerHTML = "Yayyy! 💜 You made my heart so happy! 🥰";
            document.getElementById("yes").style.fontSize = "30px";
            document.getElementById("no").style.display = "none";

            // Hide image and show response text
            document.getElementById("catImage").style.display = "none";
            document.getElementById("responseText").innerHTML = "Meet me tomorrow ❤️";
            document.getElementById("responseText").style.display = "block";
        }

        function sayNo() {
            noClickCount++;
            let noButton = document.getElementById("no");
            let responseText = document.getElementById("responseText");

            // Hide the image and show a sad message instead
            document.getElementById("catImage").style.display = "none";
            responseText.innerHTML = noMessages[Math.min(noClickCount, noMessages.length - 1)];
            responseText.style.display = "block";

            // Change "No" button text
            if (noClickCount >= noMessages.length) {
                noButton.innerHTML = "No more excuses! 💜";
            }

            // Make sad emojis fall
            createSadEmojis(5);
        }

        function createSadEmojis(count) {
            for (let i = 0; i < count; i++) {
                let emoji = document.createElement("div");
                emoji.innerHTML = sadEmojis[Math.floor(Math.random() * sadEmojis.length)];
                emoji.classList.add("emoji");
                document.body.appendChild(emoji);

                // Random position
                emoji.style.left = Math.random() * window.innerWidth + "px";
                emoji.style.animationDuration = (Math.random() * 2 + 2) + "s";

                // Remove emojis after animation
                setTimeout(() => { emoji.remove(); }, 3000);
            }
        }
    </script>
</body>
</html>
