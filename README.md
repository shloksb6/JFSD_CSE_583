<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Guessing Game</title>
</head>
<body>

    <div class="game-container">
        <h1>Number Guessing Game</h1>
        <p>Guess a number between 1 and 100</p>

        <div id="message"></div>

        <input type="number" id="guess" placeholder="Enter your guess" />
        <button id="submit-btn">Submit</button>

        <p>Attempts: <span id="attempts">0</span></p>

        <button id="restart-btn" style="display:none;">Restart</button>
    </div>

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .game-container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 300px;
        }

        h1 {
            margin-bottom: 20px;
        }

        input {
            padding: 10px;
            font-size: 16px;
            width: 80%;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        #message {
            margin: 10px 0;
            font-weight: bold;
        }

        #restart-btn {
            background-color: #f44336;
        }

        #restart-btn:hover {
            background-color: #e53935;
        }
    </style>

    <script>
        let randomNumber = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;

        document.getElementById('submit-btn').addEventListener('click', function() {
            let guess = parseInt(document.getElementById('guess').value);
            attempts++;

            if (isNaN(guess) || guess < 1 || guess > 100) {
                document.getElementById('message').textContent = "Please enter a valid number between 1 and 100.";
                return;
            }

            if (guess === randomNumber) {
                document.getElementById('message').textContent = Congratulations! You guessed it right in ${attempts} attempts.;
                document.getElementById('restart-btn').style.display = 'inline-block';
                document.getElementById('submit-btn').disabled = true;
            } else if (guess < randomNumber) {
                document.getElementById('message').textContent = "Too low! Try again.";
            } else {
                document.getElementById('message').textContent = "Too high! Try again.";
            }

            document.getElementById('attempts').textContent = attempts;
        });

        document.getElementById('restart-btn').addEventListener('click', function() {
            randomNumber = Math.floor(Math.random() * 100) + 1;
            attempts = 0;
            document.getElementById('message').textContent = '';
            document.getElementById('attempts').textContent = attempts;
            document.getElementById('guess').value = '';
            document.getElementById('submit-btn').disabled = false;
            document.getElementById('restart-btn').style.display = 'none';
        });
    </script>

</body>
</html>
