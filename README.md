<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Сільський Шаолінь — Chat Roulette</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background: #090b10;
    color: #fff;
    min-height: 100vh;
}

button, select {
    font: inherit;
}

.app {
    max-width: 520px;
    margin: auto;
    min-height: 100vh;
    background: #11151d;
}

/* HEADER */

.header {
    padding: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #292f3a;
    position: sticky;
    top: 0;
    background: #11151d;
    z-index: 10;
}

.logo {
    font-size: 18px;
    font-weight: bold;
}

.logo span {
    display: block;
    font-size: 11px;
    color: #9da7b5;
    margin-top: 3px;
}

.coin {
    background: #242b36;
    border-radius: 20px;
    padding: 8px 12px;
    font-size: 13px;
}

/* SCREENS */

.screen {
    display: none;
    padding: 20px;
    padding-bottom: 90px;
}

.screen.active {
    display: block;
}

/* HOME */

.hero {
    text-align: center;
    padding: 35px 10px;
}

.hero .emoji {
    font-size: 60px;
    margin-bottom: 15px;
}

.hero h1 {
    font-size: 29px;
    margin-bottom: 8px;
}

.hero p {
    color: #aab2bf;
    line-height: 1.5;
}

.main-button {
    width: 100%;
    border: 0;
    border-radius: 15px;
    padding: 17px;
    background: #e4a52b;
    color: #111;
    font-weight: bold;
    font-size: 17px;
    cursor: pointer;
    margin-top: 20px;
}

.main-button:active {
    transform: scale(.98);
}

.cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-top: 25px;
}

.card {
    background: #191f28;
    border: 1px solid #29313d;
    border-radius: 15px;
    padding: 18px 12px;
    text-align: center;
}

.card .big {
    font-size: 28px;
    margin-bottom: 8px;
}

.card small {
    color: #aab2bf;
}

/* FILTERS */

.title {
    font-size: 23px;
    margin-bottom: 8px;
}

.subtitle {
    color: #9da7b5;
    margin-bottom: 20px;
}

.section {
    margin-bottom: 22px;
}

.section-title {
    font-size: 14px;
    color: #9da7b5;
    margin-bottom: 10px;
}

.options {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
}

.option {
    background: #1b212b;
    border: 1px solid #303846;
    color: white;
    padding: 10px 13px;
    border-radius: 12px;
    cursor: pointer;
}

.option.selected {
    background: #e4a52b;
    color: #111;
    border-color: #e4a52b;
    font-weight: bold;
}

/* ROULETTE */

.video {
    height: 300px;
    border-radius: 18px;
    background: #050607;
    border: 1px solid #303642;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    margin-bottom: 15px;
}

.video-avatar {
    font-size: 70px;
}

.video-text {
    color: #9da7b5;
    margin-top: 8px;
}

.controls {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
    margin-bottom: 15px;
}

.control {
    background: #202631;
    border: 1px solid #303846;
    color: white;
    padding: 12px 5px;
    border-radius: 12px;
    cursor: pointer;
    font-size: 12px;
}

.control.next {
    background: #e4a52b;
    color: #111;
}

/* AI */

.ai-panel {
    background: #171d26;
    border: 1px solid #343c49;
    border-radius: 18px;
    padding: 16px;
}

.ai-title {
    display: flex;
    justify-content: space-between;
    margin-bottom: 15px;
}

.ai-title strong {
    font-size: 16px;
}

.ai-online {
    color: #71d49b;
    font-size: 12px;
}

.stats {
    display: grid;
    gap: 10px;
}

.stat {
    display: flex;
    justify-content: space-between;
    color: #b8c0cc;
    font-size: 13px;
}

.bar {
    height: 6px;
    background: #303744;
    border-radius: 5px;
    overflow: hidden;
    margin-top: 5px;
}

.bar div {
    height: 100%;
    width: 70%;
    background: #e4a52b;
}

.suggestion {
    margin-top: 16px;
    background: #202732;
    border-radius: 12px;
    padding: 13px;
}

.suggestion p {
    color: #aeb7c4;
    font-size: 12px;
    margin-bottom: 8px;
}

.say {
    width: 100%;
    border: 1px solid #3b4554;
    background: #181e27;
    color: white;
    padding: 10px;
    border-radius: 10px;
    text-align: left;
    margin-top: 7px;
    cursor: pointer;
}

/* WALLET */

.balance {
    text-align: center;
    background: #191f28;
    border-radius: 18px;
    padding: 25px;
    margin: 20px 0;
}

.balance-number {
    font-size: 35px;
    font-weight: bold;
    margin: 8px 0;
}

.wallet-actions {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}

.wallet-button {
    background: #242b36;
    border: 1px solid #343d4b;
    color: white;
    padding: 13px;
    border-radius: 12px;
}

.transaction {
    display: flex;
    justify-content: space-between;
    padding: 14px 0;
    border-bottom: 1px solid #292f38;
}

.plus {
    color: #71d49b;
}

.minus {
    color: #ed7777;
}

/* PROFILE */

.profile-box {
    text-align: center;
    background: #191f28;
    padding: 25px;
    border-radius: 18px;
}

.profile-avatar {
    font-size: 60px;
}

.profile-name {
    font-size: 22px;
    margin: 10px;
}

.setting {
    margin-top: 12px;
    background: #1c222c;
    padding: 15px;
    border-radius: 12px;
}

/* NAV */

.nav {
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: min(520px, 100%);
    background: #11151d;
    border-top: 1px solid #292f3a;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    padding: 8px 5px;
    z-index: 20;
}

.nav button {
    background: none;
    border: 0;
    color: #8f99a7;
    padding: 7px 2px;
    font-size: 11px;
    cursor: pointer;
}

.nav button.active {
    color: #e4a52b;
}

.nav-icon {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
}

/* MODAL */

.modal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,.75);
    z-index: 50;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

.modal.show {
    display: flex;
}

.modal-box {
    background: #181e27;
    border: 1px solid #343d4b;
    border-radius: 18px;
    padding: 22px;
    width: 100%;
    max-width: 420px;
}

.modal-box h2 {
    margin-bottom: 10px;
}

.modal-box p {
    color: #aeb7c4;
    line-height: 1.5;
    margin-bottom: 15px;
}

.close {
    width: 100%;
    padding: 13px;
    border: 0;
    border-radius: 12px;
    background: #e4a52b;
    color: #111;
    font-weight: bold;
}

/* DESKTOP */

@media (min-width: 800px) {
    body {
        padding: 20px;
    }

    .app {
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 10px 50px rgba(0,0,0,.4);
    }
}
</style>
</head>

<body>

<div class="app">

<header class="header">
    <div class="logo">
        🥷 СІЛЬСЬКИЙ ШАОЛІН
        <span>CHAT ROULETTE</span>
    </div>

    <div class="coin">
        🪙 <span id="coinBalance">250</span>
    </div>
</header>


<!-- HOME -->

<section id="home" class="screen active">

    <div class="hero">

        <div class="emoji">🥷</div>

        <h1>Chat Roulette</h1>

        <p>
            Знайди випадкового співрозмовника
            з будь-якої точки світу.
        </p>

        <button class="main-button" onclick="showScreen('search')">
            🎲 ЗНАЙТИ СПІВРОЗМОВНИКА
        </button>

    </div>

    <div class="cards">

        <div class="card">
            <div class="big">🌍</div>
            <small>Міжнародне спілкування</small>
        </div>

        <div class="card">
            <div class="big">🧠</div>
            <small>AI-суфлер</small>
        </div>

        <div class="card">
            <div class="big">🌐</div>
            <small>Перекладач</small>
        </div>

        <div class="card">
            <div class="big">🪙</div>
            <small>SHAOLIN COIN</small>
        </div>

    </div>

</section>


<!-- SEARCH -->

<section id="search" class="screen">

    <h2 class="title">Кого шукаємо?</h2>

    <p class="subtitle">
        Налаштуй параметри співрозмовника.
    </p>

    <div class="section">

        <div class="section-title">Стать</div>

        <div class="options">

            <button class="option selected" onclick="selectOption(this)">
                👤 Без різниці
            </button>

            <button class="option" onclick="selectOption(this)">
                👨 Чоловік
            </button>

            <button class="option" onclick="selectOption(this)">
                👩 Жінка
            </button>

        </div>

    </div>


    <div class="section">

        <div class="section-title">Мова</div>

        <div class="options">

            <button class="option selected" onclick="selectOption(this)">
                🌍 Будь-яка
            </button>

            <button class="option" onclick="selectOption(this)">
                🇺🇦 Українська
            </button>

            <button class="option" onclick="selectOption(this)">
                🇬🇧 English
            </button>

            <button class="option" onclick="selectOption(this)">
                🇩🇪 Deutsch
            </button>

            <button class="option" onclick="selectOption(this)">
                🇵🇱 Polski
            </button>

            <button class="option" onclick="selectOption(this)">
                🇪🇸 Español
            </button>

        </div>

    </div>


    <div class="section">

        <div class="section-title">Вік</div>

        <div class="options">

            <button class="option selected" onclick="selectOption(this)">
                Без різниці
            </button>

            <button class="option" onclick="selectOption(this)">
                18–25
            </button>

            <button class="option" onclick="selectOption(this)">
                26–35
            </button>

            <button class="option" onclick="selectOption(this)">
                36–45
            </button>

            <button class="option" onclick="selectOption(this)">
                46+
            </button>

        </div>

    </div>


    <div class="section">

        <div class="section-title">Мета</div>

        <div class="options">

            <button class="option selected" onclick="selectOption(this)">
                💬 Спілкування
            </button>

            <button class="option" onclick="selectOption(this)">
                🌍 Мови
            </button>

            <button class="option" onclick="selectOption(this)">
                ❤️ Знайомства
            </button>

            <button class="option" onclick="selectOption(this)">
                🧠 Тренування
            </button>

        </div>

    </div>


    <button class="main-button" onclick="startRoulette()">
        🔎 ПОЧАТИ ПОШУК
    </button>

</section>


<!-- ROULETTE -->

<section id="roulette" class="screen">

    <div class="video">

        <div>

            <div class="video-avatar" id="avatar">
                👤
            </div>

            <div id="connectionText" class="video-text">
                Очікування співрозмовника...
            </div>

        </div>

    </div>


    <div class="controls">

        <button class="control" onclick="toggleMic()">
            🎤 Мікрофон
        </button>

        <button class="control" onclick="toggleCamera()">
            📹 Камера
        </button>

        <button class="control" onclick="openTranslate()">
            🌐 Переклад
        </button>

        <button class="control next" onclick="nextPerson()">
            🔄 Далі
        </button>

    </div>


    <div class="ai-panel">

        <div class="ai-title">

            <strong>🧠 AI-СУФЛЕР</strong>

            <span class="ai-online">
                ● ONLINE
            </span>

        </div>


        <div class="stats">

            <div>

                <div class="stat">
                    <span>🙂 Настрій</span>
                    <span>позитивний</span>
                </div>

                <div class="bar">
                    <div style="width:78%"></div>
                </div>

            </div>


            <div>

                <div class="stat">
                    <span>🗣️ Відкритість</span>
                    <span>висока</span>
                </div>

                <div class="bar">
                    <div style="width:82%"></div>
                </div>

            </div>


            <div>

                <div class="stat">
                    <span>🎯 Інтерес</span>
                    <span>82%</span>
                </div>

                <div class="bar">
                    <div style="width:82%"></div>
                </div>

            </div>

        </div>


        <div class="suggestion">

            <p>💡 ШІ пропонує запитати:</p>

            <button class="say" onclick="saySuggestion(this)">
                «А ким ти працюєш?»
            </button>

            <button class="say" onclick="saySuggestion(this)">
                «А як ти взагалі прийшов до цього?»
            </button>

            <button class="say" onclick="saySuggestion(this)">
                😂 Пожартувати
            </button>

        </div>

    </div>

</section>


<!-- WALLET -->

<section id="wallet" class="screen">

    <h2 class="title">🪙 SHAOLIN WALLET</h2>

    <p class="subtitle">
        Твоя внутрішня економіка Шаоліню.
    </p>


    <div class="balance">

        <div>Поточний баланс</div>

        <div class="balance-number">
            <span id="walletBalance">250</span>
        </div>

        <div>SHAOLIN COIN</div>

    </div>


    <div class="wallet-actions">

        <button class="wallet-button">
            ➕ Отримати
        </button>

        <button class="wallet-button">
            ➖ Відправити
        </button>

    </div>


    <h3 style="margin-top:25px;margin-bottom:10px">
        Історія
    </h3>


    <div class="transaction">

        <span>🎲 Вхід у рулетку</span>
        <span class="plus">+10</span>

    </div>

    <div class="transaction">

        <span>🧠 AI-тренування</span>
        <span class="plus">+25</span>

    </div>

    <div class="transaction">

        <span>🌐 Перекладач</span>
        <span class="minus">-5</span>

    </div>

</section>


<!-- PROFILE -->

<section id="profile" class="screen">

    <h2 class="title">👤 Мій профіль</h2>

    <div class="profile-box">

        <div class="profile-avatar">
            🥷
        </div>

        <div class="profile-name">
            Гість Шаоліню
        </div>

        <p style="color:#9da7b5">
            Рівень 1 · Початківець
        </p>

    </div>


    <div class="setting">
        🌍 Моя мова: <b>Українська</b>
    </div>

    <div class="setting">
        🧠 AI-суфлер: <b>Увімкнений</b>
    </div>

    <div class="setting">
        🌐 Автопереклад: <b>Увімкнений</b>
    </div>

    <div class="setting">
        🛡️ Безпека та блокування
    </div>

</section>


<!-- NAVIGATION -->

<nav class="nav">

    <button class="active" onclick="showScreen('home',this)">
        <span class="nav-icon">🏠</span>
        Головна
    </button>

    <button onclick="showScreen('search',this)">
        <span class="nav-icon">🎲</span>
        Рулетка
    </button>

    <button onclick="showScreen('wallet',this)">
        <span class="nav-icon">🪙</span>
        Wallet
    </button>

    <button onclick="showScreen('profile',this)">
        <span class="nav-icon">👤</span>
        Профіль
    </button>

</nav>

</div>


<!-- MODAL -->

<div id="modal" class="modal">

    <div class="modal-box">

        <h2 id="modalTitle">
            🌐 Перекладач
        </h2>

        <p id="modalText">
            Тут буде автоматичний переклад
            голосу співрозмовника в реальному часі.
        </p>

        <button class="close" onclick="closeModal()">
            Зрозуміло
        </button>

    </div>

</div>


<script>

let coins = 250;

function showScreen(id, button) {

    document.querySelectorAll('.screen')
        .forEach(s => s.classList.remove('active'));

    document.getElementById(id)
        .classList.add('active');

    document.querySelectorAll('.nav button')
        .forEach(b => b.classList.remove('active'));

    if(button) {
        button.classList.add('active');
    }

    window.scrollTo(0,0);
}


function selectOption(button) {

    const parent = button.parentElement;

    parent.querySelectorAll('.option')
        .forEach(b => b.classList.remove('selected'));

    button.classList.add('selected');
}


function startRoulette() {

    showScreen('roulette');

    document.getElementById('connectionText')
        .innerText = '🔎 Шукаємо співрозмовника...';

    setTimeout(() => {

        document.getElementById('connectionText')
            .innerText = '🟢 Співрозмовника знайдено';

        document.getElementById('avatar')
            .innerText = '🙂';

    }, 1800);

}


function nextPerson() {

    document.getElementById('connectionText')
        .innerText = '🔄 Пошук нового співрозмовника...';

    document.getElementById('avatar')
        .innerText = '👤';

    setTimeout(() => {

        document.getElementById('connectionText')
            .innerText = '🟢 Нового співрозмовника знайдено';

        document.getElementById('avatar')
            .innerText = '😎';

    }, 1300);

}


function toggleMic() {

    alert('🎤 Мікрофон буде підключено через WebRTC.');

}


function toggleCamera() {

    alert('📹 Камера буде підключена через WebRTC.');

}


function openTranslate() {

    document.getElementById('modalTitle')
        .innerText = '🌐 AI-перекладач';

    document.getElementById('modalText')
        .innerText =
        'ШІ автоматично розпізнаватиме твою мову, перекладатиме її мовою співрозмовника та показуватиме переклад його відповіді.';

    document.getElementById('modal')
        .classList.add('show');

}


function closeModal() {

    document.getElementById('modal')
        .classList.remove('show');

}


function saySuggestion(button) {

    button.style.borderColor = '#e4a52b';

    setTimeout(() => {
        button.style.borderColor = '#3b4554';
    }, 700);

}


function toggleCoin(amount) {

    coins += amount;

    document.getElementById('coinBalance')
        .innerText = coins;

    document.getElementById('walletBalance')
        .innerText = coins;

}

</script>

</body>
</html>
