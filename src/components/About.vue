<template>
  <section id="about" class="about-section">
    <div class="container">
      
      <!-- heading -->
      <div class="about-head">
        <div>
          <p class="about-label">About</p>
          <h2 class="about-title">
            Firma Hukum Strategis untuk Perlindungan & Pertumbuhan Bisnis
          </h2>
        </div>

        <p class="about-desc">
          <b>Prosperity Law Firm</b> memberikan layanan hukum strategis dan
          berorientasi hasil, dengan fokus pada <b>hukum korporasi dan kepailitan</b>.
          Kami mendampingi perusahaan dan individu dalam menghadapi risiko hukum,
          restrukturisasi usaha, serta kompleksitas regulasi di Indonesia.
          <br><br>
          Setiap perkara ditangani oleh tim advokat berpengalaman melalui analisa
          mendalam, strategi terukur, dan komunikasi yang transparan — sehingga
          keputusan hukum selaras dengan kepentingan dan tujuan klien.
        </p>
      </div>

      <!-- cards -->
      <div class="about-grid">
        <div class="about-card">
          <div class="icon gold">
            <AcademicCapIcon />
          </div>
          <div>
            <h3>Keahlian Korporasi & Kepailitan</h3>
            <p>
              Ditangani oleh advokat berpengalaman di bidang hukum korporasi,
              restrukturisasi, dan proses kepailitan usaha.
            </p>
          </div>
        </div>

        <div class="about-card">
          <div class="icon blue">
            <ChartBarIcon />
          </div>
          <div>
            <h3>Pendekatan Analitis & Strategis</h3>
            <p>
              Setiap perkara disusun berbasis riset, analisa risiko,
              dan strategi hukum yang terukur.
            </p>
          </div>
        </div>

        <div class="about-card">
          <div class="icon green">
            <HandThumbUpIcon />
          </div>
          <div>
            <h3>Berorientasi pada Kepentingan Klien</h3>
            <p>
              Komunikasi transparan dan pendekatan personal
              untuk memastikan tujuan klien menjadi prioritas utama.
            </p>
          </div>
        </div>

        <div class="about-card">
          <div class="icon dark">
            <ShieldCheckIcon />
          </div>
          <div>
            <h3>Perlindungan & Solusi Berkelanjutan</h3>
            <p>
              Fokus pada perlindungan hukum jangka panjang,
              bukan sekadar penyelesaian sengketa sesaat.
            </p>
          </div>
        </div>

      </div>
    </div>
    <div class="about-divider">
      <svg viewBox="0 0 1440 120" preserveAspectRatio="none">
        <path
          d="M0,64 C320,120 720,0 1440,64 L1440,120 L0,120 Z"
          fill="#0f172a"
          fill-opacity="1"
        />
      </svg>
    </div>

  </section>
</template>

<script setup>
  import { AcademicCapIcon, ChartBarIcon, HandThumbUpIcon, ShieldCheckIcon } 
  from '@heroicons/vue/24/solid'
</script>

<style scoped>
  .about-divider {
    position: absolute;
    left: 0;
    bottom: 0;               /* nempel ke dasar section */
    width: 100%;
    height: 150px;
    overflow: hidden;
    line-height: 0;
    z-index: 2;
    pointer-events: none;
  }
  
  .about-divider svg {
    width: 100%;
    height: 100%;
    display: block;
  }

  .about-section {
    position: relative;
    padding: 80px 0 150px;   /* tambah padding bawah = tinggi divider */
    background: linear-gradient(to bottom, #f8fafc, #eef2f7);
    overflow: hidden;
    scroll-margin-top: 68px;
    margin-bottom: 0;        /* buang margin bawah */
  }
  /* accent line atas */
  .about-section::before {
    content: "";
    position: absolute;
    top: 0;
    left: 8%;
    width: 120px;
    height: 4px;
    background: linear-gradient(to right, #d4af37, #f6d365);
    border-radius: 4px;
  }

  .container {
    max-width: 1200px;
    margin: auto;
    padding: 0 24px;
  }

  .icon {
    width: 48px;
    height: 48px;
    border-radius: 14px;
    display: grid;
    place-items: center;
    flex-shrink: 0;
    transition: transform .25s ease, box-shadow .25s ease;
  }

  .icon svg {
    animation: iconIn .6s ease both;
  }

  @keyframes iconIn {
    from {
      opacity: 0;
      transform: scale(.7) rotate(-8deg);
    }
    to {
      opacity: 1;
      transform: scale(1) rotate(0);
    }
  }

  .about-card:hover .icon {
    transform: translateY(-4px) scale(1.08);
    box-shadow: 0 8px 22px rgba(0,0,0,0.12);
  }

  /* ===== heading ===== */

  .about-head {
    display: grid;
    gap: 24px;
    margin-bottom: 60px;
  }

  @media (min-width: 768px) {
    .about-head {
      grid-template-columns: 1fr 1fr;
      align-items: center;
    }
  }

  .about-label {
    font-size: 15px;
    letter-spacing: .25em;
    font-weight: 700;
    color: #d4af37;
    text-transform: uppercase;
    margin-bottom: 10px;
  }

  .about-title {
    font-size: 35px;
    font-weight: 700;
    color: #0f172a;
    line-height: 1.3;
  }

  .about-desc {
    color: #475569;
    line-height: 1.7;
    font-size: 18px;
  }

  /* ===== grid ===== */

  .about-grid {
    display: grid;
    gap: 22px;
  }

  @media (min-width: 640px) {
    .about-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  /* ===== card ===== */

  .about-card {
    position: relative;
    display: flex;
    gap: 16px;
    padding: 26px;
    border-radius: 18px;
    background: white;
    border: 1px solid #e5e7eb;
    box-shadow: 0 10px 30px rgba(15,23,42,0.06);
    transition: all .35s ease;
    overflow: hidden;
  }

  /* gradient hover edge */
  .about-card::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(120deg, transparent, rgba(247, 228, 167, 0.4)); 
    opacity: 0;
    transition: .35s;
  }

  .about-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 18px 50px rgba(15,23,42,0.12);
  }

  .about-card:hover::after {
    opacity: 1;
  }

  .about-card h3 {
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 6px;
    color: #0f172a;
  }

  .about-card p {
    font-size: 15px;
    color: #64748b;
    line-height: 1.6;
  }

  /* ===== icon bubble ===== */

  .icon {
    width: 48px;
    height: 48px;
    border-radius: 14px;
    display: grid;
    place-items: center;
    flex-shrink: 0;
  }

  .icon svg {
    width: 24px;
    height: 24px;
  }

  /* color themes */
  .icon.gold  { background: #fef3c7; color: #b45309; }
  .icon.blue  { background: #dbeafe; color: #1d4ed8; }
  .icon.green { background: #d1fae5; color: #047857; }
  .icon.dark  { background: #e5e7eb; color: #111827; }

  /* ===== subtle reveal ===== */

  .about-card {
    animation: cardIn .6s ease both;
  }

  @keyframes cardIn {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* mobile tweak */
  @media (max-width: 640px) {

    .about-section {
      padding: 70px 0 100px; 
    }

    .about-divider {
      height: 100px;
    }

    .about-title {
      font-size: 22px;
    }
  }

</style>
