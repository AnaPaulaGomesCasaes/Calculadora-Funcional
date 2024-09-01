<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Verde e Preto</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }

        .calculadora {
            width: 300px;
            margin: 50px auto;
            background-color: #000;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }

        #display {
            width: 100%;
            height: 40px;
            font-size: 24px;
            text-align: right;
            padding: 10px;
            border: none;
            border-radius: 10px;
            background-color: #0f0;
            color: #000;
        }

        .botoes {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 10px;
            margin-top: 20px;
        }

        .botao {
            background-color: #0f0;
            color: #000;
            border: none;
            padding: 10px;
            border-radius: 10px;
            cursor: pointer;
        }

        .botao:hover {
            background-color: #0c0;
        }
    </style>
</head>
<body>
    <div class="calculadora">
        <input type="text" id="display" disabled>
        <div class="botoes">
            <button class="botao" onclick="limpar()">C</button>
            <button class="botao" onclick="apagar()">DEL</button>
            <button class="botao" onclick="calcular('%')">%</button>
            <button class="botao" onclick="calcular('/')">/</button>
            <button class="botao" onclick="calcular('7')">7</button>
            <button class="botao" onclick="calcular('8')">8</button>
            <button class="botao" onclick="calcular('9')">9</button>
            <button class="botao" onclick="calcular('*')">*</button>
            <button class="botao" onclick="calcular('4')">4</button>
            <button class="botao" onclick="calcular('5')">5</button>
            <button class="botao" onclick="calcular('6')">6</button>
            <button class="botao" onclick="calcular('-')">-</button>
            <button class="botao" onclick="calcular('1')">1</button>
            <button class="botao" onclick="calcular('2')">2</button>
            <button class="botao" onclick="calcular('3')">3</button>
            <button class="botao" onclick="calcular('+')">+</button>
            <button class="botao" onclick="calcular('0')">0</button>
            <button class="botao" onclick="calcular('.')">.</button>
            <button class="botao" onclick="igual()">=</button>
            <button class="botao" onclick="raizQuadrada()">√</button>
        </div>
    </div>

    <script>
        let display = document.getElementById('display');

        function calcular(valor) {
            if (display.value === '0' && valor !== '.') {
                display.value = valor;
            } else {
                display.value += valor;
            }
        }

        function limpar() {
            display.value = '0';
        }

        function apagar() {
            if (display.value.length > 1) {
                display.value = display.value.slice(0, -1);
            } else {
                display.value = '0';
            }
        }

        function igual() {
            try {
                let resultado = eval(display.value);
                display.value = resultado.toString();
            } catch (e) {
                display.value = 'Erro';
            }
        }

        function raizQuadrada() {
            try {
                let resultado = Math.sqrt(parseFloat(display.value));
                display.value = resultado.toString();
            } catch (e) {
                display.value = 'Erro';
            }
        }

        limpar();
    </script>
</body>
</html>
