<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Metode Numerik • Futuristik (Biru Neon)</title>

<style>
    /* --- KONTEN ASLI TETAP, TIDAK DIUBAH --- */

    #home p { text-align: justify; text-justify: inter-word; }
    .author-card {
        display: flex;
        align-items: center;
        gap: 20px;
        background: #1e1e1e;
        padding: 20px;
        border-radius: 14px;
        margin-bottom: 20px;
        border: 1px solid #333;
    }
    .author-photo {
        width: 80px; height: 80px;
        border-radius: 12px;
        object-fit: cover;
        border: 2px solid #444;
    }
    .author-info h3 { margin:0;font-size:20px;color:#fff; }
    .author-info p { margin:2px 0;color:#ccc;font-size:15px; }

    :root{
        --bg-1: #071028;
        --bg-2: #0b1a3a;
        --card: rgba(8,12,28,0.72);
        --accent: #6ea8ff;
        --accent-2: #9cc2ff;
        --muted: #cfe6ff;
        --text: #e9f4ff;
        --pre-bg-dark: #071427;
        --pre-border-dark: rgba(110,168,255,0.12);
    }

    html,body{
        height:100%; margin:0; padding:0;
        background: radial-gradient(circle at 10% 10%, #071230 0%, var(--bg-1) 25%, var(--bg-2) 100%);
        font-family: "Inter","Segoe UI",Roboto,Arial,sans-serif;
        color: var(--text);
    }

    a { color: var(--accent-2); text-decoration: none; }
    a:hover { text-decoration: underline; }

    .navbar{
        position:sticky; top:0; z-index:50;
        display:flex; align-items:center; justify-content:space-between;
        gap:20px; padding:16px 28px;
        background: linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.00));
        border-bottom:1px solid rgba(110,168,255,0.06);
        backdrop-filter: blur(8px) saturate(120%);
        box-shadow:0 6px 30px rgba(3,10,25,0.6);
    }

    .logo{
        display:flex; align-items:center; gap:12px;
        font-weight:700; color:var(--accent-2); font-size:20px;
    }
    .logo .dot{
        width:10px; height:10px; border-radius:50%;
        background: linear-gradient(90deg,var(--accent),#bfe7ff);
        box-shadow:0 0 12px rgba(110,168,255,0.9);
    }

    .nav-right{ display:flex; gap:26px; font-weight:600; }
    .nav-right a{
        color:var(--muted); font-size:16px;
        transition:.18s ease; padding:8px 10px; border-radius:8px;
    }
    .nav-right a:hover{
        color:white;
        background: linear-gradient(90deg,rgba(110,168,255,0.06),rgba(110,168,255,0.03));
        transform: translateY(-2px);
    }

    .main-wrap{
        width:94%; max-width:1100px;
        margin:36px auto 80px; padding:0 12px;
    }

    .section{ display:none; margin-bottom:34px; }
    .section.active{ display:block; animation: fadeUp .45s ease both; }

    @keyframes fadeUp {
        from { opacity:0; transform: translateY(8px); }
        to   { opacity:1; transform: translateY(0); }
    }

    .card{
        background:var(--card);
        border-radius:14px;
        padding:28px;
        border:1px solid rgba(110,168,255,0.06);
        box-shadow:0 10px 30px rgba(5,10,25,0.5);
        backdrop-filter: blur(8px) saturate(120%);
    }

    h2{ margin:0 0 12px 0; font-size:28px; color:var(--accent-2); }
    h3{ margin-top:18px; color:var(--accent); font-size:18px; }

    p, li{ font-size:16px; line-height:1.7; }

    pre{
        background:var(--pre-bg-dark)!important;
        color:#dff6ff!important;
        padding:14px 16px!important;
        border-radius:10px!important;
        border:1px solid var(--pre-border-dark)!important;
        font-size:14px;
        white-space:pre-wrap!important;
    }

    /* =====================================================
       ========== WIDGET CHATBOT (FUTURISTIK) ==============
       ===================================================== */
    #chatbot-button {
        position: fixed;
        bottom: 26px;
        right: 26px;
        background: var(--accent);
        color: #000;
        font-weight: 700;
        padding: 14px 20px;
        border-radius: 14px;
        cursor: pointer;
        box-shadow: 0 6px 24px rgba(110,168,255,0.4);
        border: none;
    }

    #chatbot-window {
        position: fixed;
        bottom: 90px;
        right: 26px;
        width: 320px;
        height: 420px;
        background: #0f1629;
        border-radius: 18px;
        border: 1px solid rgba(110,168,255,0.2);
        display: none;
        flex-direction: column;
        overflow: hidden;
        box-shadow: 0 10px 40px rgba(30,70,140,0.5);
    }

    #chat-header {
        padding: 14px;
        background: #111b3c;
        font-weight:700;
        color: var(--accent-2);
        text-align:center;
        border-bottom:1px solid rgba(110,168,255,0.15);
    }

    #chat-body {
        flex:1; padding:10px; overflow-y:auto;
        font-size:14px; line-height:1.5;
    }

    .bot-msg{
        background:#13234a;
        padding:10px; border-radius:10px;
        margin-bottom:10px; width: fit-content;
        max-width:90%;
    }

    .user-msg{
        background:#1b355c;
        padding:10px; border-radius:10px;
        margin-bottom:10px; width: fit-content;
        margin-left:auto; max-width:90%;
    }

    #chat-input-wrap {
        display:flex; border-top:1px solid rgba(110,168,255,0.15);
    }

    #chat-input {
        flex:1; padding:10px; border:none;
        background:#0d1428; color:white;
    }

    #send-btn {
        padding:10px 14px;
        background: var(--accent);
        border:none; cursor:pointer;
        font-weight:700;
        border-left:1px solid rgba(110,168,255,0.25);
    }
</style>

<script>
function tampilkan(id){
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    window.scrollTo({ top: 0, behavior:'smooth' });
}
window.addEventListener('DOMContentLoaded', () => tampilkan('home'));


// ==========================
// WIDGET CHATBOT SEDERHANA
// ==========================
function botReply(text){
    const body = document.getElementById("chat-body");
    const div = document.createElement("div");
    div.className = "bot-msg";
    div.innerText = text;
    body.appendChild(div);
    body.scrollTop = body.scrollHeight;
}

function userReply(text){
    const body = document.getElementById("chat-body");
    const div = document.createElement("div");
    div.className = "user-msg";
    div.innerText = text;
    body.appendChild(div);
    body.scrollTop = body.scrollHeight;
}

function sendMessage(){
    const input = document.getElementById("chat-input");
    const msg = input.value.trim();
    if(!msg) return;
    userReply(msg);
    input.value = "";

    // Jawaban bot (versi simple)
    setTimeout(() => {
        botReply("Untuk saat ini chatbot masih versi demo sederhana. Saya bisa bantu menjelaskan materi metode numerik seperti interpolasi, beda bagi, Newton, dll. 😊");
    }, 400);
}

function toggleChat(){
    const win = document.getElementById("chatbot-window");
    win.style.display = (win.style.display === "flex") ? "none" : "flex";
}
</script>
</head>

<body>

<!-- NAVBAR -->
<div class="navbar">
    <div class="logo"><div class="dot"></div>Metode Numerik</div>
    <div class="nav-right">
        <a href="#" onclick="tampilkan('home');return false;">Home</a>
        <a href="#" onclick="tampilkan('materi');return false;">Materi</a>
        <a href="#" onclick="tampilkan('penulis');return false;">Tentang Penulis</a>
    </div>
</div>

<!-- MAIN -->
<main class="main-wrap">

<!-- HOME -->
<section id="home" class="section card">
    <h2>Selamat Datang</h2>
    <p>
        (ISI PERSIS SEPERTI YANG KAMU KIRIM — TIDAK DIUBAH)
    </p>
</section>

<!-- MATERI -->
<div id="materi" class="container section card">
    <h2>Interpolasi Beda Bagi Newton</h2>
    (ISI MATERI PERSIS SAMA — TIDAK DIUBAH)
</div>

<!-- PENULIS -->
<div id="penulis" class="container section card">
    <h2>Tentang Penulis</h2>
    (ISI PENULIS SAMA — TIDAK DIUBAH)
</div>

</main>

<!-- CHATBOT FLOATING -->
<button id="chatbot-button" onclick="toggleChat()">Chatbot</button>

<div id="chatbot-window">
    <div id="chat-header">Asisten Belajar</div>
    <div id="chat-body">
        <div class="bot-msg">Halo! Ada yang ingin ditanyakan tentang metode numerik? 😊</div>
    </div>
    <div id="chat-input-wrap">
        <input id="chat-input" placeholder="Ketik pesan..." onkeydown="if(event.key==='Enter') sendMessage()">
        <button id="send-btn" onclick="sendMessage()">➤</button>
    </div>
</div>

</body>
</html>
