<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<title>Бібліотека презентацій</title>

<style>
:root {
    --bg: url('https://images.unsplash.com/photo-1522383225653-ed111181a951?q=80&w=1920');
    --card: rgba(255,255,255,0.85);
    --text: #222;
    --accent: #bde0fe;
}

/* DARK MODE */
body.dark {
    --card: rgba(20,20,20,0.85);
    --text: #eee;
    --accent: #6c9bcf;
}

/* THEMES */
body.theme-green {
    --bg: url('https://images.unsplash.com/photo-1501004318641-b39e6451bec6?q=80&w=1920');
}

body.theme-blue {
    --bg: url('https://images.unsplash.com/photo-1503264116251-35a269479413?q=80&w=1920');
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    color: var(--text);
    background: var(--bg) no-repeat center center/cover;
    transition: 0.3s;
}

.overlay {
    background: rgba(255,255,255,0.75);
    min-height: 100vh;
}

/* HEADER */
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 40px;
    background: rgba(255,255,255,0.6);
    backdrop-filter: blur(6px);
}

.title {
    font-size: 20px;
    font-weight: bold;
}

.nav {
    display: flex;
    gap: 10px;
}

.nav a, .nav button {
    padding: 8px 12px;
    border-radius: 10px;
    border: none;
    cursor: pointer;
    text-decoration: none;
    background: #d8f3dc;
    color: #222;
}

/* SETTINGS */
.settings {
    display: none;
    position: fixed;
    right: 20px;
    top: 80px;
    background: var(--card);
    padding: 15px;
    border-radius: 12px;
    width: 220px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.2);
}

.settings h4 {
    margin-top: 0;
}

.settings button {
    width: 100%;
    margin-top: 8px;
}

/* LIBRARY */
.library {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 60px;
    gap: 30px;
}

/* CATEGORY */
.category {
    width: 100%;
    max-width: 900px;
}

.category h2 {
    margin-bottom: 10px;
}

/* CARD */
.card {
    width: 100%;
    background: var(--card);
    border-radius: 15px;
    padding: 15px;
    margin-bottom: 15px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.15);
}

/* BUTTON */
.open-btn {
    display: inline-block;
    margin-top: 10px;
    padding: 10px 14px;
    background: var(--accent);
    border-radius: 10px;
    text-decoration: none;
    color: #000;
}

/* FOOTER */
footer {
    text-align: center;
    padding: 20px;
    font-size: 13px;
    opacity: 0.7;
}
</style>
</head>

<body>

<div class="overlay">

<header>
    <div class="title">Бібліотека презентацій Боднара Владислава</div>

    <div class="nav">
        <a href="#">Головна</a>
        <button onclick="toggleSettings()">Налаштування</button>
        <a href="http://nvk2.km.ua/" target="_blank">Навчальний заклад</a>
    </div>
</header>

<!-- SETTINGS -->
<div class="settings" id="settings">
    <h4>Налаштування</h4>

    <button onclick="setTheme('default')">Світла тема</button>
    <button onclick="document.body.classList.toggle('dark')">Темний режим</button>

    <button onclick="setTheme('theme-green')">Зелений фон</button>
    <button onclick="setTheme('theme-blue')">Синій фон</button>
</div>

<section class="library">

    <!-- ХІМІЯ -->
    <div class="category">
        <h2>Хімія</h2>

        <div class="card">
            <h3>Друге життя паперу</h3>
            <p>Переробка паперу та екологічне використання ресурсів</p>

            <a class="open-btn"
               href="https://gamma.app/docs/-9z5jzmrp4b9sc3k"
               target="_blank">
               Відкрити презентацію
            </a>
        </div>
    </div>

    <!-- БІОЛОГІЯ -->
    <div class="category">
        <h2>Біологія</h2>

        <div class="card">
            <h3>Людина проти природи</h3>
            <p>Вплив людини на екосистеми та техногенний тиск</p>

            <a class="open-btn"
               href="https://gamma.app/docs/-1k3g4el9wthjyyn"
               target="_blank">
               Відкрити презентацію
            </a>
        </div>
    </div>

</section>

<footer>
    © 2026 Навчальний проєкт
</footer>

</div>

<script>
function toggleSettings() {
    const s = document.getElementById("settings");
    s.style.display = (s.style.display === "block") ? "none" : "block";
}

function setTheme(theme) {
    document.body.className = document.body.className.replace(/theme-\w+/g, '');
    if(theme !== 'default') {
        document.body.classList.add(theme);
    }
    localStorage.setItem("theme", theme);
}

window.onload = function() {
    const saved = localStorage.getItem("theme");
    if(saved && saved !== "default") {
        document.body.classList.add(saved);
    }
}
</script>

</body>
</html>
