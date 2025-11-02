# CARDS
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CARDS - Design e Negociação de Veículos</title>
    <style>
        :root {
            --azul: rgb(0,0,255);
            --ouro: rgb(255,215,0);
            --vermelho: rgb(255, 0, 0);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--azul) 0%, #00008b 100%);
            color: white;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Login Styles */
        .login-container {
            background: rgba(255,255,255,0.1);
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 400px;
            margin: 100px auto;
            border: 2px solid var(--ouro);
        }

        .logo {
            text-align: center;
            margin-bottom: 30px;
        }

        .logo h1 {
            color: var(--ouro);
            font-size: 28px;
            margin-bottom: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid var(--ouro);
            border-radius: 8px;
            font-size: 16px;
            background: rgba(255,255,255,0.9);
        }

        .btn {
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-primary {
            background: var(--vermelho);
            color: white;
            width: 100%;
        }

        .btn-primary:hover {
            background: #cc0000;
            transform: translateY(-2px);
        }

        /* Dashboard */
        .dashboard {
            display: none;
        }

        .user-info {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            border: 2px solid var(--vermelho);
        }

        .user-balance {
            font-size: 24px;
            color: var(--ouro);
            font-weight: bold;
        }

        .options-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .option-card {
            background: rgba(255,255,255,0.1);
            padding: 25px;
            border-radius: 10px;
            border: 2px solid var(--vermelho);
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }

        .option-card:hover {
            transform: translateY(-5px);
            background: rgba(255,255,255,0.2);
        }

        .option-card h3 {
            color: var(--ouro);
            margin-bottom: 10px;
            font-size: 22px;
        }

        /* Popup Styles */
        .popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .popup-content {
            background: linear-gradient(135deg, var(--azul) 0%, #00008b 100%);
            padding: 40px;
            border-radius: 15px;
            border: 3px solid var(--ouro);
            text-align: center;
            max-width: 600px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }

        .popup h2 {
            color: var(--ouro);
            margin-bottom: 20px;
        }

        .car-models-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin: 30px 0;
        }

        .model-card {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 10px;
            border: 2px solid var(--vermelho);
            cursor: pointer;
            transition: all 0.3s;
        }

        .model-card:hover {
            transform: scale(1.05);
            background: rgba(255,255,255,0.2);
        }

        .model-card h4 {
            color: var(--ouro);
            margin-bottom: 10px;
        }

        .model-stats {
            font-size: 12px;
            color: white;
        }

        /* Drawing Canvas */
        .drawing-container {
            display: none;
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }

        .drawing-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--azul);
        }

        .drawing-header h2 {
            color: var(--vermelho);
        }

        .tools-panel {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
            padding: 15px;
            background: #f0f0f0;
            border-radius: 8px;
        }

        .tool-group {
            display: flex;
            gap: 5px;
            align-items: center;
        }

        .tool-btn {
            padding: 8px 12px;
            background: var(--azul);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .tool-btn.active {
            background: var(--vermelho);
        }

        .tool-btn:hover {
            transform: translateY(-2px);
        }

        #drawingCanvas {
            border: 3px solid var(--ouro);
            border-radius: 10px;
            background: white;
            cursor: crosshair;
            display: block;
            margin: 0 auto;
        }

        /* Registration Form */
        .registration-form {
            display: none;
            background: rgba(255,255,255,0.1);
            padding: 30px;
            border-radius: 15px;
            border: 2px solid var(--ouro);
            margin-top: 20px;
        }

        .form-row {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            flex: 1;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: var(--ouro);
            font-weight: bold;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 10px;
            border: 2px solid var(--ouro);
            border-radius: 5px;
            background: rgba(255,255,255,0.9);
        }

        /* Car Cards */
        .car-card {
            background: white;
            border: 3px solid var(--ouro);
            border-radius: 10px;
            padding: 15px;
            margin: 10px;
            width: 144px;
            height: 96px;
            display: inline-block;
            position: relative;
            color: black;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .car-card h4 {
            color: var(--azul);
            margin-bottom: 5px;
            font-size: 14px;
        }

        .car-stats {
            font-size: 10px;
            margin-top: 5px;
        }

        .qr-code {
            position: absolute;
            bottom: 5px;
            right: 5px;
            width: 30px;
            height: 30px;
            background: #333;
            color: white;
            font-size: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 3px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Tela de Login -->
        <div class="login-container" id="loginContainer">
            <div class="logo">
                <h1>CARDS</h1>
                <p>Faça login em sua conta</p>
            </div>
            <form id="loginForm">
                <div class="form-group">
                    <input type="email" id="email" placeholder="seu@email.com" required>
                </div>
                <div class="form-group">
                    <input type="password" id="password" placeholder="Sua senha" required>
                </div>
                <button type="submit" class="btn btn-primary">Entrar</button>
            </form>
        </div>

        <!-- Dashboard Principal -->
        <div class="dashboard" id="dashboard">
            <div class="user-info">
                <h2>Bem-vindo ao CARDS!</h2>
                <p class="user-balance">Saldo: O$ <span id="userBalance">111,00</span></p>
            </div>
            
            <div class="options-grid">
                <div class="option-card" onclick="startCarDesign()">
                    <h3>🏎️ Desenhar Carro</h3>
                    <p>Crie seu veículo personalizado</p>
                </div>
                <div class="option-card" onclick="showMarketplace()">
                    <h3>💰 Negociar</h3>
                    <p>Compre e venda veículos</p>
                </div>
                <div class="option-card" onclick="startNegotiationCourse()">
                    <h3>🎓 Curso Negociação</h3>
                    <p>Aprenda a negociar como um profissional</p>
                </div>
                <div class="option-card" onclick="showVehicleFeed()">
                    <h3>📰 Feed de Veículos</h3>
                    <p>Veja as criações de outros usuários</p>
                </div>
            </div>

            <!-- Feed de Veículos -->
            <div id="vehicleFeed" style="margin-top: 30px;">
                <h2 style="color: var(--ouro); margin-bottom: 20px;">Veículos em Destaque</h2>
                <div id="feedContent"></div>
            </div>
        </div>

        <!-- Área de Desenho -->
        <div class="drawing-container" id="drawingContainer">
            <div class="drawing-header">
                <h2>Desenhando seu <span id="currentModel">CARRO</span></h2>
                <button class="btn" onclick="backToDashboard()" style="background: var(--vermelho);">Voltar ao Dashboard</button>
            </div>
            
            <div class="tools-panel">
                <div class="tool-group">
                    <button class="tool-btn active" onclick="setTool('pencil')">✏️ Lápis</button>
                    <button class="tool-btn" onclick="setTool('line')">📏 Linha</button>
                    <button class="tool-btn" onclick="setTool('rectangle')">⬜ Retângulo</button>
                    <button class="tool-btn" onclick="setTool('circle')">⭕ Círculo</button>
                    <button class="tool-btn" onclick="setTool('eraser')">🧽 Borracha</button>
                </div>
                <div class="tool-group">
                    <button class="tool-btn" onclick="moveLayer('back')">⬅️ Camada Trás</button>
                    <button class="tool-btn" onclick="moveLayer('front')">➡️ Camada Frente</button>
                </div>
                <div class="tool-group">
                    <input type="color" id="colorPicker" value="#000000">
                    <input type="range" id="brushSize" min="1" max="20" value="2">
                    <button class="btn" onclick="clearCanvas()" style="background: var(--azul);">🧹 Limpar</button>
                </div>
                <div class="tool-group">
                    <button class="btn" onclick="finishDrawing()" style="background: var(--ouro); color: black;">✅ Carro Pronto</button>
                </div>
            </div>
            <canvas id="drawingCanvas" width="800" height="500"></canvas>
        </div>

        <!-- Formulário de Registro do Veículo -->
        <div class="registration-form" id="registrationForm">
            <h2 style="color: var(--ouro); text-align: center; margin-bottom: 20px;">Registrar seu Veículo</h2>
            <div class="form-row">
                <div class="form-group">
                    <label>Nome do Veículo:</label>
                    <input type="text" id="vehicleName" placeholder="Ex: Super Veloz">
                </div>
                <div class="form-group">
                    <label>Cor Predominante:</label>
                    <input type="text" id="vehicleColor" placeholder="Ex: Vermelho">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>Tipo de Alimentação:</label>
                    <select id="fuelType">
                        <option value="GASOLINA">GASOLINA</option>
                        <option value="ETANOL">ETANOL</option>
                        <option value="FLEX">FLEX</option>
                        <option value="HÍBRIDO">HÍBRIDO</option>
                        <option value="ELÉTRICO">ELÉTRICO</option>
                        <option value="DIESEL">DIESEL</option>
                        <option value="URÂNIO">URÂNIO</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Placa:</label>
                    <input type="text" id="vehiclePlate" readonly>
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>Número do Chassi:</label>
                    <input type="text" id="vehicleChassis" readonly>
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>Óleo:</label>
                    <input type="text" value="ÓLEO NOVO" readonly>
                </div>
                <div class="form-group">
                    <label>Filtro de Óleo:</label>
                    <input type="text" value="FILTRO NOVO" readonly>
                </div>
                <div class="form-group">
                    <label>Filtro de Ar:</label>
                    <input type="text" value="FILTRO NOVO" readonly>
                </div>
                <div class="form-group">
                    <label>IPVA:</label>
                    <input type="text" value="IPVA PAGO" readonly>
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>O que fazer com o veículo?</label>
                    <select id="vehicleAction" onchange="toggleActionFields()">
                        <option value="">Selecione</option>
                        <option value="VENDER">VENDER</option>
                        <option value="LEILOAR">LEILOAR</option>
                    </select>
                </div>
            </div>
            <div id="actionFields" style="display: none; margin-top: 20px;">
                <!-- Campos dinâmicos para venda/leilão -->
            </div>
            <button class="btn btn-primary" onclick="registerVehicle()" style="margin-top: 20px; width: 100%;">Finalizar Registro</button>
        </div>
    </div>

    <!-- Popups -->
    <div class="popup" id="modelSelectionPopup">
        <div class="popup-content">
            <h2>Qual modelo de veículo você quer desenhar?</h2>
            <div class="car-models-grid">
                <div class="model-card" onclick="selectCarModel('SEDAN', 17000, 9, 75, 12)">
                    <h4>SEDAN</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 17.000,00</div>
                        <div>Consumo: 9 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('COUPÊ', 120000, 6, 75, 12)">
                    <h4>COUPÊ</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 120.000,00</div>
                        <div>Consumo: 6 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('HATCH', 17000, 9, 75, 12)">
                    <h4>HATCH</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 17.000,00</div>
                        <div>Consumo: 9 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('LIMOUSINE', 151, 5, 75, 12)">
                    <h4>LIMOUSINE</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 151,00</div>
                        <div>Consumo: 5 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('SMARTCAR', 61000, 32, 75, 12)">
                    <h4>SMARTCAR</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 61.000,00</div>
                        <div>Consumo: 32 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('WAGON', 38000, 10, 75, 12)">
                    <h4>WAGON</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 38.000,00</div>
                        <div>Consumo: 10 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('DRAGSTER', 490000, 1, 75, 12)">
                    <h4>DRAGSTER</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 490.000,00</div>
                        <div>Consumo: 1 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('CONVERSÍVEL', 20000, 9, 75, 12)">
                    <h4>CONVERSÍVEL</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 20.000,00</div>
                        <div>Consumo: 9 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('MONSTERCAR', 321000, 2, 75, 12)">
                    <h4>MONSTERCAR</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 321.000,00</div>
                        <div>Consumo: 2 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
                <div class="model-card" onclick="selectCarModel('PICKUP', 20000, 9, 75, 12)">
                    <h4>PICKUP</h4>
                    <div class="model-stats">
                        <div>Preço: O$ 20.000,00</div>
                        <div>Consumo: 9 KM/L</div>
                        <div>Potência: 75 CV</div>
                        <div>0-100: 12 seg</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="popup" id="confirmDrawingPopup">
        <div class="popup-content">
            <h2>Tem certeza que sua máquina já está pronta?</h2>
            <div style="margin: 30px 0;">
                <button class="btn btn-primary" onclick="confirmDrawing()" style="margin: 0 10px;">SIM</button>
                <button class="btn" onclick="closeConfirmPopup()" style="background: var(--ouro); color: black; margin: 0 10px;">VOLTAR AO PROJETO</button>
            </div>
        </div>
    </div>

    <div class="popup" id="rewardPopup">
        <div class="popup-content">
            <h2>Boa escolha!</h2>
            <p>Você ganhou:</p>
            <div style="font-size: 32px; font-weight: bold; color: var(--ouro); text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); margin: 20px 0;">O$ 111,00 oros</div>
            <p>Bons negócios!</p>
            <button class="btn btn-primary" onclick="closeRewardPopup()" style="margin-top: 20px;">OK</button>
        </div>
    </div>

    <script>
        // Dados do usuário e veículos
        let userData = {
            balance: 111,
            vehicles: [],
            selectedModel: null
        };

        // Sistema de desenho
        let currentTool = 'pencil';
        let isDrawing = false;
        let lastX = 0;
        let lastY = 0;
        const canvas = document.getElementById('drawingCanvas');
        const ctx = canvas.getContext('2d');

        // Login - VERSÃO ORIGINAL QUE FUNCIONA
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            // Validação simples
            if(email && password) {
                // Esconde o login e mostra o dashboard
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('dashboard').style.display = 'block';
                
                // Mostra popup de recompensa
                document.getElementById('rewardPopup').style.display = 'flex';
                
                // Atualiza saldo
                updateBalance();
                generateFeed();
            } else {
                alert('Por favor, preencha todos os campos.');
            }
        });

        // Função para atualizar saldo
        function updateBalance() {
            document.getElementById('userBalance').textContent = userData.balance.toLocaleString('pt-BR', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
        }

        // Função para fechar popup de recompensa
        function closeRewardPopup() {
            document.getElementById('rewardPopup').style.display = 'none';
        }

        // Funções de navegação
        function backToDashboard() {
            document.getElementById('drawingContainer').style.display = 'none';
            document.getElementById('registrationForm').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
        }

        function startCarDesign() {
            document.getElementById('modelSelectionPopup').style.display = 'flex';
        }

        function showMarketplace() {
            alert('Mercado de negociações em desenvolvimento!');
        }

        function startNegotiationCourse() {
            alert('Curso de negociação em desenvolvimento!');
        }

        function showVehicleFeed() {
            generateFeed();
        }

        // Sistema de seleção de modelo
        function selectCarModel(model, price, kml, cv, acceleration) {
            userData.selectedModel = {
                type: model,
                price: price,
                kml: kml,
                cv: cv,
                acceleration: acceleration
            };
            
            document.getElementById('modelSelectionPopup').style.display = 'none';
            document.getElementById('dashboard').style.display = 'none';
            document.getElementById('drawingContainer').style.display = 'block';
            document.getElementById('currentModel').textContent = model;
            
            // Inicializar canvas
            ctx.lineWidth = document.getElementById('brushSize').value;
            ctx.lineJoin = 'round';
            ctx.lineCap = 'round';
            ctx.strokeStyle = document.getElementById('colorPicker').value;
        }

        // Funções do sistema de desenho
        function setTool(tool) {
            currentTool = tool;
            document.querySelectorAll('.tool-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
        }

        function moveLayer(direction) {
            alert(`Camada movida para ${direction === 'back' ? 'trás' : 'frente'}`);
        }

        // Event listeners para desenho
        canvas.addEventListener('mousedown', startDrawing);
        canvas.addEventListener('mousemove', draw);
        canvas.addEventListener('mouseup', stopDrawing);
        canvas.addEventListener('mouseout', stopDrawing);

        function startDrawing(e) {
            isDrawing = true;
            [lastX, lastY] = [e.offsetX, e.offsetY];
        }

        function draw(e) {
            if (!isDrawing) return;
            
            ctx.strokeStyle = document.getElementById('colorPicker').value;
            ctx.lineWidth = document.getElementById('brushSize').value;

            ctx.beginPath();
            ctx.moveTo(lastX, lastY);
            ctx.lineTo(e.offsetX, e.offsetY);
            ctx.stroke();
            [lastX, lastY] = [e.offsetX, e.offsetY];
        }

        function stopDrawing() {
            isDrawing = false;
        }

        function clearCanvas() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
        }

        function finishDrawing() {
            document.getElementById('confirmDrawingPopup').style.display = 'flex';
        }

        function closeConfirmPopup() {
            document.getElementById('confirmDrawingPopup').style.display = 'none';
        }

        function confirmDrawing() {
            document.getElementById('confirmDrawingPopup').style.display = 'none';
            document.getElementById('drawingContainer').style.display = 'none';
            document.getElementById('registrationForm').style.display = 'block';
            
            // Gerar placa e chassi
            document.getElementById('vehiclePlate').value = generatePlate();
            document.getElementById('vehicleChassis').value = generateChassis();
        }

        function generatePlate() {
            const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
            let plate = '';
            for (let i = 0; i < 3; i++) {
                plate += letters.charAt(Math.floor(Math.random() * letters.length));
            }
            for (let i = 0; i < 4; i++) {
                plate += Math.floor(Math.random() * 10);
            }
            return plate;
        }

        function generateChassis() {
            let chassis = '';
            for (let i = 0; i < 12; i++) {
                chassis += Math.floor(Math.random() * 10);
            }
            return chassis;
        }

        function toggleActionFields() {
            const action = document.getElementById('vehicleAction').value;
            const actionFields = document.getElementById('actionFields');
            
            if (action) {
                actionFields.style.display = 'block';
                if (action === 'VENDER') {
                    actionFields.innerHTML = `
                        <div class="form-group">
                            <label>Quanto?</label>
                            <input type="number" id="sellPrice" placeholder="Digite o valor">
                        </div>
                    `;
                } else if (action === 'LEILOAR') {
                    actionFields.innerHTML = `
                        <div class="form-group">
                            <label>Lance Inicial</label>
                            <input type="number" id="initialBid" placeholder="Lance inicial">
                        </div>
                        <div class="form-group">
                            <label>Data Final do Leilão</label>
                            <input type="date" id="auctionEndDate">
                        </div>
                    `;
                }
            } else {
                actionFields.style.display = 'none';
            }
        }

        function registerVehicle() {
            const vehicleData = {
                ...userData.selectedModel,
                name: document.getElementById('vehicleName').value,
                color: document.getElementById('vehicleColor').value,
                fuel: document.getElementById('fuelType').value,
                plate: document.getElementById('vehiclePlate').value,
                chassis: document.getElementById('vehicleChassis').value,
                image: canvas.toDataURL(),
                created: new Date(),
                condition: 100
            };
            
            userData.vehicles.push(vehicleData);
            alert('Veículo registrado com sucesso!');
            
            // Voltar ao dashboard
            document.getElementById('registrationForm').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            generateFeed();
        }

        function generateFeed() {
            const feed = document.getElementById('feedContent');
            feed.innerHTML = '';
            
            // Gerar alguns veículos de exemplo
            const sampleVehicles = [
                { name: 'Carro Exemplo 1', type: 'SEDAN', price: 17000, kml: 9, cv: 75 },
                { name: 'Carro Exemplo 2', type: 'COUPÊ', price: 120000, kml: 6, cv: 75 },
                { name: 'Carro Exemplo 3', type: 'HATCH', price: 17000, kml: 9, cv: 75 },
                { name: 'Carro Exemplo 4', type: 'SMARTCAR', price: 61000, kml: 32, cv: 75 }
            ];
            
            sampleVehicles.forEach(vehicle => {
                const card = document.createElement('div');
                card.className = 'car-card';
                card.innerHTML = `
                    <h4>${vehicle.name}</h4>
                    <div class="car-stats">
                        <div>Tipo: ${vehicle.type}</div>
                        <div>Preço: O$ ${vehicle.price.toLocaleString()}</div>
                        <div>Consumo: ${vehicle.kml} KM/L</div>
                        <div>Potência: ${vehicle.cv} CV</div>
                    </div>
                    <div class="qr-code">QR</div>
                `;
                feed.appendChild(card);
            });
        }
    </script>
</body>
</html>










