<template>
  <section class="hero" ref="heroRef" id="hero">

    <!-- background -->
    <img src="/images/gambarGedung2.jpg" class="hero-bg" />

    <!-- left panel -->
    <div class="hero-left"></div>

    <!-- accent line -->
    <div class="accent-line"></div>

    <!-- content -->
    <div class="hero-content">
      <div class="inner">

        <h1 class="brand">
          <span class="brand-top">PROSPERITY</span>
          <span class="brand-bottom">LAW FIRM</span>
        </h1>

        <p class="tagline">
          Mitra Hukum Tepercaya<br>
          untuk Bisnis & Individu
        </p>

        <div class="cta-group">
          <a href="#contact" class="btn-primary">Consult Now</a>
          <a href="#about" class="btn-outline">Learn More</a>
        </div>

      </div>
    </div>

  </section>
</template>

<script setup>
  import { ref, onMounted, onUnmounted } from 'vue'

  const heroRef = ref(null)

  const handleScroll = () => {
    if (!heroRef.value) return
    const y = window.scrollY
    heroRef.value.style.setProperty('--parallax-y', y * 0.20 + 'px')
  }

  onMounted(() => {
    window.addEventListener('scroll', handleScroll)
  })

  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
  })
</script>

<style scoped>
  .hero {
    position: relative;
    min-height: 90vh;
    overflow: hidden;
    color: white;
    scroll-margin-top: 95px;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 140%;
    object-fit: cover;
    transform: translateY(calc(var(--parallax-y, 0px) * -1));
    transition: transform 0.12s linear;
    filter: brightness(0.75);
    z-index: 0;
    will-change: transform;
  }

  .hero-left {
    position: absolute;
    top: 0;
    left: 0;
    width: 48%;
    height: 100%;
    background: linear-gradient(
      135deg,
    #16213ecb 55%,
    #1e2f55c5 100%
    );
    z-index: 1;
  }

  .accent-line {
    position: absolute;
    top: 0;
    left: 48%;
    width: 3px;
    height: 100%;
    background: linear-gradient(to bottom, #d4af379d, #f6d46586);
    z-index: 2;
    animation: glowLine 3s ease-in-out infinite alternate;
  }

  @keyframes glowLine {
    from { filter: brightness(1); }
    to { filter: brightness(1.4); }
  }

  .hero-content {
    position: relative;
    z-index: 3;
    min-height: 90vh;
    display: flex;
    align-items: center;
  }

  .inner {
    padding: 70px;
    max-width: 640px;
    animation: heroReveal 1s ease-out both;
  }

  /* ========= BRAND TITLE ========= */
  .brand {
    margin-bottom: 26px;
    line-height: 1.05;
  }

  .brand-top {
    display: block;
    font-size: 58px;
    font-weight: 800;
    letter-spacing: 2px;
    text-shadow: 0 6px 24px rgba(0,0,0,0.35);
  }

  .brand-bottom {
    display: block;
    font-size: 30px;
    font-weight: 600;
    letter-spacing: 5px;
    color: #d4af37;
    margin-top: 6px;
  }

  /* ========= TAGLINE ========= */
  .tagline {
    font-size: 20px;
    opacity: 0.92;
    color: #dbeafe;
  }

  .cta-group {
    margin-top: 34px;
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }

  .btn-primary {
    background: linear-gradient(135deg, #d4af37, #f6d465);
    color: #1e293b;
    padding: 10px 20px;
    border-radius: 10px;
    font-weight: 700;
    letter-spacing: 0.5px;
    text-decoration: none;
    transition: all 0.25s ease;
    box-shadow: 0 10px 30px rgba(0,0,0,0.25);
  }

  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.35);
    filter: brightness(1.05);
  }

  .btn-outline {
    border: 2px solid rgba(255,255,255,0.7);
    color: white;
    padding: 10px 20px;
    border-radius: 10px;
    font-weight: 600;
    text-decoration: none;
    transition: all 0.25s ease;
    backdrop-filter: blur(4px);
  }

  .btn-outline:hover {
    background: rgba(255,255,255,0.12);
    transform: translateY(-3px);
  }


  /* ========= REVEAL ANIMATION ========= */
  @keyframes heroReveal {
    from {
      opacity: 0;
      transform: translateY(40px) scale(0.98);
    }
    to {
      opacity: 1;
      transform: translateY(0) scale(1);
    }
  }

  /* ========= RESPONSIVE ========= */
  @media (max-width: 768px) {
    .hero {
      min-height: 65vh;
    }

    .hero-content {
      min-height: 65vh;
    }

    .hero-bg {
      height: 130%;
    }

    .hero-left {
      width: 100%;
    }

    .accent-line {
      display: none;
    }

    .inner {
      padding: 40px;
    }

    .brand-top {
      font-size: 42px;
    }

    .brand-bottom {
      font-size: 22px;
      letter-spacing: 4px;
    }

    .tagline {
      font-size: 16px;
    }
  }
</style>
