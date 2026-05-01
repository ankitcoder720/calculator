<!DOCTYPE html>
<html>
<head>
<title>Pro Calculator</title>

<link rel="manifest" href="manifest.json">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background: linear-gradient(135deg,#0f2027,#203a43,#2c5364);
    font-family: Arial;
}

.calculator {
    backdrop-filter: blur(15px);
    background: rgba(255,255,255,0.1);
    padding:20px;
    border-radius:20px;
    box-shadow:0 0 25px rgba(0,255,255,0.3);
}

input {
    width:100%;
    height:60px;
    font-size:26px;
    margin-bottom:15px;
    border:none;
    border-radius:10px;
    text-align:right;
    padding:10px;
    background: rgba(0,0,0,0.5);
    color:#0ff;
}

.buttons {
    display:grid;
    grid-template-columns:repeat(4,70px);
    gap:10px;
}

button {
    height:60px;
    font-size:18px;
    border:none;
    border-radius:15px;
    cursor:pointer;
    transition:0.2s;
    color:white;
}

button:hover {
    transform:scale(1.08);
}

.num { background:#2d2d44; }
.op { background:#ff9500; }
.eq { background:#00ffe0; color:black; grid-column:span 2; }
.clr { background:#ff3b30; }
.sci { background:#6c5ce7; }

</style>
</head>

<body>

<div class="calculator">
<input id="display" readonly>

<div class="buttons">
<button class="num" onclick="add('7')">7</button>
<button class="num" onclick="add('8')">8</button>
<button class="num" onclick="add('9')">9</button>
<button class="op" onclick="add('/')">÷</button>

<button class="num" onclick="add('4')">4</button>
<button class="num" onclick="add('5')">5</button>
<button class="num" onclick="add('6')">6</button>
<button class="op" onclick="add('*')">×</button>

<button class="num" onclick="add('1')">1</button>
<button class="num" onclick="add('2')">2</button>
<button class="num" onclick="add('3')">3</button>
<button class="op" onclick="add('-')">−</button>

<button class="num" onclick="add('0')">0</button>
<button class="num" onclick="add('.')">.</button>
<button class="clr" onclick="clearDisplay()">C</button>
<button class="op" onclick="add('+')">+</button>

<button class="sci" onclick="sqrt()">√</button>
<button class="sci" onclick="power()">x²</button>
<button class="sci" onclick="percent()">%</button>
<button class="eq" onclick="calculate()">=</button>
</div>
</div>

<script>

// 🔊 Sound
const clickSound = new Audio("https://www.soundjay.com/buttons/sounds/button-16.mp3");

function playSound() {
    clickSound.currentTime = 0;
    clickSound.play();
}

function add(val) {
    playSound();
    document.getElementById("display").value += val;
}

function clearDisplay() {
    playSound();
    document.getElementById("display").value = "";
}

function calculate() {
    playSound();
    try {
        let val = document.getElementById("display").value;
        document.getElementById("display").value = eval(val);
    } catch {
        document.getElementById("display").value = "Error";
    }
}

// 🧠 Scientific functions
function sqrt() {
    playSound();
    let val = document.getElementById("display").value;
    document.getElementById("display").value = Math.sqrt(val);
}

function power() {
    playSound();
    let val = document.getElementById("display").value;
    document.getElementById("display").value = val * val;
}

function percent() {
    playSound();
    let val = document.getElementById("display").value;
    document.getElementById("display").value = val / 100;
}

</script>

</body>
</html>
