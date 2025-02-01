<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Dias</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        input, button {
            margin: 10px;
            padding: 10px;
        }
        #resultado {
            margin-top: 20px;
            font-weight: bold;
        }
        .erro {
            color: red;
        }
        .sinalizacao {
            color: red;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h2>Calculadora de Dias</h2>
    <label for="dataInicio">Data de Início:</label>
    <input type="date" id="dataInicio">
    <br>
    <label for="duracao">Duração (dias):</label>
    <input type="number" id="duracao" min="1">
    <br>
    <button onclick="calcularDataFinal()">Calcular Data Final</button>
    <p id="resultado"></p>
    
    <script>
        function calcularDataFinal() {
            const dataInicio = document.getElementById('dataInicio').value;
            const duracao = parseInt(document.getElementById('duracao').value);
            const resultado = document.getElementById('resultado');
            
            if (!dataInicio || isNaN(duracao) || duracao < 1) {
                resultado.innerHTML = '<span class="erro">Por favor, insira uma data válida e uma duração positiva.</span>';
                return;
            }
            
            const data = new Date(dataInicio);
            data.setDate(data.getDate() + duracao);
            
            const dataSinalizacao = new Date(data);
            dataSinalizacao.setDate(data.getDate() - 45);
            
            resultado.innerHTML = `A data final do estoque será: <strong>${data.toLocaleDateString('pt-BR')}</strong><br><br>
                                  <span class="sinalizacao">O paciente deve ser sinalizado no dia: <strong>${dataSinalizacao.toLocaleDateString('pt-BR')}</strong></span>`;
        }
    </script>
</body>
</html>
