
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
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

        .calculator {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            width: 300px;
        }

        .display {
            width: 100%;
            height: 50px;
            background: #eee;
            border: none;
            border-radius: 5px;
            margin-bottom: 20px;
            font-size: 1.5rem;
            text-align: right;
            padding: 10px;
            box-sizing: border-box;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .button {
            padding: 15px;
            font-size: 1.2rem;
            text-align: center;
            background: #4caf50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .button:hover {
            background: #45a049;
        }

        .button.operator {
            background: #2196f3;
        }

        .button.operator:hover {
            background: #1e88e5;
        }

        .button.clear {
            background: #f44336;
        }

        .button.clear:hover {
            background: #e53935;
        }

    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" class="display" id="display" disabled>
        <div class="buttons">
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="appendOperator('/')">/</button>

            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="appendOperator('*')">*</button>

            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button operator" onclick="appendOperator('-')">-</button>

            <button class="button" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button clear" onclick="clearDisplay()">C</button>
            <button class="button operator" onclick="appendOperator('+')">+</button>

            <button class="button operator" style="grid-column: span 4;" onclick="calculateResult()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');

        function appendNumber(number) {
            display.value += number;
        }

        function appendOperator(operator) {
            if (display.value !== '' && !isNaN(display.value.slice(-1))) {
                display.value += operator;
            }
        }

        function clearDisplay() {
            display.value = '';
        }

        function calculateResult() {
            try {
                display.value = eval(display.value);
            } catch {
                display.value = 'Error';
            }
        }
    </script>
</body>
</html>
