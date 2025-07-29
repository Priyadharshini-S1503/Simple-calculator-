<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .calculator {
      background: #222;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    input {
      width: 100%;
      height: 50px;
      font-size: 1.5em;
      text-align: right;
      margin-bottom: 10px;
      padding: 5px;
      border-radius: 5px;
      border: none;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 60px);
      grid-gap: 10px;
    }
    button {
      height: 60px;
      font-size: 1.2em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button.operator {
      background-color: #f39c12;
      color: white;
    }
    button.equal {
      background-color: #2ecc71;
      color: white;
      grid-column: span 2;
    }
    button.clear {
      background-color: #e74c3c;
      color: white;
      grid-column: span 2;
    }
    button.number {
      background-color: #34495e;
      color: white;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled />
    <div class="buttons">
      <button class="number" onclick="appendNumber('7')">7</button>
      <button class="number" onclick="appendNumber('8')">8</button>
      <button class="number" onclick="appendNumber('9')">9</button>
      <button class="operator" onclick="appendOperator('/')">÷</button>

      <button class="number" onclick="appendNumber('4')">4</button>
      <button class="number" onclick="appendNumber('5')">5</button>
      <button class="number" onclick="appendNumber('6')">6</button>
      <button class="operator" onclick="appendOperator('*')">×</button>

      <button class="number" onclick="appendNumber('1')">1</button>
      <button class="number" onclick="appendNumber('2')">2</button>
      <button class="number" onclick="appendNumber('3')">3</button>
      <button class="operator" onclick="appendOperator('-')">−</button>

      <button class="number" onclick="appendNumber('0')">0</button>
      <button class="number" onclick="appendDot()">.</button>
      <button class="equal" onclick="calculate()">=</button>
      <button class="operator" onclick="appendOperator('+')">+</button>

      <button class="clear" onclick="clearDisplay()">C</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");

    function appendNumber(number) {
      display.value += number;
    }

    function appendOperator(operator) {
      const lastChar = display.value.slice(-1);
      if (['+', '-', '*', '/'].includes(lastChar)) return;
      display.value += operator;
    }

    function appendDot() {
      const parts = display.value.split(/[\+\-\*\/]/);
      const lastPart = parts[parts.length - 1];
      if (!lastPart.includes(".")) {
        display.value += ".";
      }
    }

    function clearDisplay() {
      display.value = "";
    }

    function calculate() {
      try {
        display.value = eval(display.value);
      } catch {
        display.value = "Error";
      }
    }
  </script>
</body>
</html># Simple-calculator-
