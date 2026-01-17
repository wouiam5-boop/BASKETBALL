
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🏀 Basketball Game</title>
<style>
  body { font-family: Arial; text-align: center; background: #eaeaea; }
  h1 { color: #ff4500; margin-top: 20px; }
  .scoreboard { display: flex; justify-content: center; gap: 50px; margin: 20px; }
  .team { background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 0 5px #aaa; }
  button { padding: 10px 20px; margin: 5px; font-size: 16px; border-radius: 5px; cursor: pointer; }
  #winner { font-size: 24px; color: green; margin-top: 20px; }
</style>
</head>
<body>

<h1>🏀 Basketball Game Tracker</h1>

<div>
  <label>Players per team:</label>
  <select id="playersPerTeam">
    <option value="1">1v1</option>
    <option value="2">2v2</option>
    <option value="3">3v3</option>
    <option value="4">4v4</option>
    <option value="5">5v5</option>
  </select>
</div>

<div class="scoreboard">
  <div class="team">
    <h2>Team A</h2>
    <p id="scoreA">0</p>
    <button onclick="addPoint('A', 1)">Inside Shot +1</button>
    <button onclick="addPoint('A', 2)">Outside Shot +2</button>
  </div>

  <div class="team">
    <h2>Team B</h2>
    <p id="scoreB">0</p>
    <button onclick="addPoint('B', 1)">Inside Shot +1</button>
    <button onclick="addPoint('B', 2)">Outside Shot +2</button>
  </div>
</div>

<button onclick="resetGame()">Reset Game</button>

<p id="winner"></p>

<script>
let scoreA = 0;
let scoreB = 0;

function addPoint(team, points) {
  if(team === 'A') scoreA += points;
  if(team === 'B') scoreB += points;
  document.getElementById('scoreA').innerText = scoreA;
  document.getElementById('scoreB').innerText = scoreB;
  checkWinner();
}

function checkWinner() {
  let players = parseInt(document.getElementById('playersPerTeam').value);
  let target = players === 1 ? 11 : 21;

  if(scoreA >= target && scoreA - scoreB >= 2){
    document.getElementById('winner').innerText = "Team A Wins! 🏆";
  } else if(scoreB >= target && scoreB - scoreA >= 2){
    document.getElementById('winner').innerText = "Team B Wins! 🏆";
  } else {
    document.getElementById('winner').innerText = "";
  }
}

function resetGame() {
  scoreA = 0;
  scoreB = 0;
  document.getElementById('scoreA').innerText = scoreA;
  document.getElementById('scoreB').innerText = scoreB;
  document.getElementById('winner').innerText = "";
}
</script>

</body>
</html>
