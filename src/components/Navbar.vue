<template>
  <header class="site-header" ref="headerRef">
    <div class="wrap">

      <!-- Logo -->
      <div class="logo">
        <span class="logo-bar"></span>
        <div class="logo-text">
          <span class="logo-top">PROSPERITY</span>
          <span class="logo-bottom">LAW FIRM</span>
        </div>
      </div>

      <!-- Menu Desktop -->
      <nav class="menu">
        <a href="#hero">Home</a>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#team">Team</a>
        <a href="#contact">Contact</a>
      </nav>

      <!-- Hamburger -->
      <button class="hamburger" @click="open = !open">
        ☰
      </button>

    </div>

    <!-- Mobile -->
    <Transition name="mobile-menu">
      <div v-if="open" class="mobile-panel">
        <nav>
          <a @click="open=false" href="#hero">Home</a>
          <a @click="open=false" href="#about">About</a>
          <a @click="open=false" href="#services">Services</a>
          <a @click="open=false" href="#team">Team</a>
          <a @click="open=false" href="#contact">Contact</a>
        </nav>
      </div>
    </Transition>

  </header>
</template>


<script setup>
  import { ref, onMounted, onUnmounted } from 'vue'

  const open = ref(false)
  const headerRef = ref(null)

  const handleClickOutside = (e) => {
    if (!open.value) return

    if (headerRef.value && !headerRef.value.contains(e.target)) {
      open.value = false
    }
  }

  onMounted(() => {
    document.addEventListener('click', handleClickOutside)
  })

  onUnmounted(() => {
    document.removeEventListener('click', handleClickOutside)
  })
</script>

<style scoped>
  .site-header {
    position: sticky;
    top: 0;
    z-index: 50;
    backdrop-filter: blur(10px);
    background: rgba(255,255,255,0.9);
    border-bottom: 1px solid #e5e7eb;
  }

  .wrap {
    max-width: 1200px;
    margin: auto;
    padding: 18px 28px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  /* ===== LOGO ===== */

  .logo {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .logo-bar {
    width: 4px;
    height: 36px;
    background: linear-gradient(#d4af37,#f6d365);
    border-radius: 2px;
  }

  .logo-text {
    line-height: 1.05;
  }

  .logo-top {
    display: block;
    font-size: 15px;
    letter-spacing: .18em;
    font-weight: 700;
  }

  .logo-bottom {
    display: block;
    font-size: 11px;
    letter-spacing: .35em;
    color: #64748b;
  }

  /* ===== MENU DESKTOP ===== */

  .menu {
    display: none;
    gap: 34px;
    font-weight: 500;
  }

  .menu a {
    position: relative;
    color: #334155;
    text-decoration: none;
  }

  /* underline grow effect */
  .menu a::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: -6px;
    width: 0;
    height: 2px;
    background: #1d4ed8;
    transition: .25s;
  }

  .menu a:hover::after {
    width: 100%;
  }

  .menu a:hover {
    color: #1d4ed8;
  }

  /* ===== HAMBURGER ===== */

  .hamburger {
    font-size: 24px;
    background: none;
    border: none;
    cursor: pointer;
  }

  /* ===== MOBILE ===== */

  .mobile-panel {
    background: white;
    border-top: 1px solid #e5e7eb;
    box-shadow: 0 12px 30px rgba(0,0,0,0.08);
  }

  .mobile-panel nav {
    display: flex;
    flex-direction: column;
    padding: 26px;
    gap: 18px;
    font-weight: 500;
  }

  .mobile-panel a {
    color: #334155;
  }


  /* ===== TRANSITION ===== */

  .mobile-menu-enter-active,
  .mobile-menu-leave-active {
    transition: all .25s ease;
  }

  .mobile-menu-enter-from,
  .mobile-menu-leave-to {
    opacity: 0;
    transform: translateY(-12px);
  }

  /* ===== RESPONSIVE ===== */

  @media (min-width: 768px) {
    .menu { display: flex; }
    .hamburger { display: none; }
  }
</style>
