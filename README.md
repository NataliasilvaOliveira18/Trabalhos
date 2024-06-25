# Trabalhos
Outros trabalhos feitos (conversor de moedas)

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Conversor de Moedas</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Conversor de Moedas</h1>
    <div class="form-group">
      <label for="valor">Valor a ser convertido:</label>
      <input type="number" id="valor" placeholder="Digite o valor...">
    </div>
    <div class="form-group">
      <label for="moedaOrigem">Moeda de origem:</label>
      <select id="moedaOrigem">
        <option value="USD">Dólar Americano (USD)</option>
        <option value="EUR">Euro (EUR)</option>
        <option value="JPY">Iene Japonês (JPY)</option>
        <option value="GBP">Libra Esterlina (GBP)</option>
        <option value="BRL">Real Brasileiro (BRL)</option>
      </select>
    </div>
    <div class="form-group">
      <label for="moedaDestino">Moeda de destino:</label>
      <select id="moedaDestino">
        <option value="USD">Dólar Americano (USD)</option>
        <option value="EUR">Euro (EUR)</option>
        <option value="JPY">Iene Japonês (JPY)</option>
        <option value="GBP">Libra Esterlina (GBP)</option>
        <option value="BRL">Real Brasileiro (BRL)</option>
      </select>
    </div>
    <button id="btnConverter">Converter</button>
    <div id="resultado"></div>
  </div>
  <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
  }
  
  .container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input[type="number"],
  select {
    width: 100%;
    padding: 8px;
    border-radius: 3px;
    border: 1px solid #ccc;
  }
  
  button {
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  #resultado {
    margin-top: 20px;
    font-size: 18px;
  }
  document.addEventListener('DOMContentLoaded', function () {
    const taxaDeCambio = {
      USD: 5.30,
      EUR: 6.20,
      JPY: 0.048,
      GBP: 7.30,
      BRL: 1.00  // Taxa base 1:1 para o Real Brasileiro
    };
  
    const btnConverter = document.getElementById('btnConverter');
    const valorInput = document.getElementById('valor');
    const moedaOrigemSelect = document.getElementById('moedaOrigem');
    const moedaDestinoSelect = document.getElementById('moedaDestino');
    const resultadoDiv = document.getElementById('resultado');
  
    btnConverter.addEventListener('click', function () {
      const valor = parseFloat(valorInput.value);
      const moedaOrigem = moedaOrigemSelect.value;
      const moedaDestino = moedaDestinoSelect.value;
  
      if (isNaN(valor) || valor <= 0) {
        resultadoDiv.textContent = 'Por favor, insira um valor válido.';
        return;
      }
  
      if (moedaOrigem === moedaDestino) {
        resultadoDiv.textContent = 'As moedas de origem e destino devem ser diferentes.';
        return;
      }
  
      const valorConvertido = valor * (taxaDeCambio[moedaDestino] / taxaDeCambio[moedaOrigem]);
      resultadoDiv.textContent = `Valor convertido: ${valorConvertido.toFixed(2)} ${moedaDestino}`;
    });
  });
