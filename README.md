<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>SUKUN</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * { box-sizing: border-box; }
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #fdeff9, #e0f2ff);
            text-align: center;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container { padding: 30px 20px; animation: fade .6s ease; width: 100%; }
        @keyframes fade {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .card {
            background: #fff;
            padding: 25px;
            border-radius: 22px;
            max-width: 420px;
            margin: auto;
            box-shadow: 0 12px 30px rgba(0,0,0,.12);
        }
        h1 { font-size: 32px; margin-bottom: 10px; color: #ff6f91; }
        input {
            padding: 12px;
            font-size: 16px;
            border-radius: 10px;
            border: 1px solid #ddd;
            width: 80%;
            margin-bottom: 10px;
            outline: none;
        }
        button {
            padding: 10px 25px;
            margin-top: 10px;
            border: none;
            border-radius: 20px;
            background: #ff6f91;
            color: #fff;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
        }
        button:hover { background: #ff3f6c; }
        .emoji {
            font-size: 45px;
            margin: 10px;
            cursor: pointer;
            display: inline-block;
            transition: transform .2s;
        }
        .emoji:hover { transform: scale(1.2); }
        .hidden { display: none; }
        .back { margin-top: 20px; background: #90caf9; }
        .back:hover { background: #64b5f6; }
        #error { color: #ff3f6c; font-size: 14px; margin-top: 10px; }
    </style>
</head>
<body>

    <div class="container" id="login">
        <div class="card">
            <h1>SUKUN</h1>
            <p>Kuch cheezein sirf mehsoos karne ke liye hoti hain…</p>
            <input type="password" id="pass" placeholder="Enter Passcode">
            <br>
            <button onclick="checkPass()">Enter</button>
            <p id="error"></p>
        </div>
    </div>

    <div class="container hidden" id="main">
        <div class="card">
            <h1>Choose a mood 🙂</h1>
            <div>
                <span class="emoji" onclick="openCard('smile')">😊</span>
                <span class="emoji" onclick="openCard('sad')">😔</span>
                <span class="emoji" onclick="openCard('kiss')">😘</span>
                <span class="emoji" onclick="openCard('funny')">😂</span>
                <span class="emoji" onclick="openCard('surprise')">❓</span>
            </div>
        </div>
    </div>

    <div class="container card hidden" id="smile">
        <p id="smileText">Tumhari ek muskaan kaafi hoti hai din better karne ke liye.</p>
        <button onclick="toggleSmile()">Tap again</button>
        <br>
        <button class="back" onclick="goBack()">Back</button>
    </div>

    <div class="container card hidden" id="sad">
        <p>Jo bhi hai, tum akeli nahi ho.</p>
        <p>Thoda sukoon yahin rehne do…</p>
        <button class="back" onclick="goBack()">Back</button>
    </div>

    <div class="container card hidden" id="kiss">
        <p>Kuch ehsaas bina lafzon ke bhi poore hote hain.</p>
        <button class="back" onclick="goBack()">Back</button>
    </div>

    <div class="container card hidden" id="funny">
        <p>Tum serious hoti ho tab bhi funny lagti ho 😄</p>
        <button class="back" onclick="goBack()">Back</button>
    </div>

    <div class="container card hidden" id="surprise">
        <p>Yeh website kisi sawal ke liye nahi…</p>
        <p>Bas tumhari muskaan ke liye hai 💙</p>
        <button class="back" onclick="goBack()">Back</button>
    </div>

    <div class="container card hidden" id="owner">
        <h3>Owner Mode</h3>
        <p>Yeh tumhara private space hai.</p>
        <p>Yahin se future me text change kar sakte ho.</p>
        <button class="back" onclick="location.reload()">Logout</button>
    </div>

    <script>
        function checkPass() {
            let p = document.getElementById("pass").value;
            let login = document.getElementById("login");
            let main = document.getElementById("main");
            let owner = document.getElementById("owner");
            let error = document.getElementById("error");

            if (p === "14.25") {
                login.classList.add("hidden");
                main.classList.remove("hidden");
            } else if (p === "2016") {
                login.classList.add("hidden");
                owner.classList.remove("hidden");
            } else {
                error.innerText = "Thoda aur yaad karo 🙂";
            }
        }

        function openCard(id) {
            document.getElementById("main").classList.add("hidden");
            document.getElementById(id).classList.remove("hidden");
        }

        function goBack() {
            // Sabhi card types ko hide karein
            const cards = ["smile", "sad", "kiss", "funny", "surprise", "owner"];
            cards.forEach(c => document.getElementById(c).classList.add("hidden"));
            document.getElementById("main").classList.remove("hidden");
        }

        let flip = false;
        function toggleSmile() {
            flip = !flip;
            document.getElementById("smileText").innerText = flip ? 
                "Ye wali smile thodi special lag rahi hai 😊" : 
                "Tumhari ek muskaan kaafi hoti hai din better karne ke liye.";
        }
    </script>

</body>
</html>
