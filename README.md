<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Metode Numerik • Futuristik (Biru Neon)</title>

<style>
        #home p {
        text-align: justify;
        text-justify: inter-word;
    }
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
        width: 80px;
        height: 80px;
        border-radius: 12px;
        object-fit: cover;
        border: 2px solid #444;
    }
    
    .author-info h3 {
        margin: 0;
        font-size: 20px;
        color: #fff;
    }
    
    .author-info p {
        margin: 2px 0;
        color: #ccc;
        font-size: 15px;
    }

    /* ---------------------------
       GLOBAL: DARK FUTURISTIC (A)
       --------------------------- */
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
        height:100%;
        margin:0;
        padding:0;
        background: radial-gradient(circle at 10% 10%, #071230 0%, var(--bg-1) 25%, var(--bg-2) 100%);
        font-family: "Inter", "Segoe UI", Roboto, Arial, sans-serif;
        color: var(--text);
        -webkit-font-smoothing:antialiased;
        -moz-osx-font-smoothing:grayscale;
    }

    a { color: var(--accent-2); text-decoration: none; }
    a:hover { text-decoration: underline; }

    /* ------------- NAVBAR ------------- */
    .navbar {
        position: sticky;
        top: 0;
        z-index: 50;
        display:flex;
        align-items:center;
        justify-content:space-between;
        gap:20px;
        padding:16px 28px;
        margin:0;
        background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.00));
        border-bottom: 1px solid rgba(110,168,255,0.06);
        backdrop-filter: blur(8px) saturate(120%);
        box-shadow: 0 6px 30px rgba(3,10,25,0.6);
    }

    .logo {
        display:flex;
        align-items:center;
        gap:12px;
        font-weight:700;
        color: var(--accent-2);
        font-size:20px;
        letter-spacing:0.2px;
        text-shadow: 0 0 12px rgba(110,168,255,0.14);
    }

    .logo .dot {
        width:10px;height:10px;border-radius:50%;
        background: linear-gradient(90deg,var(--accent),#bfe7ff);
        box-shadow: 0 0 12px rgba(110,168,255,0.9), 0 0 30px rgba(110,168,255,0.08);
    }

    .nav-right {
        display:flex;
        gap:26px;
        align-items:center;
        font-weight:600;
    }

    .nav-right a {
        color: var(--muted);
        font-size:16px;
        transition:0.18s ease;
        padding:8px 10px;
        border-radius:8px;
    }

    .nav-right a:hover {
        color: white;
        background: linear-gradient(90deg, rgba(110,168,255,0.06), rgba(110,168,255,0.03));
        box-shadow: 0 6px 20px rgba(30,70,140,0.12);
        transform: translateY(-2px);
    }

    /* ---------- LAYOUT CONTAINER ---------- */
    .main-wrap {
        width: 94%;
        max-width: 1100px;
        margin: 36px auto 80px auto;
        padding: 0 12px;
    }

    .section {
        display: none;
        margin-bottom: 34px;
    }

    .section.active {
        display: block;
        animation: fadeUp .45s ease both;
    }

    @keyframes fadeUp {
        from { opacity: 0; transform: translateY(8px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* ---------- CARD (FUTURISTIC) ---------- */
    .card {
        background: var(--card);
        border-radius: 14px;
        padding: 28px;
        border: 1px solid rgba(110,168,255,0.06);
        box-shadow:
            0 10px 30px rgba(5,10,25,0.5),
            inset 0 1px 0 rgba(255,255,255,0.02);
        backdrop-filter: blur(8px) saturate(120%);
    }

    h2 {
        margin: 0 0 12px 0;
        font-size: 28px;
        color: var(--accent-2);
        text-shadow: 0 6px 26px rgba(110,168,255,0.06);
    }

    h3 {
        margin-top: 18px;
        color: var(--accent);
        font-size: 18px;
        margin-bottom:8px;
    }

    p, li {
        color: var(--text);
        font-size: 16px;
        line-height: 1.7;
    }

    ul { padding-left: 18px; }

    /* ---------- PRE ---------- */
    pre, .code-box {
        background: var(--pre-bg-dark) !important;
        color: #dff6ff !important;
        padding: 14px 16px !important;
        border-radius: 10px !important;
        border: 1px solid var(--pre-border-dark) !important;
        box-shadow: 0 6px 18px rgba(15,30,60,0.5), 0 0 18px rgba(110,168,255,0.04) inset;
        overflow-x: auto;
        white-space: pre-wrap !important;
        font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", monospace;
        font-size: 14px;
        line-height:1.55;
    }

    b { color: #e9f6ff; font-weight:700; }

    @media (max-width:720px){
        .nav-right { gap:14px; font-size:15px; }
        .main-wrap { width:95%; margin-top: 22px; padding:0 8px; }
        h2 { font-size:22px; }
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
        <div class="dot" aria-hidden="true"></div>
        Metode Numerik
    </div>

    <div class="nav-right" role="navigation" aria-label="Main navigation">
        <a href="#" onclick="tampilkan('home'); return false;">Home</a>
        <a href="#" onclick="tampilkan('materi'); return false;">Materi</a>
        <a href="#" onclick="tampilkan('penulis'); return false;">Tentang Penulis</a>
    </div>
</div>

<!-- MAIN -->
<main class="main-wrap">

    <!-- HOME -->
    <section id="home" class="section card">
        <h2>Selamat Datang</h2>
        <p>
            Landing page ini dibuat sebagai media pembelajaran untuk mata kuliah Metode Numerik 
            dengan fokus pada materi interpolasi. Di dalamnya, pengguna diajak memahami cara kerja 
            interpolasi melalui contoh yang dekat dengan kehidupan nyata, yaitu data jumlah penduduk 
            pada sebuah kabupaten. Materi disusun agar mudah diikuti sehingga konsep yang awalnya terlihat 
            rumit bisa terasa lebih masuk akal ketika dipelajari lewat data nyata.
            <br><br>
            Tampilan dan alurnya dibuat jelas serta nyaman untuk diikuti. Pengguna dapat membaca 
            penjelasan materi, mencoba melakukan perhitungan interpolasi, dan melihat hasil visualisasinya 
            secara langsung. Semua fitur disusun agar pembelajaran terasa lebih praktis sehingga pengguna 
            tidak hanya membaca teori tetapi juga melihat bagaimana langkah perhitungannya berjalan.
            <br><br>
            Secara keseluruhan, halaman ini membantu mahasiswa memahami bagaimana interpolasi digunakan 
            untuk memperkirakan nilai yang belum diketahui berdasarkan data yang tersedia. Pembelajaran 
            dibuat sederhana tanpa kesan terlalu teknis sehingga pengguna bisa langsung fokus pada inti 
            materi dan memahami manfaat metode numerik dalam analisis data.
        </p>
    </section>

    <!-- MATERI -->
    <div id="materi" class="container section card">
        <h2>Interpolasi Beda Bagi Newton</h2>

        <p>
            Interpolasi Newton adalah metode untuk membangun polinom interpolasi 
            berdasarkan tabel <b>beda bagi (divided difference)</b>. 
            Metode ini cocok ketika titik-titik data tidak memiliki jarak yang sama.
        </p>

        <h3>1. Konsep Dasar</h3>
        <p>
            Diberikan titik-titik data:
            <br>
            (x₀, f(x₀)), (x₁, f(x₁)), ..., (xₙ, f(xₙ))
            <br><br>
            Tujuan interpolasi adalah membuat polinom P(x) sehingga:
            <br>
            P(xᵢ) = f(xᵢ) untuk semua i.
        </p>

        <h3>2. Definisi Beda Bagi</h3>

        <p><b>Beda bagi orde 1:</b></p>
        <pre>
f[x₀, x₁] = ( f(x₁) - f(x₀) ) / ( x₁ - x₀ )
        </pre>

        <p><b>Beda bagi orde 2:</b></p>
        <pre>
f[x₀, x₁, x₂] = ( f[x₁, x₂] - f[x₀, x₁] ) / ( x₂ - x₀ )
        </pre>

        <p><b>Beda bagi orde ke-n:</b></p>
        <pre>
f[x₀, x₁, ..., xₙ] = ( f[x₁, ..., xₙ] - f[x₀, ..., xₙ₋₁] ) / ( xₙ - x₀ )
        </pre>

        <h3>3. Bentuk Umum Polinom Newton</h3>

        <p>
            Polinom Newton dalam bentuk <b>Newton maju</b> adalah:
        </p>

        <pre>
P(x) = f[x₀] + f[x₀,x₁](x - x₀) + f[x₀,x₁,x₂](x - x₀)(x - x₁) + ... 
       + f[x₀,x₁,...,xₙ](x - x₀)(x - x₁)...(x - xₙ₋₁)
        </pre>

        <h3>4. Contoh Tabel Beda Bagi</h3>

        <p>Misalkan tabel data:</p>

        <pre>
x       : 1   2   4
f(x)    : 1   4   16
        </pre>

        <p>Buat tabel beda bagi:</p>

        <pre>
     x     f(x)     Δ1      Δ2
-------------------------------------------
     1      1       3        1
     2      4       6
     4      16
-------------------------------------------
        </pre>

        <h3>5. Polinomnya</h3>

        <pre>
P(x) = f[x₀] + f[x₀,x₁](x - x₀) + f[x₀,x₁,x₂](x - x₀)(x - x₁)
     = 1 + 3(x - 1) + 1(x - 1)(x - 2)
        </pre>

        <h3>6. Kelebihan Metode Beda Bagi Newton</h3>
        <ul>
            <li>Dapat digunakan untuk data dengan jarak tidak sama.</li>
            <li>Penyusunan tabel sederhana dan sistematis.</li>
            <li>Mudah menambah titik baru tanpa mengulang seluruh perhitungan.</li>
            <li>Stabil secara numerik dibanding metode interpolasi lainnya.</li>
        </ul>

        <h3>7. Kekurangan</h3>
        <ul>
            <li>Masih sensitif terhadap banyak titik (Runge phenomenon).</li>
            <li>Jika titik sangat rapat, beda bagi bisa menyebabkan pembulatan.</li>
            <li>Polinom derajat tinggi tidak selalu representatif terhadap data asli.</li>
        </ul>

        <h3>8. Penggunaan dalam Komputasi (Algoritma)</h3>
        <pre>
1. Siapkan tabel x dan f(x)
2. Hitung beda bagi orde 1, simpan kolom pertama
3. Hitung beda bagi orde 2, simpan kolom pertama
4. Lanjutkan hingga orde n
5. Masukkan ke rumus Newton
6. Evaluasi P(x)
        </pre>

        <h3>9. Kesimpulan</h3>
        <p>
            Interpolasi Beda Bagi Newton merupakan metode efektif,
            fleksibel, dan sangat berguna dalam penyelesaian numerik
            ketika titik-titik data tidak berjarak sama.
        </p>

    </div>

<!-- PENULIS -->
<div id="penulis" class="container section">

    <h2>Tentang Penulis</h2>

    <!-- Penulis 1 -->
    <div class="author-card">
        <img src="author1.png" alt="Foto Alfredho Fathurrahman Rizquna Ahmadi" class="author-photo">
        <div class="author-info">
            <h3>Alfredho Fathurrahman Rizquna Ahmadi</h3>
            <p>Mahasiswa Pendidikan Matematika – Universitas Sebelas Maret</p>
            <p>Fokus pada pengembangan media pembelajaran matematika berbasis teknologi.</p>
        </div>
    </div>

    <!-- Penulis 2 -->
    <div class="author-card">
        <img src="author2.jpg" alt="Foto Galih Wicaksono" class="author-photo">
        <div class="author-info">
            <h3>Galih Wicaksono</h3>
            <p>Mahasiswa Pendidikan Matematika – Universitas Sebelas Maret</p>
            <p>Memiliki minat pada metode numerik, pemrograman, dan desain sistem pembelajaran digital.</p>
        </div>
    </div>

</div>

</main>

<!-- ============= CHATBOT FLOATING (UTUH, TIDAK DIUBAH) ============= -->
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
