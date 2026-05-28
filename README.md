<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Timer Sederhana</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #4facfe, #00f2fe);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            width: 300px;
        }

        h1 {
            color: #333;
        }

        #timer {
            font-size: 50px;
            margin: 20px 0;
            color: #007BFF;
            font-weight: bold;
        }

        input {
            width: 80%;
            padding: 10px;
            font-size: 16px;
            margin-bottom: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            text-align: center;
        }

        button {
            padding: 10px 15px;
            margin: 5px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
        }

        .start {
            background: green;
            color: white;
        }

        .pause {
            background: orange;
            color: white;
        }

        .reset {
            background: red;
            color: white;
        }

        button:hover {
            opacity: 0.8;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>⏳ Timer</h1>

        <input type="number" id="minutes" placeholder="Masukkan menit">

        <div id="timer">00:00</div>

        <button class="start" onclick="startTimer()">Mulai</button>
        <button class="pause" onclick="pauseTimer()">Pause</button>
        <button class="reset" onclick="resetTimer()">Reset</button>
    </div>

    <script>
        let countdown;
        let timeLeft = 0;

        function startTimer() {
            if (timeLeft === 0) {
                const minutes = document.getElementById("minutes").value;
                timeLeft = minutes * 60;
            }

            countdown = setInterval(() => {
                let minutes = Math.floor(timeLeft / 60);
                let seconds = timeLeft % 60;

                document.getElementById("timer").innerText =
                    String(minutes).padStart(2, '0') + ":" +
                    String(seconds).padStart(2, '0');

                if (timeLeft <= 0) {
                    clearInterval(countdown);
                    alert("⏰ Waktu Habis!");
                }

                timeLeft--;
            }, 1000);
        }

        function pauseTimer() {
            clearInterval(countdown);
        }

        function resetTimer() {
            clearInterval(countdown);
            timeLeft = 0;
            document.getElementById("timer").innerText = "00:00";
            document.getElementById("minutes").value = "";
        }
    </script>

</body>
</html># Timer-
