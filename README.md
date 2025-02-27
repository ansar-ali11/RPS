# **Rock-Paper-Scissors Game**

## **Overview**
The **Rock-Paper-Scissors** game is a simple and fun web-based application where a player competes against the computer in the classic game. The player chooses one of three options (rock, paper, or scissors) and the computer randomly selects its option. The game then determines the winner based on the game rules:
- Rock beats Scissors
- Scissors beats Paper
- Paper beats Rock

The application displays the player's and computer's choices, the outcome of each round, and keeps track of the scores.

### **Features**:
- **Play against the Computer**: Choose between Rock, Paper, and Scissors.
- **Score Display**: Shows the current score of both the player and the computer.
- **Dynamic Result**: Displays if the player won, lost, or tied.
- **Responsive UI**: The game is designed to work well on both desktop and mobile devices.

### **Tech Stack**:
- **Frontend**: HTML, CSS, JavaScript
- **Design**: Custom CSS with a background image for styling and making the game visually appealing.

---

## **Code Provided**

### 1. **HTML: `index.html`**
This HTML file contains the structure of the game, including buttons for user choices and display areas for the results and scores.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome</title>
    <link rel="stylesheet" href="index.css">
</head>
<body>
    <h1>Rock-Paper-Scissors</h1>
    <div class="choices">
        <button onclick="playgame('rock')">✊</button>
        <button onclick="playgame('paper')">✋</button>
        <button onclick="playgame('scissors')">✌️</button>
    </div>
    <div id="playerDisplay">PLAYER:</div>
    <div id="computerDisplay">COMPUTER:</div>
    <div id="resultDisplay"></div>
    <div class="scoreDisplay">Player Score: <span id="playerScoreDisplay">0</span></div>
    <div class="scoreDisplay">Computer Score: <span id="computerScoreDisplay">0</span></div>
    <script src="index.js"></script>
</body>
</html>
```

### 2. **CSS: `index.css`**
This CSS file contains the styles for the game layout, button design, font sizes, and background image.

```css
body {
    margin: 0;
    font-family: Arial, sans-serif;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-image: url("https://images.pexels.com/photos/235985/pexels-photo-235985.jpeg?auto=compress&cs=tinysrgb&w=600");
    background-size: cover;
}

h1 {
    font-size: 2.5rem;
    margin: 20px 0;
}

.choices {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.choices button {
    font-size: 7.5rem;
    border-radius: 40px;
    background-color: lightblue;
    cursor: pointer;
    transition: 0.5s ease;
    margin: 10px;
}

.choices button:hover {
    background-color: rgb(112, 176, 109);
}

#playerDisplay, #computerDisplay {
    font-size: 2.5rem;
}

#resultDisplay {
    font-size: 5rem;
    margin: 30px 0;
}

.green, #playerScoreDisplay {
    color: hsl(130, 84%, 54%);
}

.red, #computerScoreDisplay {
    color: rgb(224, 26, 26);
}

.scoreDisplay {
    font-size: 2rem;
}

@media (max-width: 768px) {
    h1 {
        font-size: 2rem;
    }

    .choices button {
        font-size: 5rem;
    }

    #playerDisplay, #computerDisplay {
        font-size: 2rem;
    }

    #resultDisplay {
        font-size: 4rem;
    }

    .scoreDisplay {
        font-size: 1.5rem;
    }
}
```

### 3. **JavaScript: `index.js`**
This JavaScript file contains the logic for the game. It handles user input, randomly selects the computer's choice, and updates the game state (scores and result).

```javascript
const choices = ['rock', 'paper', 'scissors'];

const playerDisplay = document.getElementById("playerDisplay");
const computerDisplay = document.getElementById("computerDisplay");
const resultDisplay = document.getElementById("resultDisplay");
const playerScoreDisplay = document.getElementById("playerScoreDisplay");
const computerScoreDisplay = document.getElementById("computerScoreDisplay");

let playerScore = 0;
let computerScore = 0;

function playgame(playerChoice) {
    const computerChoice = choices[Math.floor(Math.random() * 3)];
    let result = "";

    if (playerChoice === computerChoice) {
        result = "It's a Tie";
    }
    else {
        switch (playerChoice) {
            case "rock":
                result = (computerChoice === 'scissors') ? "YOU WIN!" : "YOU LOSE!";
                break;
            case "paper":
                result = (computerChoice === 'rock') ? "YOU WIN!" : "YOU LOSE!";
                break;
            case "scissors":
                result = (computerChoice === 'paper') ? "YOU WIN!" : "YOU LOSE!";
                break;
        }
    }

    playerDisplay.textContent = ` PLAYER : ${playerChoice}`;
    computerDisplay.textContent = ` COMPUTER : ${computerChoice}`;
    resultDisplay.textContent = result;

    resultDisplay.classList.remove("green","red");

    switch(result) {
        case "YOU WIN!":
            resultDisplay.classList.add("green");
            playerScore++;
            playerScoreDisplay.textContent = playerScore;
            break;
        case "YOU LOSE!":
            resultDisplay.classList.add("red");
            computerScore++;
            computerScoreDisplay.textContent = computerScore;
            break;
    }

}
```

---

## **How to Run the Game Locally**

To run this **Rock-Paper-Scissors** game on your local machine:

1. **Clone the Repository**: Clone the GitHub repository to your local machine using:
   ```bash
   git clone https://github.com/your-username/rock-paper-scissors.git
   ```

2. **Open the Project**: Open the folder where you cloned the project.

3. **Open `index.html` in a Browser**: 
   - Navigate to the folder containing `index.html`.
   - Double-click on `index.html` to open it in your browser.

4. **Play the Game**: Click on the buttons for Rock, Paper, or Scissors to start playing!

---
