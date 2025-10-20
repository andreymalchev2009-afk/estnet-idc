# testnet-idc
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ideal Coin Blockchain</title>
    <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Все стили остаются без изменений */
        :root {
            --primary: #121212;
            --secondary: #1e1e1e;
            --accent: #2a2a2a;
            --light: #2d2d2d;
            --success: #4CAF50;
            --warning: #FF9800;
            --text: #e0e0e0;
            --text-secondary: #a0a0a0;
            --border: #333333;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Manrope', sans-serif;
        }
        
        body {
            background-color: var(--primary);
            color: var(--text);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--secondary), var(--accent));
            color: var(--text);
            padding: 1.5rem 0;
            text-align: center;
            border-radius: 0 0 12px 12px;
            margin-bottom: 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-left: 2rem;
            padding-right: 2rem;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
            border-bottom: 1px solid var(--border);
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
            font-weight: 700;
            background: linear-gradient(90deg, #e0e0e0, #a0a0a0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.8;
            font-weight: 400;
            color: var(--text-secondary);
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .user-avatar {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            background: linear-gradient(135deg, #333, #555);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            border: 2px solid var(--border);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }
        
        .wallet-info {
            background: rgba(255, 255, 255, 0.05);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-weight: 600;
            border: 1px solid var(--border);
        }
        
        .logout-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            color: var(--text);
            padding: 0.5rem 1rem;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }
        
        .logout-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
        }
        
        .card {
            background: var(--secondary);
            border-radius: 12px;
            padding: 1.8rem;
            margin-bottom: 1.8rem;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid var(--border);
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 28px rgba(0, 0, 0, 0.3);
        }
        
        .card-title {
            font-size: 1.5rem;
            color: var(--text);
            margin-bottom: 1.2rem;
            border-bottom: 1px solid var(--border);
            padding-bottom: 0.7rem;
            font-weight: 600;
        }
        
        .auth-container {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
        }
        
        .auth-form {
            background: var(--secondary);
            border-radius: 12px;
            padding: 2.2rem;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 420px;
            border: 1px solid var(--border);
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        label {
            display: block;
            margin-bottom: 0.6rem;
            font-weight: 600;
            color: var(--text);
        }
        
        input[type="text"],
        input[type="password"],
        select {
            width: 100%;
            padding: 0.85rem;
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 1rem;
            font-family: 'Manrope', sans-serif;
            background: var(--accent);
            color: var(--text);
            transition: all 0.3s;
        }
        
        input[type="text"]:focus,
        input[type="password"]:focus,
        select:focus {
            outline: none;
            border-color: var(--text-secondary);
            box-shadow: 0 0 0 2px rgba(255, 255, 255, 0.1);
        }
        
        .tabs {
            display: flex;
            margin-bottom: 1.8rem;
            border-bottom: 1px solid var(--border);
        }
        
        .tab {
            padding: 0.85rem 1.7rem;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            font-weight: 500;
            transition: all 0.3s;
            color: var(--text-secondary);
        }
        
        .tab.active {
            border-bottom: 3px solid var(--success);
            font-weight: 600;
            color: var(--text);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .mining-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.8rem;
        }
        
        .mining-params {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.2rem;
        }
        
        .param-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            background: var(--accent);
            border-radius: 8px;
            transition: all 0.3s;
            border: 1px solid var(--border);
        }
        
        .param-item:hover {
            background: var(--light);
            transform: translateY(-2px);
        }
        
        .param-name {
            font-weight: 600;
        }
        
        .param-toggle {
            width: 64px;
            height: 32px;
            background: #444;
            border-radius: 16px;
            position: relative;
            cursor: pointer;
            transition: all 0.3s;
            border: 1px solid var(--border);
        }
        
        .param-toggle.active {
            background: var(--success);
        }
        
        .param-toggle::before {
            content: "0";
            position: absolute;
            left: 10px;
            top: 50%;
            transform: translateY(-50%);
            color: white;
            font-weight: bold;
            font-size: 0.8rem;
            transition: all 0.3s;
        }
        
        .param-toggle.active::before {
            content: "1";
            left: auto;
            right: 10px;
        }
        
        .param-toggle::after {
            content: "";
            position: absolute;
            width: 26px;
            height: 26px;
            background: white;
            border-radius: 50%;
            top: 2px;
            left: 3px;
            transition: transform 0.3s;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }
        
        .param-toggle.active::after {
            transform: translateX(32px);
        }
        
        .mining-info {
            background: var(--accent);
            padding: 1.8rem;
            border-radius: 10px;
            border: 1px solid var(--border);
        }
        
        button {
            background: linear-gradient(135deg, var(--success), #3d8b40);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s;
            width: 100%;
            margin-top: 1.2rem;
            font-family: 'Manrope', sans-serif;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
        
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(0, 0, 0, 0.3);
        }
        
        button:disabled {
            background: #444;
            color: #777;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .blockchain {
            margin-top: 2.5rem;
        }
        
        .blocks-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(360px, 1fr));
            gap: 1.8rem;
        }
        
        .block {
            background: var(--secondary);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.2);
            border-left: 4px solid var(--border);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid var(--border);
        }
        
        .block:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 24px rgba(0, 0, 0, 0.3);
        }
        
        .block.genesis {
            border-left-color: var(--warning);
            background: linear-gradient(135deg, var(--secondary), #2a2a2a);
        }
        
        .block.own-block {
            border-left-color: var(--success);
            background: linear-gradient(135deg, var(--secondary), #1a2a1a);
        }
        
        .block-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1.2rem;
            padding-bottom: 0.7rem;
            border-bottom: 1px solid var(--border);
        }
        
        .block-index {
            font-weight: bold;
            color: var(--text);
            font-size: 1.1rem;
        }
        
        .block-miner {
            font-size: 0.9rem;
            color: var(--text);
            background: var(--accent);
            padding: 0.3rem 0.7rem;
            border-radius: 6px;
            font-weight: 500;
        }
        
        .block-hash {
            font-family: monospace;
            font-size: 0.8rem;
            color: var(--text-secondary);
            word-break: break-all;
            margin-bottom: 0.7rem;
            background: var(--accent);
            padding: 0.7rem;
            border-radius: 6px;
            border: 1px solid var(--border);
        }
        
        .block-data {
            font-size: 0.9rem;
        }
        
        .data-item {
            margin-bottom: 0.7rem;
            display: flex;
            justify-content: space-between;
        }
        
        .data-label {
            font-weight: 600;
            color: var(--text-secondary);
        }
        
        .data-value {
            color: var(--text);
        }
        
        .mined-idc {
            display: inline-block;
            background: var(--success);
            color: white;
            padding: 0.4rem 0.8rem;
            border-radius: 6px;
            font-weight: bold;
        }
        
        .fundamental-code {
            background: linear-gradient(135deg, var(--accent), #2a2a2a);
            border-left: 4px solid var(--warning);
            padding: 1.5rem;
            border-radius: 0 10px 10px 0;
            margin-top: 2.5rem;
            border: 1px solid var(--border);
        }
        
        .code-title {
            font-weight: bold;
            margin-bottom: 0.8rem;
            color: var(--warning);
            font-size: 1.2rem;
        }
        
        .wallet-section {
            background: var(--secondary);
            border-radius: 12px;
            padding: 2rem;
            margin-bottom: 1.8rem;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
            text-align: center;
            border: 1px solid var(--border);
        }
        
        .wallet-balance {
            font-size: 4rem;
            font-weight: bold;
            color: var(--success);
            margin: 1.5rem 0;
            text-shadow: 0 2px 10px rgba(76, 175, 80, 0.3);
        }
        
        .wallet-label {
            font-size: 1.3rem;
            color: var(--text-secondary);
            font-weight: 600;
            letter-spacing: 1px;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 1.2rem 1.8rem;
            border-radius: 10px;
            background: var(--success);
            color: white;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
            transform: translateX(150%);
            transition: transform 0.4s ease;
            z-index: 1000;
            font-weight: 500;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            background: #d32f2f;
        }
        
        .blockchain-stats {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1.5rem;
            padding: 1.5rem;
            background: var(--secondary);
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            border: 1px solid var(--border);
        }
        
        .blockchain-stat {
            text-align: center;
            flex: 1;
        }
        
        .blockchain-stat-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--success);
            margin-bottom: 0.5rem;
        }
        
        .blockchain-stat-label {
            font-size: 0.9rem;
            color: var(--text-secondary);
            font-weight: 500;
        }
        
        .mining-status {
            text-align: center;
            padding: 1.2rem;
            margin-top: 1.5rem;
            border-radius: 8px;
            font-weight: 600;
            border: 1px solid var(--border);
        }
        
        .mining-status.available {
            background: rgba(76, 175, 80, 0.1);
            color: var(--success);
        }
        
        .mining-status.unavailable {
            background: rgba(211, 47, 47, 0.1);
            color: #d32f2f;
        }
        
        .validation-badge {
            display: inline-block;
            padding: 0.3rem 0.7rem;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-left: 0.5rem;
        }
        
        .valid-badge {
            background: var(--success);
            color: white;
        }
        
        .auto-save-status {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--success);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-size: 0.8rem;
            font-weight: 600;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .auto-save-status.show {
            opacity: 1;
        }
        
        @media (max-width: 768px) {
            .mining-form {
                grid-template-columns: 1fr;
            }
            
            .blocks-container {
                grid-template-columns: 1fr;
            }
            
            header {
                flex-direction: column;
                gap: 1.2rem;
            }
            
            .notification {
                top: 10px;
                right: 10px;
                left: 10px;
            }
            
            .blockchain-stats {
                flex-direction: column;
                gap: 1.2rem;
            }
            
            .wallet-balance {
                font-size: 3rem;
            }
            
            .auto-save-status {
                bottom: 10px;
                right: 10px;
                left: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="notification" id="notification"></div>
    <div class="auto-save-status" id="auto-save-status">✅ Автосохранение</div>
    
    <header>
        <div>
            <h1>Ideal Coin Blockchain</h1>
            <p class="subtitle">Автоматическое сохранение всех данных</p>
        </div>
        <div class="user-info" id="user-info" style="display: none;">
            <div class="user-avatar" id="user-avatar">U</div>
            <div>
                <div id="user-nickname">User</div>
                <div class="wallet-info">Баланс: <span id="user-balance">0</span> IDC</div>
            </div>
            <button class="logout-btn" id="logout-btn">Выйти</button>
        </div>
    </header>
    
    <div class="container">
        <!-- Форма авторизации -->
        <div class="auth-container" id="auth-container">
            <div class="auth-form">
                <div class="tabs">
                    <div class="tab active" data-tab="login">Вход</div>
                    <div class="tab" data-tab="register">Регистрация</div>
                </div>
                
                <div class="tab-content active" id="login-tab">
                    <div class="form-group">
                        <label for="login-nickname">Никнейм</label>
                        <input type="text" id="login-nickname" placeholder="Ваш никнейм">
                    </div>
                    <div class="form-group">
                        <label for="login-password">Пароль</label>
                        <input type="password" id="login-password" placeholder="Ваш пароль">
                    </div>
                    <button id="login-btn">Войти</button>
                </div>
                
                <div class="tab-content" id="register-tab">
                    <div class="form-group">
                        <label for="register-nickname">Никнейм</label>
                        <input type="text" id="register-nickname" placeholder="Придумайте никнейм">
                    </div>
                    <div class="form-group">
                        <label for="register-password">Пароль</label>
                        <input type="password" id="register-password" placeholder="Придумайте пароль">
                    </div>
                    <div class="form-group">
                        <label for="register-confirm-password">Подтвердите пароль</label>
                        <input type="password" id="register-confirm-password" placeholder="Повторите пароль">
                    </div>
                    <button id="register-btn">Зарегистрироваться</button>
                </div>
            </div>
        </div>
        
        <!-- Основной контент (виден только после авторизации) -->
        <div id="main-content" style="display: none;">
            <div class="wallet-section">
                <h2 class="card-title">Мой кошелек IDC</h2>
                <div class="wallet-balance" id="wallet-balance">0</div>
                <div class="wallet-label">IDC</div>
            </div>
            
            <div class="card">
                <h2 class="card-title">Майнинг Ideal Coin</h2>
                <div class="mining-form">
                    <div class="mining-params">
                        <div class="param-item">
                            <span class="param-name">Праведность / Этичность</span>
                            <div class="param-toggle" id="param1-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Задача дня</span>
                            <div class="param-toggle" id="param2-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Сон</span>
                            <div class="param-toggle" id="param3-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Здоровое питание</span>
                            <div class="param-toggle" id="param4-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Физ. активность</span>
                            <div class="param-toggle" id="param5-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Без соц. сетей</span>
                            <div class="param-toggle" id="param6-toggle"></div>
                        </div>
                        <div class="param-item">
                            <span class="param-name">Когнитивное развитие</span>
                            <div class="param-toggle" id="param7-toggle"></div>
                        </div>
                    </div>
                    
                    <div class="mining-info">
                        <div id="mining-status" class="mining-status available">
                            ✅ Сегодня вы можете добыть IDC
                        </div>
                        
                        <button id="mine-button">Добыть Ideal Coin</button>
                    </div>
                </div>
            </div>
            
            <div class="fundamental-code">
                <div class="code-title">Fundamental Code of Ideal Coin 2.0 (from 30.09.2025)</div>
                <p>Ideal можно добыть, нельзя купить или продать. Транзакции делать невозможно.</p>
                <p>Добыть Ideal возможно по 7 параметрам за день. Каждый выполненный параметр = 1 IDC.</p>
                <p>Эмиссия в год для одного майнера: 2548 Ideal Coin's.</p>
                <p>Нельзя добыть Ideal, если вовремя его не внести в блокчейн в течение суток.</p>
                <p><strong>В один день можно создать только один блок.</strong></p>
            </div>
            
            <div class="blockchain">
                <h2 class="card-title">Публичный реестр блоков Ideal Coin 
                    <span class="validation-badge valid-badge" id="chain-validation">Цепочка валидна</span>
                </h2>
                
                <div class="blockchain-stats">
                    <div class="blockchain-stat">
                        <div class="blockchain-stat-value" id="total-blocks">0</div>
                        <div class="blockchain-stat-label">Всего блоков</div>
                    </div>
                    <div class="blockchain-stat">
                        <div class="blockchain-stat-value" id="total-miners">0</div>
                        <div class="blockchain-stat-label">Всего майнеров</div>
                    </div>
                    <div class="blockchain-stat">
                        <div class="blockchain-stat-value" id="total-idc-mined">0</div>
                        <div class="blockchain-stat-label">Всего добыто IDC</div>
                    </div>
                </div>
                
                <div class="blocks-container" id="blocks-container">
                    <!-- Блоки будут добавляться здесь -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // === ЖЕСТКО ЗАКРЕПЛЕННЫЙ ГЕНЕЗИС БЛОК ===
        const GENESIS_BLOCK = {
            index: 0,
            timestamp: "2024-01-01T00:00:00.000Z",
            data: {
                message: "Genesis Block of Ideal Coin - Fundamental Code 2.0",
                fundamentalCode: "FC of IDC 2.0 from 30.09.2025",
                idcCount: 0,
                params: [],
                type: "genesis"
            },
            miner: "System",
            previousHash: "0",
            hash: "0000a1b2c3d4e5f67890123456789012345678901234567890123456789012",
            nonce: 12345,
            isValid: true
        };

        // === ПЕРЕМЕННЫЕ ПРОГРАММЫ ===
        let blockchain = [GENESIS_BLOCK];
        let users = {};
        let currentUser = null;
        const DIFFICULTY = 2;

        // === СИСТЕМА АВТОСОХРАНЕНИЯ ===
        function showAutoSaveStatus() {
            const status = document.getElementById('auto-save-status');
            status.classList.add('show');
            setTimeout(() => {
                status.classList.remove('show');
            }, 1000);
        }

        function saveAllData() {
            try {
                // Сохраняем блокчейн
                localStorage.setItem('idealCoinBlockchain', JSON.stringify(blockchain));
                
                // Сохраняем пользователей
                localStorage.setItem('idealCoinUsers', JSON.stringify(users));
                
                // Сохраняем текущего пользователя
                if (currentUser) {
                    localStorage.setItem('currentIdealCoinUser', JSON.stringify(currentUser));
                }
                
                // Показываем статус автосохранения
                showAutoSaveStatus();
                
                console.log('✅ Все данные автоматически сохранены');
            } catch (error) {
                console.error('❌ Ошибка автосохранения:', error);
            }
        }

        function loadAllData() {
            try {
                // Загружаем блокчейн
                const savedBlockchain = localStorage.getItem('idealCoinBlockchain');
                if (savedBlockchain) {
                    const parsedBlockchain = JSON.parse(savedBlockchain);
                    // Проверяем валидность каждого блока
                    blockchain = [GENESIS_BLOCK]; // Всегда начинаем с генезис блока
                    
                    for (let i = 1; i < parsedBlockchain.length; i++) {
                        const block = parsedBlockchain[i];
                        const previousBlock = blockchain[blockchain.length - 1];
                        
                        if (isValidBlock(block, previousBlock)) {
                            blockchain.push(block);
                        }
                    }
                    console.log('✅ Блокчейн загружен:', blockchain.length, 'блоков');
                }

                // Загружаем пользователей
                const savedUsers = localStorage.getItem('idealCoinUsers');
                if (savedUsers) {
                    users = JSON.parse(savedUsers);
                    console.log('✅ Пользователи загружены:', Object.keys(users).length, 'пользователей');
                }

                // Загружаем текущего пользователя
                const savedCurrentUser = localStorage.getItem('currentIdealCoinUser');
                if (savedCurrentUser) {
                    currentUser = JSON.parse(savedCurrentUser);
                    console.log('✅ Текущий пользователь загружен:', currentUser.nickname);
                }

            } catch (error) {
                console.error('❌ Ошибка загрузки данных:', error);
                // В случае ошибки используем данные по умолчанию
                blockchain = [GENESIS_BLOCK];
                users = {};
            }
        }

        // === ОСНОВНЫЕ ФУНКЦИИ БЛОКЧЕЙНА ===
        
        function showNotification(message, isError = false) {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.className = 'notification' + (isError ? ' error' : '');
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        function calculateHash(index, timestamp, data, previousHash, miner, nonce = 0) {
            return CryptoJS.SHA256(index + timestamp + JSON.stringify(data) + previousHash + miner + nonce).toString();
        }
        
        function isValidHash(hash) {
            return hash.substring(0, DIFFICULTY) === '0'.repeat(DIFFICULTY);
        }
        
        function mineBlock(block) {
            let nonce = 0;
            let hash = '';
            
            do {
                nonce++;
                hash = calculateHash(block.index, block.timestamp, block.data, block.previousHash, block.miner, nonce);
            } while (!isValidHash(hash));
            
            return { hash, nonce };
        }
        
        function isValidBlock(block, previousBlock) {
            if (!block.index || !block.timestamp || !block.data || !block.miner || !block.previousHash || !block.hash || block.nonce === undefined) {
                return false;
            }
            
            if (block.index !== previousBlock.index + 1) {
                return false;
            }
            
            if (block.previousHash !== previousBlock.hash) {
                return false;
            }
            
            const calculatedHash = calculateHash(block.index, block.timestamp, block.data, block.previousHash, block.miner, block.nonce);
            if (block.hash !== calculatedHash) {
                return false;
            }
            
            if (!isValidHash(block.hash)) {
                return false;
            }
            
            if (block.index > 0 && block.data.type === "mining") {
                if (!block.data.idcCount || typeof block.data.idcCount !== 'number') {
                    return false;
                }
                if (block.data.idcCount < 0 || block.data.idcCount > 7) {
                    return false;
                }
                if (!Array.isArray(block.data.params)) {
                    return false;
                }
            }
            
            return true;
        }
        
        function createUserRegistrationBlock(nickname) {
            const previousBlock = blockchain[blockchain.length - 1];
            const index = previousBlock.index + 1;
            const timestamp = new Date().toISOString();
            
            const userData = {
                type: "user_registration",
                nickname: nickname,
                registrationDate: timestamp,
                idcCount: 0,
                params: []
            };
            
            const newBlock = {
                index,
                timestamp,
                data: userData,
                miner: "System",
                previousHash: previousBlock.hash,
                nonce: 0,
                isValid: false
            };
            
            const { hash, nonce } = mineBlock(newBlock);
            newBlock.hash = hash;
            newBlock.nonce = nonce;
            newBlock.isValid = true;
            
            return newBlock;
        }
        
        function createMiningBlock(miningData) {
            const previousBlock = blockchain[blockchain.length - 1];
            const index = previousBlock.index + 1;
            const timestamp = new Date().toISOString();
            
            const newBlock = {
                index,
                timestamp,
                data: miningData,
                miner: currentUser.nickname,
                previousHash: previousBlock.hash,
                nonce: 0,
                isValid: false
            };
            
            const { hash, nonce } = mineBlock(newBlock);
            newBlock.hash = hash;
            newBlock.nonce = nonce;
            newBlock.isValid = true;
            
            return newBlock;
        }
        
        function hasUserMinedToday() {
            const today = new Date().toDateString();
            
            for (const block of blockchain) {
                if (block.index === 0) continue;
                if (block.miner !== currentUser.nickname) continue;
                if (block.data.type === "user_registration") continue;
                
                const blockDate = new Date(block.timestamp).toDateString();
                if (blockDate === today) {
                    return true;
                }
            }
            
            return false;
        }
        
        function updateMiningStatus() {
            const miningStatus = document.getElementById('mining-status');
            
            if (hasUserMinedToday()) {
                miningStatus.textContent = "❌ Вы уже добывали IDC сегодня. Новый блок можно создать завтра.";
                miningStatus.className = 'mining-status unavailable';
                document.getElementById('mine-button').disabled = true;
            } else {
                miningStatus.textContent = "✅ Сегодня вы можете добыть IDC";
                miningStatus.className = 'mining-status available';
                document.getElementById('mine-button').disabled = false;
            }
        }
        
        function addBlock(newBlock) {
            const previousBlock = blockchain[blockchain.length - 1];
            
            if (!isValidBlock(newBlock, previousBlock)) {
                showNotification("Ошибка: создан невалидный блок!", true);
                return false;
            }
            
            blockchain.push(newBlock);
            
            // АВТОМАТИЧЕСКОЕ СОХРАНЕНИЕ ВСЕХ ДАННЫХ
            saveAllData();
            
            renderBlockchain();
            updateStats();
            updateMiningStatus();
            return true;
        }
        
        function validateYearlyLimit(newIdc) {
            const currentYear = new Date().getFullYear();
            let yearlyTotal = 0;
            
            for (const block of blockchain) {
                if (block.index === 0) continue;
                if (block.miner !== currentUser.nickname) continue;
                if (block.data.type === "user_registration") continue;
                
                const blockYear = new Date(block.timestamp).getFullYear();
                if (blockYear === currentYear) {
                    yearlyTotal += block.data.idcCount;
                }
            }
            
            return yearlyTotal + newIdc <= 2548;
        }
        
        function updateStats() {
            const totalIdc = calculateTotalIdc();
            
            document.getElementById('wallet-balance').textContent = totalIdc;
            document.getElementById('user-balance').textContent = totalIdc;
            
            const isValid = isChainValid(blockchain);
            const validationBadge = document.getElementById('chain-validation');
            validationBadge.textContent = isValid ? 'Цепочка валидна' : 'Цепочка невалидна';
            validationBadge.className = `validation-badge ${isValid ? 'valid-badge' : 'invalid-badge'}`;
            
            updateBlockchainStats();
        }
        
        function updateBlockchainStats() {
            const validBlocks = blockchain.filter(block => block.isValid && block.index > 0);
            const totalIdcMined = calculateTotalIdcAllUsers();
            const miners = getAllMiners();
            
            document.getElementById('total-blocks').textContent = validBlocks.length;
            document.getElementById('total-miners').textContent = miners.length;
            document.getElementById('total-idc-mined').textContent = totalIdcMined;
        }
        
        function getAllMiners() {
            const miners = new Set();
            
            for (const block of blockchain) {
                if (block.index > 0 && block.isValid && block.data.type !== "user_registration") {
                    miners.add(block.miner);
                }
            }
            
            return Array.from(miners);
        }
        
        function calculateTotalIdcAllUsers() {
            let totalIdc = 0;
            
            for (const block of blockchain) {
                if (block.index > 0 && block.isValid && block.data.type !== "user_registration") {
                    totalIdc += block.data.idcCount;
                }
            }
            
            return totalIdc;
        }
        
        function calculateTotalIdc() {
            let totalIdc = 0;
            
            for (const block of blockchain) {
                if (block.index > 0 && block.miner === currentUser.nickname && block.isValid && block.data.type !== "user_registration") {
                    totalIdc += block.data.idcCount;
                }
            }
            
            return totalIdc;
        }
        
        function renderBlockchain() {
            const container = document.getElementById('blocks-container');
            container.innerHTML = '';
            
            const validBlocks = blockchain.filter(block => block.isValid);
            const reversedBlocks = [...validBlocks].reverse();
            
            reversedBlocks.forEach(block => {
                const blockElement = document.createElement('div');
                blockElement.className = 'block';
                
                if (block.index === 0) {
                    blockElement.classList.add('genesis');
                } else if (block.miner === currentUser.nickname) {
                    blockElement.classList.add('own-block');
                }
                
                let dataHTML = '';
                if (block.index === 0) {
                    dataHTML = `
                        <div class="data-item"><span class="data-label">Сообщение:</span> <span class="data-value">${block.data.message}</span></div>
                        <div class="data-item"><span class="data-label">Fundamental Code:</span> <span class="data-value">${block.data.fundamentalCode}</span></div>
                        <div class="data-item"><span class="data-label">Nonce:</span> <span class="data-value">${block.nonce}</span></div>
                    `;
                } else if (block.data.type === "user_registration") {
                    dataHTML = `
                        <div class="data-item"><span class="data-label">Тип:</span> <span class="data-value">Регистрация пользователя</span></div>
                        <div class="data-item"><span class="data-label">Никнейм:</span> <span class="data-value">${block.data.nickname}</span></div>
                        <div class="data-item"><span class="data-label">Дата регистрации:</span> <span class="data-value">${new Date(block.timestamp).toLocaleDateString()}</span></div>
                        <div class="data-item"><span class="data-label">Nonce:</span> <span class="data-value">${block.nonce}</span></div>
                    `;
                } else {
                    dataHTML = `
                        <div class="data-item"><span class="data-label">Майнер:</span> <span class="data-value">${block.miner}</span></div>
                        <div class="data-item"><span class="data-label">IDC добыто:</span> <span class="data-value"><span class="mined-idc">${block.data.idcCount}</span></span></div>
                        <div class="data-item"><span class="data-label">Nonce:</span> <span class="data-value">${block.nonce}</span></div>
                        <div class="data-item"><span class="data-label">Дата:</span> <span class="data-value">${new Date(block.timestamp).toLocaleDateString()}</span></div>
                    `;
                }
                
                blockElement.innerHTML = `
                    <div class="block-header">
                        <span class="block-index">Блок #${block.index}</span>
                        ${block.index > 0 ? `<span class="block-miner">${block.miner}</span>` : ''}
                    </div>
                    <div class="block-data">
                        ${dataHTML}
                    </div>
                    <div class="block-hash">Хэш: ${block.hash}</div>
                    <div class="block-hash">Пред. хэш: ${block.previousHash}</div>
                `;
                
                container.appendChild(blockElement);
            });
        }
        
        function showAuthForm() {
            document.getElementById('auth-container').style.display = 'flex';
            document.getElementById('main-content').style.display = 'none';
            document.getElementById('user-info').style.display = 'none';
        }
        
        function showMainContent() {
            document.getElementById('auth-container').style.display = 'none';
            document.getElementById('main-content').style.display = 'block';
            document.getElementById('user-info').style.display = 'flex';
            
            document.getElementById('user-nickname').textContent = currentUser.nickname;
            document.getElementById('user-avatar').textContent = currentUser.nickname.charAt(0).toUpperCase();
            
            renderBlockchain();
            updateStats();
            updateMiningStatus();
        }
        
        function registerUser(nickname, password) {
            for (const userKey in users) {
                if (users[userKey].nickname === nickname) {
                    showNotification('Пользователь с таким никнеймом уже зарегистрирован!', true);
                    return false;
                }
            }
            
            const userId = 'user_' + Date.now();
            
            users[userId] = {
                nickname,
                password: CryptoJS.SHA256(password).toString(),
                registrationDate: new Date().toISOString()
            };
            
            // АВТОМАТИЧЕСКОЕ СОХРАНЕНИЕ ВСЕХ ДАННЫХ
            saveAllData();
            
            // Создание блока регистрации в блокчейне
            const registrationBlock = createUserRegistrationBlock(nickname);
            if (addBlock(registrationBlock)) {
                showNotification('Регистрация успешна! Ваш аккаунт записан в блокчейн.');
                return true;
            }
            
            return false;
        }
        
        function loginUser(nickname, password) {
            let userFound = null;
            
            for (const userId in users) {
                if (users[userId].nickname === nickname) {
                    userFound = users[userId];
                    break;
                }
            }
            
            if (!userFound) {
                showNotification('Пользователь с таким никнеймом не найден!', true);
                return false;
            }
            
            if (userFound.password !== CryptoJS.SHA256(password).toString()) {
                showNotification('Неверный пароль!', true);
                return false;
            }
            
            currentUser = {
                nickname: userFound.nickname,
                registrationDate: userFound.registrationDate
            };
            
            // Сохраняем текущего пользователя
            localStorage.setItem('currentIdealCoinUser', JSON.stringify(currentUser));
            
            return true;
        }
        
        function logoutUser() {
            currentUser = null;
            localStorage.removeItem('currentIdealCoinUser');
            showAuthForm();
            showNotification('Вы вышли из системы');
        }
        
        // === ИНИЦИАЛИЗАЦИЯ ===
        document.addEventListener('DOMContentLoaded', function() {
            // Загружаем все данные при запуске
            loadAllData();
            
            // Проверяем авторизацию
            if (currentUser) {
                showMainContent();
            } else {
                showAuthForm();
            }
            
            // Обработчики вкладок
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                    document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                    
                    this.classList.add('active');
                    document.getElementById(`${this.dataset.tab}-tab`).classList.add('active');
                });
            });
            
            // Обработчики переключателей
            document.querySelectorAll('.param-toggle').forEach((toggle, index) => {
                toggle.addEventListener('click', function() {
                    this.classList.toggle('active');
                });
            });
            
            // Регистрация
            document.getElementById('register-btn').addEventListener('click', function() {
                const nickname = document.getElementById('register-nickname').value.trim();
                const password = document.getElementById('register-password').value;
                const confirmPassword = document.getElementById('register-confirm-password').value;
                
                if (!nickname || !password) {
                    showNotification('Заполните все поля!', true);
                    return;
                }
                
                if (nickname.length < 3) {
                    showNotification('Никнейм должен содержать не менее 3 символов!', true);
                    return;
                }
                
                if (password.length < 4) {
                    showNotification('Пароль должен содержать не менее 4 символов!', true);
                    return;
                }
                
                if (password !== confirmPassword) {
                    showNotification('Пароли не совпадают!', true);
                    return;
                }
                
                if (registerUser(nickname, password)) {
                    document.querySelector('.tab[data-tab="login"]').click();
                    document.getElementById('login-nickname').value = nickname;
                    document.getElementById('register-nickname').value = '';
                    document.getElementById('register-password').value = '';
                    document.getElementById('register-confirm-password').value = '';
                }
            });
            
            // Вход
            document.getElementById('login-btn').addEventListener('click', function() {
                const nickname = document.getElementById('login-nickname').value.trim();
                const password = document.getElementById('login-password').value;
                
                if (!nickname || !password) {
                    showNotification('Заполните все поля!', true);
                    return;
                }
                
                if (loginUser(nickname, password)) {
                    showMainContent();
                    showNotification(`Добро пожаловать, ${nickname}!`);
                    document.getElementById('login-nickname').value = '';
                    document.getElementById('login-password').value = '';
                }
            });
            
            // Выход
            document.getElementById('logout-btn').addEventListener('click', logoutUser);
            
            // Майнинг
            document.getElementById('mine-button').addEventListener('click', function() {
                const params = [
                    document.getElementById('param1-toggle').classList.contains('active'),
                    document.getElementById('param2-toggle').classList.contains('active'),
                    document.getElementById('param3-toggle').classList.contains('active'),
                    document.getElementById('param4-toggle').classList.contains('active'),
                    document.getElementById('param5-toggle').classList.contains('active'),
                    document.getElementById('param6-toggle').classList.contains('active'),
                    document.getElementById('param7-toggle').classList.contains('active')
                ];
                
                const idcCount = params.filter(Boolean).length;
                
                if (idcCount === 0) {
                    showNotification("Выберите хотя бы один параметр для майнинга!", true);
                    return;
                }
                
                if (!validateYearlyLimit(idcCount)) {
                    showNotification("Превышен годовой лимит майнинга!", true);
                    return;
                }
                
                const miningData = {
                    idcCount,
                    date: "today",
                    params: params,
                    type: "mining"
                };
                
                const newBlock = createMiningBlock(miningData);
                if (addBlock(newBlock)) {
                    showNotification(`Успешно добыто ${idcCount} IDC!`);
                    
                    document.querySelectorAll('.param-toggle').forEach(toggle => {
                        toggle.classList.remove('active');
                    });
                }
            });
        });

        // Вспомогательная функция для проверки цепочки
        function isChainValid(chain) {
            for (let i = 1; i < chain.length; i++) {
                const currentBlock = chain[i];
                const previousBlock = chain[i - 1];
                
                if (currentBlock.previousHash !== previousBlock.hash) {
                    return false;
                }
                
                const calculatedHash = calculateHash(
                    currentBlock.index,
                    currentBlock.timestamp,
                    currentBlock.data,
                    currentBlock.previousHash,
                    currentBlock.miner,
                    currentBlock.nonce
                );
                
                if (currentBlock.hash !== calculatedHash) {
                    return false;
                }
            }
            return true;
        }
    </script>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
</body>
</html>
