<!DOCTYPE HTML>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Aplicação Financeira</title>
    
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f4f6;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #0a74da;
            color: white;
            text-align: center;
            padding: 15px 0;
        }
        .container {
            width: 90%;
            max-width: 600px;
            margin: 30px auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0px 2px 8px rgba(0,0,0,0.1);
        }
        input, select, button {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            background-color: #0a74da;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            background-color: #0859a1;
        }
        ul {
            list-style: none;
            padding: 0;
        }
        li {
            padding: 6px 0;
            border-bottom: 1px solid #eee;
        }
        .saldo {
            font-size: 1.4em;
            font-weight: bold;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Controle Financeiro</h1>
    </header>

    <div class="container">
        <h3>Adicionar Transação</h3>
        
        <input type="text" id="descricao" placeholder="Descrição">
        <input type="number" id="valor" placeholder="Valor (ex: 100 ou -50)">
        
        <button onclick="adicionarTransacao()">Adicionar</button>
        
        <h3>Transações</h3>
        <ul id="listaTransacoes"></ul>
        
        <div class="saldo" id="saldoTotal">Saldo: R$ 0.00</div>
    </div>

    <script>
        let transacoes = [];

        function adicionarTransacao() {
            const descricao = document.getElementById('descricao').value;
            const valor = Number(document.getElementById('valor').value);

            if (descricao && valor) {
                transacoes.push({ descricao, valor });
                
                // Limpa os campos de input
                document.getElementById('descricao').value = "";
                document.getElementById('valor').value = "";
                
                atualizarTela();
            }
        }

        function atualizarTela() {
            const lista = document.getElementById('listaTransacoes');
            lista.innerHTML = "";
            let saldo = 0;

            transacoes.forEach(t => {
                const item = document.createElement('li');
                item.textContent = `${t.descricao}: R$ ${t.valor.toFixed(2)}`;
                lista.appendChild(item);
                
                saldo += t.valor;
            });

            document.getElementById('saldoTotal').textContent = `Saldo: R$ ${saldo.toFixed(2)}`;
        }
    </script>
</body>
</html>
