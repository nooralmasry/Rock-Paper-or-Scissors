# Rock-Paper-or-Scissors
HTML 

<h1>Rock, Paper, or Scissors?</h1>
<strong>paper</strong>, and <strong>paper</strong> beats <strong>rock</strong>.</p>
<div class="scoreboard">
  <h2>Scoreboard</h2>
  <table>
    <tbody>
      <tr>
        <td id="humanScore">0</td>
        <td id="computerScore">0</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <th>You</th>
        <th>Bot</th>
      </tr>
    </tfoot>
  </table>
</div>
<h2>Choose Wisely</h2>
<button id="rock">Rock</button>
<button id="paper">Paper</button>
<button id="scissors">Scissors</button>
<div id="status"></div>

Css

body {
  font-family: monospace;
  font-size: 20px;
  text-align: center;
  background: black;
  color: lime;
  margin: 3em;
}

strong {
  text-decoration: underline;
}

button {
  background: lime;
  color: black;
  border: none;
  padding: 10px 15px;
  font-size: 1.2em;
  font-family: monospace;
  font-weight: bold;
}
button:active {
  background: green;
}

.scoreboard {
  width: 14em;
  margin: auto;
  border: 1px solid lime;
}
.scoreboard h2 {
  border-bottom: 1px solid lime;
  margin: 0;
  padding: 10px;
}
.scoreboard table {
  margin: 10px auto;
  width: 100%;
  border-collapse: collapse;
}
.scoreboard th, .scoreboard td {
  text-align: center;
}
.scoreboard td {
  font-size: 3em;
  padding: 0 20px;
}

#status {
  margin-top: 20px;
}

Js

var humanScore = 0;
var computerScore = 0;

document.getElementById('rock').onclick = playRock;
document.getElementById('paper').onclick = playPaper;
document.getElementById('scissors').onclick = playScissors;

function playRock() {
  play("rock");
}
function playPaper() {
  play("paper");
}
function playScissors() {
  play("scissors");
}

function play(humanPlay) {
  
  computerPlay = getComputerPlay();
  
  document.getElementById('status').innerHTML = "<p>You played <strong>" + humanPlay + "</strong>. The bot played <strong>" + computerPlay + "</strong>.</p>";
  
  if(humanPlay == 'rock') {
    if(computerPlay == 'rock') {
      document.getElementById('status').innerHTML += "<p>You tied. :|</p>";
    } else if (computerPlay == 'paper') {
      document.getElementById('status').innerHTML += "<p>You lose. :(</p>";
      computerScore++;
    } else if (computerPlay == 'scissors') {
      document.getElementById('status').innerHTML += "<p>You win! :)</p>";
      humanScore++;
    }
  } else if (humanPlay == 'paper') {
    if(computerPlay == 'rock') {
      document.getElementById('status').innerHTML += "<p>You win! :)</p>";
      humanScore++;
    } else if (computerPlay == 'paper') {
      document.getElementById('status').innerHTML += "<p>You tied. :|</p>";
    } else if (computerPlay == 'scissors') {
      document.getElementById('status').innerHTML += "<p>You lose. :(</p>";
      computerScore++;
    }  
  } else if (humanPlay == 'scissors') {
    if(computerPlay == 'rock') {
      document.getElementById('status').innerHTML += "<p>You lose. :(</p>";
      computerScore++;
    } else if (computerPlay == 'paper') {
      document.getElementById('status').innerHTML += "<p>You win! :)</p>";
      humanScore++;
    } else if (computerPlay == 'scissors') {
      document.getElementById('status').innerHTML += "<p>You tied. :|</p>";
    }  
  }
  
  document.getElementById('humanScore').innerHTML = humanScore;
  document.getElementById('computerScore').innerHTML = computerScore;
  
}

function getComputerPlay() {
  var plays = ['rock', 'paper', 'scissors'];
  var play = plays[Math.floor(Math.random() * plays.length)];
  return play;
}
