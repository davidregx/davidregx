<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Monedas - Solución de Canje</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2ecc71;
            --danger: #e74c3c;
            --warning: #f39c12;
            --dark: #2c3e50;
            --light: #ecf0f1;
            --whatsapp: #25D366;
        }
        
  * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
  body {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            color: #fff;
        }
        
 .container {
            background: rgba(0, 0, 0, 0.85);
            border-radius: 20px;
            padding: 30px;
            width: 100%;
            max-width: 800px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
  .header {
            margin-bottom: 25px;
            position: relative;
            z-index: 2;
        }
        
  h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
            color: #ffd700;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.7);
        }
        
  .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 25px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50px;
            padding: 5px;
        }
        
  .tab {
            padding: 12px 30px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            margin: 0 5px;
        }
        
 .tab.active {
            background: var(--primary);
            color: white;
        }
        
.section {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
 .section.active {
            display: block;
        }
        
 @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
 .card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin: 25px 0;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
.coins-section {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 25px 0;
            padding: 15px;
            background: rgba(255, 215, 0, 0.1);
            border-radius: 15px;
            border: 2px solid #ffd700;
        }
        
.coins-display {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
            margin-right: 25px;
        }
        
.coin-icon {
            color: #ffd700;
            margin-right: 10px;
            font-size: 2rem;
        }
        
 .btn {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            margin: 10px;
        }
        
 .btn i {
            margin-right: 8px;
        }
        
 .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
        }
        
 .btn:active {
            transform: translateY(1px);
        }
        
 .btn-warning {
            background: linear-gradient(to right, var(--warning), #ff6b00);
        }
        
.btn-danger {
            background: linear-gradient(to right, var(--danger), #c0392b);
        }
        
 .btn-whatsapp {
            background: var(--whatsapp);
        }
        
 .input-group {
            margin: 20px 0;
        }
        
  input, select {
            padding: 15px 20px;
            font-size: 1.1rem;
            border: none;
            border-radius: 50px;
            width: 100%;
            max-width: 300px;
            text-align: center;
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: 2px solid var(--primary);
            margin: 10px 0;
        }
        
 .result-container {
            min-height: 100px;
            background: rgba(0, 0, 0, 0.4);
            border-radius: 15px;
            padding: 20px;
            margin-top: 25px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            text-align: center;
        }
        
 .result-text {
            font-size: 1.2rem;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 10px;
            word-break: break-all;
        }
        
 .code-display {
            font-size: 1.4rem;
            font-weight: bold;
            background: rgba(0, 0, 0, 0.6);
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            border: 2px dashed var(--secondary);
            color: var(--secondary);
            letter-spacing: 3px;
        }
        
  .coin-package {
            display: inline-block;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            margin: 15px;
            width: 150px;
            border: 2px solid var(--warning);
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
.coin-package:hover {
            transform: scale(1.05);
            background: rgba(255, 255, 255, 0.15);
        }
        
 .coin-package.selected {
            background: rgba(255, 193, 7, 0.2);
            border-color: #ffc107;
            box-shadow: 0 0 15px rgba(255, 193, 7, 0.5);
        }
        
 .package-coins {
            font-size: 2rem;
            color: #ffd700;
            margin: 10px 0;
        }
        
 .package-price {
            font-size: 1.2rem;
            font-weight: bold;
        }
        
.instructions {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            margin: 20px 0;
            text-align: left;
            font-size: 0.95rem;
        }
        
 .instructions ol {
            padding-left: 20px;
            margin: 15px 0;
        }
        
 .instructions li {
            margin-bottom: 10px;
            line-height: 1.6;
        }
        
.success {
            color: var(--secondary);
        }
        
 .error {
            color: var(--danger);
        }
        
 .game-controls {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin: 20px 0;
        }
        
 .win-animation {
            animation: win-celebration 2s infinite;
        }
        
  @keyframes win-celebration {
            0% { text-shadow: 0 0 10px #ff0, 0 0 20px #ff0; }
            50% { text-shadow: 0 0 20px #ff0, 0 0 30px #ff0, 0 0 40px #ff0; }
            100% { text-shadow: 0 0 10px #ff0, 0 0 20px #ff0; }
        }
        
 .whatsapp-info {
            background: rgba(37, 211, 102, 0.1);
            border: 2px solid var(--whatsapp);
            border-radius: 15px;
            padding: 15px;
            margin: 20px 0;
        }
        
 .whatsapp-info h3 {
            color: var(--whatsapp);
            margin-bottom: 10px;
        }
        
 .whatsapp-btn-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 15px;
            flex-wrap: wrap;
        }
        
 .admin-codes-list {
            margin-top: 20px;
            max-height: 200px;
            overflow-y: auto;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            padding: 10px;
        }
        
 .code-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
 .code-item:last-child {
            border-bottom: none;
        }
        
 .code-value {
            font-weight: bold;
            letter-spacing: 1px;
        }
        
 .code-status {
            padding: 3px 8px;
            border-radius: 15px;
            font-size: 0.8rem;
        }
        
 .status-pending {
            background: rgba(243, 156, 18, 0.2);
            color: var(--warning);
        }
        
.status-paid {
            background: rgba(46, 204, 113, 0.2);
            color: var(--secondary);
        }
        
 .status-rejected {
            background: rgba(231, 76, 60, 0.2);
            color: var(--danger);
        }
        
 .status-used {
            background: rgba(155, 89, 182, 0.2);
            color: #9b59b6;
        }
        
 .select-code-btn {
            background: rgba(52, 152, 219, 0.3);
            border: none;
            color: var(--primary);
            padding: 5px 10px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 0.8rem;
        }
        
 @media (max-width: 600px) {
            .container {
                padding: 20px;
            }
            
  h1 {
                font-size: 2.2rem;
            }
            
 .tabs {
                flex-direction: column;
                border-radius: 15px;
            }
            
  .tab {
                margin: 5px 0;
                border-radius: 15px;
            }
            
 .coin-package {
                width: 130px;
                margin: 10px;
            }
            
.whatsapp-btn-container {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-coins"></i> Sistema de Monedas</h1>
            <p>Juego de Adivinar el Número</p>
        </div>
        
  <div class="tabs">
            <div class="tab active" data-tab="buy">Comprar Monedas</div>
            <div class="tab" data-tab="redeem">Canjear Código</div>
            <div class="tab" data-tab="play">Jugar</div>
            <div class="tab" data-tab="verify">Verificar Pago</div>
        </div>
        
        <!-- Sección de Compra de Monedas -->
 <div class="section active" id="buy-section">
            <div class="card">
                <h2><i class="fas fa-shopping-cart"></i> Comprar Monedas</h2>
                <p>Cada moneda cuesta 1 S/ y te permite un intento en el juego</p>
                
 <div class="input-group">
                    <h3>Selecciona un paquete:</h3>
                    <div class="packages">
                        <div class="coin-package" data-coins="5" data-price="5">
                            <div class="package-coins">5 <i class="fas fa-coins"></i></div>
                            <div class="package-price">5 S/</div>
                        </div>
                        <div class="coin-package" data-coins="10" data-price="10">
                            <div class="package-coins">10 <i class="fas fa-coins"></i></div>
                            <div class="package-price">10 S/</div>
                        </div>
                        <div class="coin-package" data-coins="20" data-price="20">
                            <div class="package-coins">20 <i class="fas fa-coins"></i></div>
                            <div class="package-price">20 S/</div>
                        </div>
                    </div>
                </div>
                
 <div class="whatsapp-info">
                    <h3><i class="fab fa-whatsapp"></i> Soporte por WhatsApp</h3>
                    <p>Para cualquier duda o problema, contáctame directamente:</p>
                    <p><strong>WhatsApp: 975 842 622</strong></p>
                </div>
                
  <button class="btn btn-warning" id="generate-code-btn">
                    <i class="fas fa-qrcode"></i> Generar Código de Pago
                </button>
                
 <div class="result-container">
                    <div class="result-text" id="buy-result">
                        Selecciona un paquete de monedas para continuar
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Sección de Canje de Código -->
 <div class="section" id="redeem-section">
            <div class="card">
                <h2><i class="fas fa-ticket-alt"></i> Canjear Código</h2>
                <p>Ingresa el código de verificación que recibiste</p>
                
 <div class="input-group">
                    <input type="text" id="redeem-code" placeholder="Ingresa tu código aquí">
                </div>
                
 <button class="btn" id="redeem-btn">
                    <i class="fas fa-gift"></i> Canjear Monedas
                </button>
                
<div class="result-container">
                    <div class="result-text" id="redeem-result">
                        El código válido agregará monedas a tu cuenta
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Sección del Juego -->
 <div class="section" id="play-section">
            <div class="card">
                <h2><i class="fas fa-gamepad"></i> Adivina el Número</h2>
                
 <div class="coins-section">
                    <div class="coins-display">
                        <span class="coin-icon"><i class="fas fa-coins"></i></span>
                        <span id="coins-count">0</span>
                    </div>
                </div>
                
 <div class="input-group">
                    <p>Adivina un número entre 1 y 100:</p>
                    <input type="number" id="guess-input" min="1" max="100" placeholder="1-100">
                </div>
                
<div class="game-controls">
                    <button class="btn" id="guess-btn">
                        <i class="fas fa-dice"></i> Adivinar (1 moneda)
                    </button>
                    <button class="btn btn-danger" id="reset-btn">
                        <i class="fas fa-redo"></i> Reiniciar Juego
                    </button>
                </div>
                
 <div class="result-container">
                    <div class="result-text" id="game-result">
                        ¡Usa tus monedas para empezar a jugar!
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Sección de Verificación (para administrador) -->
<div class="section" id="verify-section">
            <div class="card">
                <h2><i class="fas fa-user-shield"></i> Verificación de Pagos</h2>
                <p>Panel de administrador para verificar códigos generados</p>
                
<div class="instructions">
                    <h3>Instrucciones:</h3>
                    <ol>
                        <li>Cuando un cliente compra monedas, se genera un código único</li>
                        <li>El sistema guarda automáticamente el código en la base de datos local</li>
                        <li>Verifica que el pago se haya realizado correctamente</li>
                        <li>Actualiza el estado del código a "Pagado"</li>
                        <li>Cuando el cliente canjea el código, el sistema verifica que esté marcado como pagado</li>
                    </ol>
                </div>
                
 <div class="input-group">
                    <input type="text" id="admin-code" placeholder="Código a verificar">
                    <select id="payment-status">
                        <option value="pending">Pendiente</option>
                        <option value="paid">Pagado</option>
                        <option value="rejected">Rechazado</option>
                    </select>
                </div>
                
 <button class="btn" id="verify-btn">
                    <i class="fas fa-check-circle"></i> Actualizar Estado
                </button>
                
 <div class="admin-codes-list" id="codes-list">
                    <!-- Aquí se mostrarán los códigos existentes -->
                </div>
                
 <div class="result-container">
                    <div class="result-text" id="verify-result">
                        Aquí se mostrarán los códigos generados y su estado
                    </div>
                </div>
            </div>
        </div>
    </div>

<script>
        document.addEventListener('DOMContentLoaded', () => {
            // Variables globales
            let coins = 0;
            let secretNumber = Math.floor(Math.random() * 100) + 1;
            let attempts = 0;
            let selectedPackage = null;
            let generatedCodes = {};
            const adminPhone = "51975842622"; // Tu número de WhatsApp en formato internacional
            
            // Elementos del DOM
            const coinsCount = document.getElementById('coins-count');
            const sections = document.querySelectorAll('.section');
            const tabs = document.querySelectorAll('.tab');
            const packages = document.querySelectorAll('.coin-package');
            const buyResult = document.getElementById('buy-result');
            const redeemResult = document.getElementById('redeem-result');
            const gameResult = document.getElementById('game-result');
            const verifyResult = document.getElementById('verify-result');
            const codesList = document.getElementById('codes-list');
            
            // Inicialización
            loadCoins();
            loadGeneratedCodes();
            renderCodesList();
            
            // Navegación por pestañas
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    tabs.forEach(t => t.classList.remove('active'));
                    sections.forEach(s => s.classList.remove('active'));
                    
                    tab.classList.add('active');
                    document.getElementById(`${tab.dataset.tab}-section`).classList.add('active');
                    
                    // Actualizar lista al entrar a verificación
                    if (tab.dataset.tab === 'verify') {
                        renderCodesList();
                    }
                });
            });
            
            // Selección de paquete de monedas
            packages.forEach(package => {
                package.addEventListener('click', () => {
                    packages.forEach(p => p.classList.remove('selected'));
                    package.classList.add('selected');
                    selectedPackage = {
                        coins: parseInt(package.dataset.coins),
                        price: parseInt(package.dataset.price)
                    };
                    buyResult.textContent = `Paquete seleccionado: ${selectedPackage.coins} monedas (${selectedPackage.price} S/)`;
                    buyResult.className = "result-text";
                });
            });
            
            // Generar código de pago
            document.getElementById('generate-code-btn').addEventListener('click', () => {
                if (!selectedPackage) {
                    buyResult.textContent = "⚠️ Por favor selecciona un paquete de monedas";
                    buyResult.className = "result-text error";
                    return;
                }
                
                // Generar código único
                const code = generateUniqueCode();
                
                // Guardar código en el sistema
                generatedCodes[code] = {
                    coins: selectedPackage.coins,
                    price: selectedPackage.price,
                    status: "pending", // Estado inicial pendiente
                    timestamp: new Date().toISOString()
                };
                
                // Crear mensaje para WhatsApp
                const whatsappMessage = `Hola, acabo de generar el código ${code} para comprar ${selectedPackage.coins} monedas. Adjunto mi comprobante de pago.`;
                const whatsappUrl = `https://wa.me/${adminPhone}?text=${encodeURIComponent(whatsappMessage)}`;
                
                // Mostrar código al usuario con botón de WhatsApp
                buyResult.innerHTML = `
                    <div class="success">¡Código generado con éxito!</div>
                    <div class="code-display">${code}</div>
                    <p>Envía ${selectedPackage.price} S/ a la cuenta bancaria y luego envía el comprobante con este código a WhatsApp.</p>
                    
                    <div class="whatsapp-btn-container">
                        <a href="${whatsappUrl}" target="_blank" class="btn btn-whatsapp">
                            <i class="fab fa-whatsapp"></i> Enviar por WhatsApp
                        </a>
                        <button class="btn" id="copy-code-btn">
                            <i class="fas fa-copy"></i> Copiar Código
                        </button>
                    </div>
                    
                    <p>Una vez verificado el pago, podrás canjear este código para obtener tus monedas</p>
                `;
                buyResult.className = "result-text";
                
                // Agregar evento para copiar el código
                document.getElementById('copy-code-btn').addEventListener('click', () => {
                    navigator.clipboard.writeText(code);
                    const copyBtn = document.getElementById('copy-code-btn');
                    copyBtn.innerHTML = '<i class="fas fa-check"></i> ¡Copiado!';
                    copyBtn.style.background = 'var(--secondary)';
                    setTimeout(() => {
                        copyBtn.innerHTML = '<i class="fas fa-copy"></i> Copiar Código';
                        copyBtn.style.background = '';
                    }, 2000);
                });
                
                // Guardar en localStorage
                saveGeneratedCodes();
                renderCodesList();
                
                // Limpiar selección
                packages.forEach(p => p.classList.remove('selected'));
                selectedPackage = null;
            });
            
            // Canjear código
            document.getElementById('redeem-btn').addEventListener('click', () => {
                const code = document.getElementById('redeem-code').value.trim().toUpperCase();
                
                if (!code) {
                    redeemResult.textContent = "⚠️ Por favor ingresa un código";
                    redeemResult.className = "result-text error";
                    return;
                }
                
                // Verificar si el código existe
                if (!generatedCodes[code]) {
                    redeemResult.textContent = "⚠️ Código inválido o no encontrado";
                    redeemResult.className = "result-text error";
                    return;
                }
                
                // Verificar estado del pago
                if (generatedCodes[code].status !== "paid") {
                    redeemResult.innerHTML = `
                        <div class="error">⚠️ Este código aún no ha sido verificado</div>
                        <p>Por favor espera a que el administrador verifique tu pago</p>
                        <p>Estado actual: ${getStatusText(generatedCodes[code].status)}</p>
                    `;
                    redeemResult.className = "result-text";
                    return;
                }
                
                // Agregar monedas
                const coinsToAdd = generatedCodes[code].coins;
                coins += coinsToAdd;
                saveCoins();
                
                // Mostrar resultado
                redeemResult.innerHTML = `
                    <div class="success">¡Código canjeado con éxito!</div>
                    <p>Has recibido ${coinsToAdd} monedas 🪙</p>
                    <p>Ahora tienes un total de ${coins} monedas</p>
                `;
                redeemResult.className = "result-text";
                
                // Eliminar código (marcar como usado)
                generatedCodes[code].status = "used";
                saveGeneratedCodes();
                renderCodesList();
                
                // Actualizar contador
                coinsCount.textContent = coins;
                
                // Cambiar a la pestaña de juego
                setTimeout(() => {
                    tabs.forEach(t => t.classList.remove('active'));
                    sections.forEach(s => s.classList.remove('active'));
                    document.querySelector('.tab[data-tab="play"]').classList.add('active');
                    document.getElementById('play-section').classList.add('active');
                }, 2000);
            });
            
            // Jugar - Adivinar número
            document.getElementById('guess-btn').addEventListener('click', () => {
                if (coins <= 0) {
                    gameResult.textContent = "⚠️ ¡No tienes monedas! Compra más monedas para jugar";
                    gameResult.className = "result-text error";
                    return;
                }
                
                const guess = parseInt(document.getElementById('guess-input').value);
                
                // Validar entrada
                if (isNaN(guess)) {
                    gameResult.textContent = "⚠️ Por favor ingresa un número válido";
                    gameResult.className = "result-text error";
                    return;
                }
                
                if (guess < 1 || guess > 100) {
                    gameResult.textContent = "⚠️ El número debe estar entre 1 y 100";
                    gameResult.className = "result-text error";
                    return;
                }
                
                // Consumir moneda
                coins--;
                saveCoins();
                coinsCount.textContent = coins;
                attempts++;
                
                // Verificar si es correcto
                if (guess === secretNumber) {
                    gameResult.innerHTML = `🎉 ¡FELICIDADES! Adivinaste el número <strong>${secretNumber}</strong> en ${attempts} intentos.`;
                    gameResult.classList.add('success', 'win-animation');
                    document.getElementById('guess-input').disabled = true;
                    document.getElementById('guess-btn').disabled = true;
                } else if (guess < secretNumber) {
                    gameResult.innerHTML = `🔺 El número secreto es <strong>MAYOR</strong> que ${guess}.`;
                    gameResult.className = "result-text";
                } else {
                    gameResult.innerHTML = `🔻 El número secreto es <strong>MENOR</strong> que ${guess}.`;
                    gameResult.className = "result-text";
                }
                
                // Limpiar campo
                document.getElementById('guess-input').value = '';
                document.getElementById('guess-input').focus();
            });
            
            // Reiniciar juego
            document.getElementById('reset-btn').addEventListener('click', () => {
                secretNumber = Math.floor(Math.random() * 100) + 1;
                attempts = 0;
                document.getElementById('guess-input').disabled = false;
                document.getElementById('guess-btn').disabled = false;
                gameResult.textContent = "¡Juego reiniciado! Adivina un nuevo número";
                gameResult.className = "result-text";
                document.getElementById('guess-input').focus();
            });
            
            // Verificar pago (panel admin)
            document.getElementById('verify-btn').addEventListener('click', () => {
                const code = document.getElementById('admin-code').value.trim().toUpperCase();
                const status = document.getElementById('payment-status').value;
                
                if (!code) {
                    verifyResult.textContent = "⚠️ Por favor ingresa un código";
                    verifyResult.className = "result-text error";
                    return;
                }
                
                if (!generatedCodes[code]) {
                    verifyResult.textContent = "⚠️ Código no encontrado en el sistema";
                    verifyResult.className = "result-text error";
                    return;
                }
                
                // Actualizar estado
                generatedCodes[code].status = status;
                saveGeneratedCodes();
                renderCodesList();
                
                verifyResult.innerHTML = `
                    <div class="success">Estado actualizado correctamente</div>
                    <p>Código: <strong>${code}</strong></p>
                    <p>Monedas: ${generatedCodes[code].coins}</p>
                    <p>Monto: ${generatedCodes[code].price} S/</p>
                    <p>Estado: ${getStatusText(status)}</p>
                `;
                verifyResult.className = "result-text";
            });
            
            // Función para generar un código único
            function generateUniqueCode() {
                const chars = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789'; // Excluir caracteres ambiguos
                let code = '';
                
                // Generar hasta obtener un código único
                do {
                    code = '';
                    for (let i = 0; i < 8; i++) {
                        code += chars.charAt(Math.floor(Math.random() * chars.length));
                    }
                } while (generatedCodes[code]); // Asegurar que no exista
                
                return code;
            }
            
            // Obtener texto del estado
            function getStatusText(status) {
                switch(status) {
                    case 'pending': return '<span style="color: orange">Pendiente</span>';
                    case 'paid': return '<span style="color: #2ecc71">Pagado</span>';
                    case 'rejected': return '<span style="color: #e74c3c">Rechazado</span>';
                    case 'used': return '<span style="color: #9b59b6">Usado</span>';
                    default: return status;
                }
            }
            
            // Guardar monedas en localStorage
            function saveCoins() {
                localStorage.setItem('gameCoins', coins.toString());
            }
            
            // Cargar monedas desde localStorage
            function loadCoins() {
                const savedCoins = localStorage.getItem('gameCoins');
                coins = savedCoins ? parseInt(savedCoins) : 0;
                coinsCount.textContent = coins;
            }
            
            // Guardar códigos generados
            function saveGeneratedCodes() {
                localStorage.setItem('generatedCodes', JSON.stringify(generatedCodes));
            }
            
            // Cargar códigos generados
            function loadGeneratedCodes() {
                const savedCodes = localStorage.getItem('generatedCodes');
                if (savedCodes) {
                    try {
                        generatedCodes = JSON.parse(savedCodes);
                    } catch (e) {
                        console.error("Error parsing generatedCodes:", e);
                        generatedCodes = {};
                    }
                } else {
                    generatedCodes = {};
                }
            }
            
            // Renderizar lista de códigos en el panel de administración
            function renderCodesList() {
                codesList.innerHTML = '';
                
                if (Object.keys(generatedCodes).length === 0) {
                    codesList.innerHTML = '<p>No hay códigos generados</p>';
                    return;
                }
                
                const title = document.createElement('h3');
                title.textContent = 'Códigos Generados:';
                title.style.marginBottom = '10px';
                title.style.textAlign = 'center';
                codesList.appendChild(title);
                
                Object.entries(generatedCodes).forEach(([code, details]) => {
                    const item = document.createElement('div');
                    item.className = 'code-item';
                    
                    const codeSpan = document.createElement('span');
                    codeSpan.className = 'code-value';
                    codeSpan.textContent = code;
                    
                    const statusSpan = document.createElement('span');
                    statusSpan.className = `code-status status-${details.status}`;
                    statusSpan.textContent = getStatusText(details.status).replace(/<\/?span[^>]*>/g, '');
                    
                    const selectBtn = document.createElement('button');
                    selectBtn.className = 'select-code-btn';
                    selectBtn.innerHTML = '<i class="fas fa-arrow-right"></i> Seleccionar';
                    selectBtn.addEventListener('click', () => {
                        document.getElementById('admin-code').value = code;
                        document.getElementById('payment-status').value = details.status;
                    });
                    
                    item.appendChild(codeSpan);
                    item.appendChild(statusSpan);
                    item.appendChild(selectBtn);
                    
                    codesList.appendChild(item);
                });
            }
        });
    </script>
</body>
</html>
