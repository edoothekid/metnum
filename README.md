<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Metode Numerik • Futuristik (Biru Neon)</title>

<style>
    body {
        margin: 0;
        font-family: 'Segoe UI', sans-serif;
        background: radial-gradient(circle at top, #0a0f24, #000);
        color: #d9e3ff;
        overflow-x: hidden;
    }
    a { color: #00aaff; text-decoration: none; }

    /* NAVBAR */
    .navbar {
        position: fixed;
        top: 0;
        width: 100%;
        backdrop-filter: blur(10px);
        background: rgba(0,0,20,0.45);
        padding: 14px 30px;
        border-bottom: 1px solid rgba(0, 132, 255, 0.25);
        display: flex;
        justify-content: space-between;
        align-items: center;
        z-index: 9990;
    }
    .logo {
        display: flex;
        align-items: center;
        font-weight: 600;
        font-size: 18px;
        color: #9bd6ff;
    }
    .dot {
        width: 10px;
        height: 10px;
        background: #00aaff;
        border-radius: 50%;
        margin-right: 10px;
        box-shadow: 0 0 10px #00aaff;
    }
    .nav-right a {
        margin-left: 18px;
        font-weight: 500;
        transition: 0.2s;
    }
    .nav-right a:hover {
        color: #4acdff;
        text-shadow: 0 0 10px #00aaff;
    }

    /* WRAPPER */
    .main-wrap {
        max-width: 900px;
        margin: 120px auto 70px auto;
        padding: 20px;
    }

    /* SECTION */
    .section {
        display: none;
        animation: fade 0.4s ease forwards;
    }
    .active { display: block; }

    @keyframes fade {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* CARD */
    .card {
        background: rgba(0,0,30,0.55);
        border: 1px solid rgba(0,140,255,0.35);
        border-radius: 14px;
        padding: 25px;
        margin-bottom: 25px;
        box-shadow: 0 0 18px rgba(0, 110, 255, 0.2);
        transition: 0.2s;
    }
    .card:hover {
        transform: translateY(-2px);
        box-shadow: 0 0 28px rgba(0, 140, 255, 0.4);
    }
    h2 {
        color: #6ecbff;
        text-shadow: 0 0 12px #009dff;
    }

    /* FOOTER */
    footer {
        margin-top: 40px;
        text-align: center;
        font-size: 13px;
        color: #4f7ca5;
    }

</style>

<script>
function tampilkan(id){
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    var el = document.getElementById(id);
    if(el) el.classList.add('active');
    setTimeout(() => { window.scrollTo({ top: 0, behavior: 'smooth' }); }, 80);
}
window.addEventListener('DOMContentLoaded', function(){
    tampilkan('home');
});
</script>
</head>

<body>

<!-- NAVBAR -->
<div class="navbar">
    <div class="logo">
        <div class="dot"></div>
        Metode Numerik
    </div>

    <div class="nav-right">
        <a href="#" onclick="tampilkan('home'); return false;">Home</a>
        <a href="#" onclick="tampilkan('materi'); return false;">Materi</a>
        <a href="#" onclick="tampilkan('penulis'); return false;">Tentang Penulis</a>
    </div>
</div>

<!-- MAIN CONTENT -->
<main class="main-wrap">

    <!-- HOME -->
    <div id="home" class="section">
        <div class="card">
            <h2>Selamat Datang</h2>
            <p>
                Ini adalah website futuristik bertema biru neon yang membahas Metode Numerik.
                Gunakan menu di atas untuk menjelajah konten.
            </p>
        </div>
    </div>

    <!-- MATERI -->
    <div id="materi" class="section">
        <div class="card">
            <h2>Materi Metode Numerik</h2>
            <p>
                Di sini kamu dapat menemukan berbagai konsep dasar hingga lanjutan terkait metode numerik.
            </p>
        </div>
    </div>

    <!-- PENULIS -->
    <div id="penulis" class="section">
        <div class="card">
            <h2>Tentang Penulis</h2>
            <p>
                Penulis adalah seorang mahasiswa yang tertarik dengan pemrograman, AI, dan desain web futuristik.
            </p>
        </div>
    </div>

</main>

<footer>
    © 2025 Metode Numerik — Website Futuristik Biru Neon
</footer>

<!-- ====================================================== -->
<!-- == CHATBOT FLOATING (INI YANG KAMU MINTA, TIDAK DIUBAH) == -->
<!-- ====================================================== -->

<!-- Chatbot Floating Mini -->
<iframe 
    src="https://app.vectorshift.ai/chatbots/embedded/69330ecf9a83eafcbc725a1b?openChatbot=true"
    width="320px"
    height="430px"
    style="
        border: none;
        position: fixed;
        bottom: 15px;
        right: 15px;
        z-index: 9999;
        border-radius: 14px;
        box-shadow: 0 4px 18px rgba(0,0,0,0.35);
        background: #00000055;
        backdrop-filter: blur(6px);
    "
    allow="clipboard-read; clipboard-write; microphone">
</iframe>

</body>
</html>
