<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kuis Interaktif SSW Peternakan Part 7 (Soal 1-45)</title>
    <style>
        :root {
            --primary-color: #3b82f6;
            --primary-hover: #2563eb;
            --bg-color: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --border-color: #e2e8f0;
            --success-bg: #dcfce7;
            --success-border: #22c55e;
            --success-text: #15803d;
            --danger-bg: #fee2e2;
            --danger-border: #ef4444;
            --danger-text: #b91c1c;
        }

        * {
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            margin: 0;
            padding: 24px 16px;
            color: var(--text-main);
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 760px;
            background: var(--card-bg);
            padding: 32px;
            border-radius: 16px;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.01);
            border: 1px solid var(--border-color);
        }

        header {
            text-align: center;
            margin-bottom: 24px;
        }

        h1 {
            color: var(--text-main);
            font-size: 24px;
            font-weight: 700;
            margin: 0 0 8px 0;
            letter-spacing: -0.02em;
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 14px;
            margin: 0;
        }

        /* Banner Mode Review Salah */
        .review-mode-banner {
            background-color: #fef3c7;
            border: 1px solid #f59e0b;
            color: #b45309;
            padding: 10px 16px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            margin-bottom: 16px;
            display: none;
            justify-content: space-between;
            align-items: center;
        }

        .review-mode-banner.active {
            display: flex;
        }

        .btn-exit-review {
            background: #b45309;
            color: white;
            border: none;
            padding: 4px 10px;
            border-radius: 6px;
            font-size: 12px;
            cursor: pointer;
        }

        .btn-exit-review:hover {
            background: #92400e;
        }

        /* Progress Bar & Stats */
        .progress-section {
            margin-bottom: 24px;
        }

        .progress-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 14px;
            font-weight: 600;
            color: var(--text-muted);
            margin-bottom: 8px;
        }

        .progress-bar-bg {
            width: 100%;
            height: 10px;
            background-color: #e2e8f0;
            border-radius: 999px;
            overflow: hidden;
        }

        .progress-bar-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
            border-radius: 999px;
            transition: width 0.3s ease;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            background: #f1f5f9;
            padding: 12px 16px;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 24px;
        }

        .stat-item {
            display: flex;
            flex-direction: column;
        }

        .stat-value {
            font-size: 18px;
            font-weight: 700;
            color: var(--text-main);
        }

        .stat-label {
            font-size: 12px;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-top: 2px;
        }

        /* Card Soal */
        .question-card {
            background: #ffffff;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 24px;
            margin-bottom: 24px;
        }

        .question-title {
            font-size: 17px;
            font-weight: 600;
            color: var(--text-main);
            margin-bottom: 20px;
            line-height: 1.6;
            white-space: pre-line;
        }

        .options-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .option-btn {
            background: #fff;
            border: 1.5px solid var(--border-color);
            padding: 14px 18px;
            border-radius: 8px;
            text-align: left;
            cursor: pointer;
            font-size: 15px;
            color: var(--text-main);
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
        }

        .option-btn:hover:not(:disabled) {
            background: #f8fafc;
            border-color: var(--primary-color);
        }

        .option-btn.correct {
            background-color: var(--success-bg) !important;
            border-color: var(--success-border) !important;
            color: var(--success-text) !important;
            font-weight: 600;
        }

        .option-btn.incorrect {
            background-color: var(--danger-bg) !important;
            border-color: var(--danger-border) !important;
            color: var(--danger-text) !important;
        }

        .feedback {
            margin-top: 16px;
            padding: 12px 16px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            display: none;
        }

        .feedback.correct {
            display: block;
            background: var(--success-bg);
            color: var(--success-text);
            border: 1px solid var(--success-border);
        }

        .feedback.incorrect {
            display: block;
            background: var(--danger-bg);
            color: var(--danger-text);
            border: 1px solid var(--danger-border);
        }

        /* Navigasi dan Kontrol */
        .controls {
            display: flex;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 20px;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            background: var(--primary-color);
            color: white;
            transition: background 0.2s, transform 0.1s;
        }

        .btn:hover:not(:disabled) {
            background: var(--primary-hover);
        }

        .btn:active:not(:disabled) {
            transform: scale(0.98);
        }

        .btn:disabled {
            background: #cbd5e1;
            cursor: not-allowed;
        }

        .btn-outline {
            background: transparent;
            border: 1.5px solid var(--border-color);
            color: var(--text-main);
        }

        .btn-outline:hover:not(:disabled) {
            background: #f1f5f9;
            border-color: #cbd5e1;
        }

        .btn-reset {
            background: #ef4444;
            color: white;
        }

        .btn-reset:hover:not(:disabled) {
            background: #dc2626;
        }

        .btn-finish {
            background: #22c55e;
            color: white;
            display: block;
            width: 100%;
            margin-bottom: 16px;
            padding: 14px;
            font-size: 16px;
        }

        .btn-finish:hover:not(:disabled) {
            background: #16a34a;
        }

        .btn-review-wrong {
            background: #f59e0b;
            color: white;
        }

        .btn-review-wrong:hover:not(:disabled) {
            background: #d97706;
        }

        .bottom-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 16px;
            border-top: 1px solid var(--border-color);
            flex-wrap: wrap;
            gap: 12px;
        }

        .jump-container {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            color: var(--text-muted);
        }

        .jump-input {
            width: 70px;
            padding: 8px;
            border-radius: 6px;
            border: 1px solid var(--border-color);
            text-align: center;
            font-size: 14px;
            outline: none;
        }

        .jump-input:focus {
            border-color: var(--primary-color);
        }

        /* Modal / Ringkasan Nilai Akhir */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(15, 23, 42, 0.6);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 16px;
        }

        .modal-card {
            background: white;
            width: 100%;
            max-width: 480px;
            padding: 32px;
            border-radius: 16px;
            text-align: center;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }

        .modal-title {
            font-size: 22px;
            font-weight: 700;
            margin-bottom: 8px;
            color: var(--text-main);
        }

        .modal-score-box {
            background: #f8fafc;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 20px;
            margin: 20px 0;
            display: flex;
            justify-content: space-around;
        }

        .modal-stat-val {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-color);
        }

        .modal-stat-lbl {
            font-size: 12px;
            color: var(--text-muted);
            text-transform: uppercase;
            margin-top: 4px;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>Latihan Soal SSW Peternakan Part 7</h1>
        <p class="subtitle" id="total-subtitle">Kumpulan Soal ASAT Dokkai (Part 7)</p>
    </header>

    <!-- Banner Mode Review Salah -->
    <div class="review-mode-banner" id="review-banner">
        <span>⚠️ Mode Tinjau: Menampilkan soal yang salah / belum dijawab</span>
        <button class="btn-exit-review" onclick="exitReviewMode()">Keluar Mode Review</button>
    </div>

    <!-- Bar Persentase Pengerjaan -->
    <div class="progress-section">
        <div class="progress-info">
            <span id="progress-label">Progres Pengerjaan</span>
            <span id="progress-percent">0%</span>
        </div>
        <div class="progress-bar-bg">
            <div class="progress-bar-fill" id="progress-fill"></div>
        </div>
    </div>

    <!-- Statistik Utama -->
    <div class="stats-grid">
        <div class="stat-item">
            <span class="stat-value"><span id="current-no">1</span>/<span id="total-count">0</span></span>
            <span class="stat-label">Nomor Soal</span>
        </div>
        <div class="stat-item">
            <span class="stat-value" id="answered-count">0</span>
            <span class="stat-label">Terjawab</span>
        </div>
        <div class="stat-item">
            <span class="stat-value" id="score">0</span>
            <span class="stat-label">Skor Benar</span>
        </div>
    </div>

    <!-- Tombol Selesai & Lihat Nilai -->
    <button class="btn btn-finish" id="finish-quiz-btn" onclick="showFinalScoreModal()">🎉 Selesai & Lihat Nilai Akhir</button>

    <!-- Card Soal -->
    <div class="question-card">
        <div class="question-title" id="question-text">Memuat soal...</div>
        <div class="options-container" id="options-box"></div>
        <div class="feedback" id="feedback-box"></div>
    </div>

    <!-- Tombol Navigasi Utama -->
    <div class="controls">
        <button class="btn btn-outline" id="prev-btn" onclick="navigate(-1)">← Soal Sebelumnya</button>
        <button class="btn" id="next-btn" onclick="navigate(1)">Soal Berikutnya →</button>
    </div>

    <!-- Tombol Khusus Review Soal Salah -->
    <div style="margin-bottom: 16px; text-align: center;">
        <button class="btn btn-review-wrong" id="review-wrong-btn" onclick="startReviewWrongMode()">⚠️ Tinjau Soal Salah / Belum Dijawab (<span id="wrong-count-badge">0</span>)</button>
    </div>

    <!-- Bar Kontrol Bawah: Lompat & Reset -->
    <div class="bottom-bar">
        <div class="jump-container" id="jump-wrapper">
            <label for="jump-no" id="jump-label">Lompat ke:</label>
            <input type="number" id="jump-no" class="jump-input" min="1" placeholder="1">
            <button class="btn btn-outline" onclick="jumpToQuestion()">Go</button>
        </div>
        <button class="btn btn-reset" onclick="resetQuiz()">Ulangi Kuis</button>
    </div>
</div>

<!-- Modal Popup Nilai Akhir -->
<div class="modal-overlay" id="score-modal">
    <div class="modal-card">
        <div class="modal-title">Hasil Kuis Anda</div>
        <p style="color: var(--text-muted); font-size: 14px; margin: 0;">Berikut adalah rekapitulasi hasil pengerjaan kuis latihan SSW Peternakan Part 7.</p>
        
        <div class="modal-score-box">
            <div>
                <div class="modal-stat-val" id="modal-correct-score">0</div>
                <div class="modal-stat-lbl">Benar</div>
            </div>
            <div>
                <div class="modal-stat-val" id="modal-wrong-score" style="color: var(--danger-text);">0</div>
                <div class="modal-stat-lbl">Salah / Kosong</div>
            </div>
            <div>
                <div class="modal-stat-val" id="modal-percentage" style="color: #10b981;">0%</div>
                <div class="modal-stat-lbl">Persentase</div>
            </div>
        </div>

        <div style="display: flex; gap: 12px;">
            <button class="btn btn-outline" style="flex: 1;" onclick="closeModal()">Tutup</button>
            <button class="btn" style="flex: 1;" onclick="closeModal(); startReviewWrongMode();">Tinjau Soal Salah</button>
        </div>
    </div>
</div>

<script>
// Data Bank Soal dari PDF Part 7
const rawQuizData = [
  { n: 1, q: "Nutrisi dalam pakan ternak terbagi atas nutrisi yang dicerna dan diserap, dan bagian yang tidak dicerna.", o: ["A. benar", "B. salah"], a: "a" },
  { n: 2, q: "Berapa persen protein kasar (CP) dan energi metabolisme (ME) fase anak ayam kecil?", o: ["A. CP 19%, ME 2.900 kcal", "B. CP 16%, ME 2.800 kcal", "C. CP 13%, ME 2.700 kcal"], a: "a" },
  { n: 3, q: "Berapa persen protein kasar (CP) dan energi metabolisme (ME) fase anak ayam sedang?", o: ["A. CP 19%, ME 2.900 kcal", "B. CP 16%, ME 2.800 kcal", "C. CP 13%, ME 2.700 kcal"], a: "b" },
  { n: 4, q: "Berapa persen protein kasar (CP) dan energi metabolisme (ME) fase anak ayam besar?", o: ["A. CP 19%, ME 2.900 kcal", "B. CP 16%, ME 2.800 kcal", "C. CP 13%, ME 2.700 kcal"], a: "c" },
  { n: 5, q: "Berapa persen protein kasar (CP) dan energi metabolisme (ME) fase ayam bertelur?", o: ["A. CP 15,5%, ME 2.800 kcal", "B. CP 22%, ME 3.150 kcal", "C. CP 19%, ME 2.900 kcal"], a: "a" },
  { n: 6, q: "Berapa persen protein kasar (CP) dan energi metabolisme (ME) fase pemeliharaan?", o: ["A. CP 15,5%, ME 2.800 kcal", "B. CP 22%, ME 3.150 kcal", "C. CP 19%, ME 2.900 kcal"], a: "b" },
  { n: 7, q: "Berapa gram pemberian pakan fase pemeliharaan untuk makan bebas dalam sehari?", o: ["A. 10 gram", "B. 35 gram", "C. 115 gram"], a: "b" },
  { n: 8, q: "Berapa gram pemberian pakan fase ayam dewasa dalam sehari?", o: ["A. 10 gram", "B. 35 gram", "C. 115 gram"], a: "c" },
  { n: 9, q: "Pada pemeliharaan kandang, dilakukan inseminasi buatan. Setelah kawin telur yang dibuahi akan keluar sekitar hari keberapa?", o: ["A. hari ke-3", "B. hari ke-5", "C. hari ke-7"], a: "a" },
  { n: 10, q: "Berapa gram telur yang bagus dengan bentuk normal dan besar?", o: ["A. 40-50 gram", "B. 54-65 gram", "C. 70-80 gram"], a: "b" },
  { n: 11, q: "Telur yang bagus dan berbentuk normal disimpan di ruangan yang bersuhu berapa derajat?", o: ["A. 5-10 derajat", "B. 20-25 derajat", "C. 15-20 derajat"], a: "c" },
  { n: 12, q: "Berapa persen kelembaban untuk penyimpanan telur yang bagus?", o: ["A. 40-70%", "B. 10-30%", "C. 60-90%"], a: "a" },
  { n: 13, q: "Dalam jangka berapa hari sebaiknya periode penyimpanan telur dilakukan?", o: ["A. 7 hari", "B. 9 hari", "C. 11 hari"], a: "a" },
  { n: 14, q: "Berapa derajat dan berapa persen kelembaban yang dilakukan untuk proses penetasan telur?", o: ["A. 35,8 derajat dan 40%", "B. 37,8 derajat dan 60%", "C. 36,8 derajat dan 50%"], a: "b" },
  { n: 15, q: "Inkubator tiga dimensi adalah inkubator tipe kecil yang digunakan untuk praktikal", o: ["A. benar", "B. salah"], a: "b" },
  { n: 16, q: "Yang bukan termasuk pekerjaan sebelum telur ayam menetas adalah?", o: ["A. membersihkan, mencuci dan mendisinfeksikan inkubator", "B. memeriksa alat pengukur suhu dan kelembapan", "C. mencuci telur yang belum dibuahi"], a: "c" },
  { n: 17, q: "Yang bukan termasuk pengelolaan selama penetasan telur adalah?", o: ["A. menjejerkan telur dengan ujung tumpul kebawah", "B. memberikan tanda supaya tahu varietas dan jenisnya", "C. memberikan ventilasi yang baik", "D. memutar telur 10-20 kali sehari"], a: "a" },
  { n: 18, q: "Pada hari keberapa pemeriksaan telur dilakukan?", o: ["A. Hari ke 7", "B. Hari ke 5", "C. Hari ke 3"], a: "a" },
  { n: 19, q: "Yang bukan termasuk cara membedakan jenis kelamin anak ayam jantan dan betina adalah?", o: ["A. melalui bentuk kloaka anak ayam", "B. melalui perbedaan besar kepala dan kaki", "C. kecepatan pertumbuhan bulu sayap utama"], a: "b" },
  { n: 20, q: "Yang bukan 3 metode pemeliharaan ayam adalah?", o: ["A. Metode dengan alat pemeliharaan bentuk box", "B. Metode pemeliharaan baterai", "C. Metode pemeliharaan umum", "D. Metode pemeliharaan umbaran"], a: "c" },
  { n: 21, q: "Kira-kira berapa ekor yang bisa dipelihara di dalam box?", o: ["A. 50-100 ekor", "B. 100-150 ekor", "C. 150-200 ekor"], a: "a" },
  { n: 22, q: "Ayam yang baru menetas dan tiba di peternakan ayam dengan waktu yang lama sebaiknya bagaimana? Pilihlah yang salah", o: ["A. bila sudah tiba segera berikan air", "B. biarkan istirahat dalam ruangan gelap sebentar", "C. segera di umbar"], a: "c" },
  { n: 23, q: "Berapa derajat dan berapa persen kelembaban untuk alat pemeliharaan tipe baterai, alat pemeliharaan tipe umbaran (mempergunakan chick guard), ataupun kehangatan permukaan lantai (mempergunakan chick guard)?", o: ["A. 32-35 derajat dan 65%", "B. 25-30 derajat dan 60%", "C. 20-25 derajat dan 55%"], a: "a" },
  { n: 24, q: "Berapa jam standar pemberian pakan untuk anak ayam yang baru menetas?", o: ["A. 10-30 jam", "B. 25-60 jam", "C. 20-40 jam"], a: "b" },
  { n: 25, q: "Fungsi debeak atau beak trimming adalah sebagai pencegahan kebiasaan buruk seperti patuk ekor atau makan bulu pada setelah fase anak ayam sedang.", o: ["A. benar", "B. salah"], a: "a" },
  { n: 26, q: "Umumnya pada umur berapa anak ayam dilakukan pemotongan paruh?", o: ["A. 2-3 minggu", "B. 1-2 minggu", "C. 3-4 minggu"], a: "b" },
  { n: 27, q: "Berapa ekor kepadatan pemeliharaan ayam pada kandang tipe baterai hingga umur 6 minggu?", o: ["A. 22-34 ekor", "B. 33-44 ekor", "C. 44-54 ekor"], a: "b" },
  { n: 28, q: "Berapa ekor kepadatan pemeliharaan ayam pada kandang tipe umbaran hingga umur 6 minggu?", o: ["A. 18-20 ekor", "B. 24-26 ekor", "C. 28-30 ekor"], a: "a" },
  { n: 29, q: "Pada anak ayam untuk meringankan stress atau pencegahan penyakit, maka sebaiknya larutkan antibiotik, vitamin dan sebagainya ke air, dan berikan selama berapa hari?", o: ["A. 1 hari", "B. 4 hari", "C. 2-3 hari"], a: "c" },
  { n: 30, q: "Berapa gram bobot anak ayam pada umur seminggu?", o: ["A. 65 gram lebih", "B. 120 gram lebih", "C. 190 gram lebih", "D. 850 gram lebih"], a: "a" },
  { n: 31, q: "Berapa gram bobot anak ayam pada umur 2 minggu?", o: ["A. 65 gram lebih", "B. 120 gram lebih", "C. 190 gram lebih", "D. 850 gram lebih"], a: "b" },
  { n: 32, q: "Berapa gram bobot anak ayam pada umur 3 minggu?", o: ["A. 65 gram lebih", "B. 120 gram lebih", "C. 190 gram lebih", "D. 850 gram lebih"], a: "c" },
  { n: 33, q: "Berapa gram bobot anak ayam pada umur 10 minggu?", o: ["A. 65 gram lebih", "B. 120 gram lebih", "C. 190 gram lebih", "D. 850 gram lebih"], a: "d" },
  { n: 34, q: "Anak ayam besar yang cepat matang akan mulai bertelur pada umur berapa?", o: ["A. 130 hari", "B. 110 hari", "C. 90 hari"], a: "a" },
  { n: 35, q: "Berapa ekor kepadatan pemeliharaan ayam pada kandang tipe baterai hingga umur 18 minggu?", o: ["A. 22-25 ekor", "B. 15-18 ekor", "C. 7-8 ekor"], a: "a" },
  { n: 36, q: "Berapa ekor kepadatan pemeliharaan ayam pada kandang tipe umbaran hingga umur 18 minggu?", o: ["A. 22-25 ekor", "B. 15-18 ekor", "C. 7-8 ekor"], a: "c" },
  { n: 37, q: "Fungsi pemberian penerangan dengan waktu yang lama untuk anak ayam besar adalah?", o: ["A. untuk kekebalan tubuh", "B. untuk mengatur kematangan seksual", "C. untuk menambah berat badan"], a: "b" },
  { n: 38, q: "Umur berapa ayam petelur akan mulai bertelur?", o: ["A. pada sekitar umur 18 minggu", "B. pada sekitar umur 14 minggu", "C. pada umur sekitar 10 minggu"], a: "a" },
  { n: 39, q: "Selama berapa bulan ayam petelur akan menghasilkan banyak telur?", o: ["A. 3-5 bulan", "B. 1-2 bulan", "C. 2-4 bulan"], a: "c" },
  { n: 40, q: "Pengertian clutch adalah produksi telur yang serangkaian berturut-turut.", o: ["A. benar", "B. salah"], a: "a" },
  { n: 41, q: "Pada musim apa produksi telur akan banyak?", o: ["A. musim gugur", "B. musim semi", "C. musim panas"], a: "b" },
  { n: 42, q: "Pada musim apa anak ayam akan menetas?", o: ["A. musim semi dan gugur", "B. musim panas dan dingin", "C. musim gugur dan dingin"], a: "a" },
  { n: 43, q: "Suhu yang optimal untuk bertelur adalah?", o: ["A. 12-25 derajat celsius", "B. 25-30 derajat celsius", "C. 30-35 derajat celsius"], a: "a" },
  { n: 44, q: "Yang bukan termasuk pengelolaan fase ayam dewasa adalah?", o: ["A. Pemberian Pakan dan Suplai Air", "B. Pengumpulan Telur dan Pengelolaan Lingkungan", "C. Pembuangan Kotoran dan Pembersihan", "D. Pemberian vaksin"], a: "d" },
  { n: 45, q: "Berapa suhu tubuh ayam dewasa yang sehat?", o: ["A. sekitar 41 derajat celsius", "B. sekitar 38 derajat celsius", "C. sekitar 35 derajat celsius"], a: "a" }
];

const quizData = rawQuizData.map((item, index) => ({
    ...item,
    displayNo: index + 1
}));

// Inisialisasi State Aplikasi
let currentIndex = 0;
let userAnswers = new Array(quizData.length).fill(null);
let isReviewWrongMode = false;
let wrongOrUnansweredIndicesList = [];
let reviewCurrentIdx = 0;

// Muat data dari LocalStorage jika ada
function loadSavedState() {
    const savedAnswers = localStorage.getItem('ssw_quiz_part7_answers');
    const savedIndex = localStorage.getItem('ssw_quiz_part7_index');
    
    if (savedAnswers) {
        userAnswers = JSON.parse(savedAnswers);
    }
    if (savedIndex !== null) {
        currentIndex = parseInt(savedIndex, 10);
    }
}

// Simpan data ke LocalStorage
function saveState() {
    localStorage.setItem('ssw_quiz_part7_answers', JSON.stringify(userAnswers));
    localStorage.setItem('ssw_quiz_part7_index', currentIndex);
}

// Update Statistik & Progress Bar
function updateStats() {
    const total = quizData.length;
    let answeredCount = 0;
    let scoreCount = 0;
    let wrongOrUnansweredCount = 0;

    userAnswers.forEach((ans, idx) => {
        if (ans !== null) {
            answeredCount++;
            if (ans === quizData[idx].a.toLowerCase()) {
                scoreCount++;
            } else {
                wrongOrUnansweredCount++;
            }
        } else {
            wrongOrUnansweredCount++;
        }
    });

    const percent = Math.round((answeredCount / total) * 100);

    document.getElementById('answered-count').innerText = answeredCount;
    document.getElementById('score').innerText = scoreCount;
    document.getElementById('progress-percent').innerText = `${percent}%`;
    document.getElementById('progress-fill').style.width = `${percent}%`;

    const reviewBtn = document.getElementById('review-wrong-btn');
    const wrongBadge = document.getElementById('wrong-count-badge');
    
    if (wrongOrUnansweredCount > 0) {
        wrongBadge.innerText = wrongOrUnansweredCount;
        reviewBtn.style.display = 'inline-block';
    } else {
        reviewBtn.style.display = 'none';
    }
}

// Tampilkan Soal Sesuai Index
function loadQuestion() {
    let activeIndex = currentIndex;

    if (isReviewWrongMode) {
        activeIndex = wrongOrUnansweredIndicesList[reviewCurrentIdx];
        document.getElementById('current-no').innerText = `${reviewCurrentIdx + 1} (Dari ${wrongOrUnansweredIndicesList.length} Soal Tinjauan)`;
    } else {
        document.getElementById('current-no').innerText = quizData[activeIndex].displayNo;
    }

    const item = quizData[activeIndex];
    document.getElementById('question-text').innerText = `${item.displayNo}. ${item.q}`;

    const optionsBox = document.getElementById('options-box');
    optionsBox.innerHTML = '';

    const feedbackBox = document.getElementById('feedback-box');
    feedbackBox.style.display = 'none';

    item.o.forEach((optionText) => {
        const optionKey = optionText.trim().charAt(0).toLowerCase();
        const btn = document.createElement('button');
        btn.className = 'option-btn';
        btn.innerText = optionText;
        
        if (userAnswers[activeIndex] !== null) {
            btn.disabled = true;
            if (optionKey === item.a.toLowerCase()) {
                btn.classList.add('correct');
            }
            if (userAnswers[activeIndex] === optionKey && optionKey !== item.a.toLowerCase()) {
                btn.classList.add('incorrect');
            }
        } else {
            btn.onclick = () => selectAnswer(optionKey, item.a.toLowerCase(), activeIndex);
        }
        
        optionsBox.appendChild(btn);
    });

    if (userAnswers[activeIndex] !== null) {
        feedbackBox.style.display = 'block';
        if (userAnswers[activeIndex] === item.a.toLowerCase()) {
            feedbackBox.className = 'feedback correct';
            feedbackBox.innerText = isReviewWrongMode ? 'Jawaban Anda Benar Sekarang!' : 'Jawaban Anda Benar!';
        } else {
            feedbackBox.className = 'feedback incorrect';
            feedbackBox.innerText = `Jawaban Anda Salah. Jawaban Benar: (${item.a.toUpperCase()})`;
        }
    } else {
        if (isReviewWrongMode) {
            feedbackBox.style.display = 'block';
            feedbackBox.className = 'feedback incorrect';
            feedbackBox.innerText = '⚠️ Belum dijawab';
        }
    }

    if (isReviewWrongMode) {
        document.getElementById('prev-btn').disabled = reviewCurrentIdx === 0;
        document.getElementById('next-btn').disabled = reviewCurrentIdx === wrongOrUnansweredIndicesList.length - 1;
    } else {
        document.getElementById('prev-btn').disabled = currentIndex === 0;
        document.getElementById('next-btn').disabled = currentIndex === quizData.length - 1;
    }

    updateStats();
    if (!isReviewWrongMode) {
        saveState();
    }
}

// Memilih Jawaban
function selectAnswer(selectedKey, correctKey, activeIndex) {
    userAnswers[activeIndex] = selectedKey;
    loadQuestion();
}

// Navigasi Maju/Mundur
function navigate(direction) {
    if (isReviewWrongMode) {
        reviewCurrentIdx += direction;
        if (reviewCurrentIdx < 0) reviewCurrentIdx = 0;
        if (reviewCurrentIdx >= wrongOrUnansweredIndicesList.length) reviewCurrentIdx = wrongOrUnansweredIndicesList.length - 1;
    } else {
        currentIndex += direction;
        if (currentIndex < 0) currentIndex = 0;
        if (currentIndex >= quizData.length) currentIndex = quizData.length - 1;
    }
    loadQuestion();
}

// Lompat ke Nomor Tertentu
function jumpToQuestion() {
    if (isReviewWrongMode) return;
    const val = parseInt(document.getElementById('jump-no').value);
    if (val >= 1 && val <= quizData.length) {
        currentIndex = val - 1;
        loadQuestion();
    } else {
        alert(`Masukkan nomor soal antara 1 sampai ${quizData.length}.`);
    }
}

// Tampilkan Modal Nilai Akhir
function showFinalScoreModal() {
    let scoreCount = 0;
    let wrongOrUnansweredCount = 0;

    userAnswers.forEach((ans, idx) => {
        if (ans !== null) {
            if (ans === quizData[idx].a.toLowerCase()) {
                scoreCount++;
            } else {
                wrongOrUnansweredCount++;
            }
        } else {
            wrongOrUnansweredCount++;
        }
    });

    const total = quizData.length;
    const percent = Math.round((scoreCount / total) * 100);

    document.getElementById('modal-correct-score').innerText = scoreCount;
    document.getElementById('modal-wrong-score').innerText = wrongOrUnansweredCount;
    document.getElementById('modal-percentage').innerText = `${percent}%`;

    document.getElementById('score-modal').style.display = 'flex';
}

// Tutup Modal Nilai Akhir
function closeModal() {
    document.getElementById('score-modal').style.display = 'none';
}

// Memulai Mode Review Soal Salah / Belum Dijawab
function startReviewWrongMode() {
    wrongOrUnansweredIndicesList = [];
    userAnswers.append = undefined;
    userAnswers.forEach((ans, idx) => {
        if (ans === null || ans !== quizData[idx].a.toLowerCase()) {
            wrongOrUnansweredIndicesList.push(idx);
        }
    });

    if (wrongOrUnansweredIndicesList.length === 0) {
        alert("Semua soal sudah dijawab dengan benar! Kerja bagus!");
        return;
    }

    isReviewWrongMode = true;
    reviewCurrentIdx = 0;

    document.getElementById('review-banner').classList.add('active');
    document.getElementById('jump-wrapper').style.display = 'none';
    document.getElementById('progress-label').innerText = 'Progres Sesi Review';

    loadQuestion();
}

// Keluar dari Mode Review
function exitReviewMode() {
    isReviewWrongMode = false;
    document.getElementById('review-banner').classList.remove('active');
    document.getElementById('jump-wrapper').style.display = 'flex';
    document.getElementById('progress-label').innerText = 'Progres Pengerjaan';
    loadQuestion();
}

// Reset Kuis / Ulang dari Awal
function resetQuiz() {
    if (confirm("Apakah Anda yakin ingin mengulang kuis dari awal? Semua jawaban Anda akan dihapus.")) {
        userAnswers = new Array(quizData.length).fill(null);
        currentIndex = 0;
        isReviewWrongMode = false;
        document.getElementById('review-banner').classList.remove('active');
        document.getElementById('jump-wrapper').style.display = 'flex';
        document.getElementById('progress-label').innerText = 'Progres Pengerjaan';
        localStorage.removeItem('ssw_quiz_part7_answers');
        localStorage.removeItem('ssw_quiz_part7_index');
        loadQuestion();
    }
}

// Inisialisasi Pertama
document.getElementById('total-count').innerText = quizData.length;
document.getElementById('total-subtitle').innerText = `Kumpulan Soal ASAT Dokkai (Total Soal: ${quizData.length})`;
const jumpInput = document.getElementById('jump-no');
jumpInput.max = quizData.length;
jumpInput.placeholder = `1-${quizData.length}`;

loadSavedState();
loadQuestion();
</script>

</body>
</html>
