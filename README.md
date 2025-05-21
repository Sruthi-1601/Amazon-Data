# Rock-Paper-Scissors
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background-color: #f0f0f0;
        }
        h1 {
            color: #333;
        }
        .choices {
            margin: 30px 0;
        }
        button {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
            border-radius: 8px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        #result {
            font-size: 24px;
            font-weight: bold;
            margin: 20px 0;
            min-height: 36px;
        }
        #scores {
            font-size: 18px;
            margin-top: 20px;
        }
        .choice {
            font-size: 60px;
            margin: 0 15px;
        }
    </style>
</head>
<body>
    <h1>Rock Paper Scissors</h1>
    
    <div class="choices">
        <button onclick="playGame('rock')">Rock</button>
        <button onclick="playGame('paper')">Paper</button>
        <button onclick="playGame('scissors')">Scissors</button>
    </div>
    
    <div id="result"></div>
    
    <div>
        <span class="choice" id="player-choice">🤔</span>
        <span>vs</span>
        <span class="choice" id="computer-choice">🤖</span>
    </div>
    
    <div id="scores">
        Player: <span id="player-score">0</span> | 
        Computer: <span id="computer-score">0</span>
    </div>

    <script>
        let playerScore = 0;
        let computerScore = 0;
        
        function playGame(playerChoice) {
            // Computer's random choice
            const choices = ['rock', 'paper', 'scissors'];
            const computerChoice = choices[Math.floor(Math.random() * 3)];
            
            // Update choice emojis
            document.getElementById('player-choice').textContent = getEmoji(playerChoice);
            document.getElementById('computer-choice').textContent = getEmoji(computerChoice);
            
            // Determine the winner
            let result;
            if (playerChoice === computerChoice) {
                result = "It's a tie!";
            } else if (
                (playerChoice === 'rock' && computerChoice === 'scissors') ||
                (playerChoice === 'paper' && computerChoice === 'rock') ||
                (playerChoice === 'scissors' && computerChoice === 'paper')
            ) {
                result = "You win!";
                playerScore++;
            } else {
                result = "Computer wins!";
                computerScore++;
            }
            
            // Update the display
            document.getElementById('result').textContent = result;
            document.getElementById('player-score').textContent = playerScore;
            document.getElementById('computer-score').textContent = computerScore;
        }
        
        function getEmoji(choice) {
            switch(choice) {
                case 'rock': return '✊';
                case 'paper': return '✋';
                case 'scissors': return '✌️';
                default: return '❓';
            }
        }
    </script>
</body>
</html>
