<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pilhas - Estrutura de Dados</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
            color: #333;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .content {
            padding: 40px;
        }

        section {
            margin-bottom: 40px;
        }

        h2 {
            color: #2c3e50;
            border-bottom: 3px solid #667eea;
            padding-bottom: 10px;
            margin-bottom: 20px;
            font-size: 1.8em;
        }

        .definition {
            background: #f8f9fa;
            border-left: 5px solid #667eea;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
            font-size: 1.1em;
        }

        .demo-container {
            background: #f8f9fa;
            padding: 30px;
            border-radius: 10px;
            margin: 20px 0;
        }

        .stack-visual {
            display: flex;
            flex-direction: column-reverse;
            align-items: center;
            margin: 20px 0;
            min-height: 300px;
            justify-content: flex-start;
        }

        .stack-item {
            width: 250px;
            padding: 15px;
            margin: 5px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
            border-radius: 5px;
            font-weight: bold;
            font-size: 1.1em;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .controls {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        button {
            padding: 15px 30px;
            font-size: 16px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
        }

        button:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        input {
            padding: 15px;
            font-size: 16px;
            border: 2px solid #667eea;
            border-radius: 5px;
            width: 250px;
        }

        .info-message {
            background: #e3f2fd;
            border-left: 4px solid #2196f3;
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            text-align: center;
            font-weight: bold;
        }

        .operations {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }

        .operation-card {
            background: white;
            border: 2px solid #667eea;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .operation-card h3 {
            color: #667eea;
            margin-bottom: 10px;
        }

        ul {
            margin-left: 20px;
            margin-top: 10px;
        }

        li {
            margin: 8px 0;
        }

        footer {
            background: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>📚 Pilhas (Stacks)</h1>
            <p>Estrutura de Dados LIFO</p>
        </header>

        <div class="content">
            <section>
                <h2>O que é uma Pilha?</h2>
                <div class="definition">
                    Uma <strong>pilha</strong> é uma estrutura de dados que funciona como uma pilha de pratos: você sempre coloca e retira pratos do topo. Ela segue o princípio <strong>LIFO (Last In, First Out)</strong>, que significa "Último a Entrar, Primeiro a Sair".
                </div>
                <p>Imagine que você tem uma pilha de livros. Para pegar o livro do meio, você precisa primeiro remover todos os livros que estão em cima dele. É exatamente assim que uma pilha funciona na programação!</p>
            </section>

            <section>
                <h2>Operações Principais</h2>
                <div class="operations">
                    <div class="operation-card">
                        <h3>PUSH</h3>
                        <p>Adiciona um elemento no topo da pilha</p>
                    </div>
                    <div class="operation-card">
                        <h3>POP</h3>
                        <p>Remove o elemento do topo da pilha</p>
                    </div>
                    <div class="operation-card">
                        <h3>PEEK</h3>
                        <p>Visualiza o elemento do topo sem remover</p>
                    </div>
                </div>
            </section>

            <section>
                <h2>Experimente a Pilha!</h2>
                <div class="demo-container">
                    <div class="controls">
                        <input type="text" id="inputValue" placeholder="Digite um valor">
                        <button onclick="pushElement()">PUSH (Adicionar)</button>
                        <button onclick="popElement()">POP (Remover)</button>
                        <button onclick="peekElement()">PEEK (Ver Topo)</button>
                    </div>
                    <div class="info-message" id="message">Digite um valor e clique em PUSH!</div>
                    <div class="stack-visual" id="stackVisual"></div>
                </div>
            </section>

            <section>
                <h2>Exemplos do Dia a Dia</h2>
                <ul>
                    <li><strong>Função "Desfazer":</strong> Editores de texto guardam suas ações numa pilha. Quando você clica em "Desfazer", o programa remove a última ação da pilha.</li>
                    <li><strong>Botão Voltar do Navegador:</strong> Cada página que você visita é adicionada numa pilha. O botão "Voltar" remove a página atual e volta para a anterior.</li>
                    <li><strong>Pilha de Pratos:</strong> Você sempre coloca e pega pratos do topo, nunca do meio ou de baixo.</li>
                    <li><strong>Histórico de Ligações:</strong> O último contato que você ligou aparece primeiro na lista.</li>
                </ul>
            </section>

            <section>
                <h2>Por que usar Pilhas?</h2>
                <div class="definition">
                    As pilhas são muito rápidas e simples! Todas as operações (adicionar, remover, visualizar) acontecem instantaneamente, independente de quantos elementos existem na pilha.
                </div>
                <p><strong>Vantagens:</strong></p>
                <ul>
                    <li>Operações muito rápidas</li>
                    <li>Simples de entender e usar</li>
                    <li>Perfeita para desfazer ações e navegação</li>
                </ul>
                <p style="margin-top: 15px;"><strong>Limitações:</strong></p>
                <ul>
                    <li>Só acessa o elemento do topo</li>
                    <li>Para pegar algo no meio, precisa remover tudo que está em cima</li>
                </ul>
            </section>
        </div>

        <footer>
            <p>Estrutura de Dados - Pilhas | Trabalho Educacional</p>
        </footer>
    </div>

    <script>
        let stack = [];

        function pushElement() {
            const input = document.getElementById('inputValue');
            const value = input.value.trim();
            
            if (value === '') {
                showMessage('⚠️ Digite um valor primeiro!');
                return;
            }
            
            stack.push(value);
            input.value = '';
            updateVisual();
            showMessage(`✅ "${value}" adicionado no TOPO da pilha!`);
        }

        function popElement() {
            if (stack.length === 0) {
                showMessage('❌ A pilha está vazia!');
                return;
            }
            
            const removed = stack.pop();
            updateVisual();
            showMessage(`🗑️ "${removed}" removido do TOPO da pilha!`);
        }

        function peekElement() {
            if (stack.length === 0) {
                showMessage('❌ A pilha está vazia!');
                return;
            }
            
            const top = stack[stack.length - 1];
            showMessage(`👀 Elemento no TOPO: "${top}"`);
        }

        function updateVisual() {
            const visual = document.getElementById('stackVisual');
            visual.innerHTML = '';
            
            if (stack.length === 0) {
                visual.innerHTML = '<div style="color: #999; padding: 40px; font-size: 1.2em;">Pilha Vazia</div>';
                return;
            }
            
            stack.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = 'stack-item';
                div.textContent = item;
                if (index === stack.length - 1) {
                    div.textContent += ' ⬅️ TOPO';
                    div.style.background = 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)';
                }
                visual.appendChild(div);
            });
        }

        function showMessage(text) {
            const message = document.getElementById('message');
            message.textContent = text;
        }

        document.getElementById('inputValue').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                pushElement();
            }
        });

        updateVisual();
    </script>
</body>
</html>