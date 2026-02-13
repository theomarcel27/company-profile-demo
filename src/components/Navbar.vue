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

      <!-- Desktop Menu -->
      <nav class="menu">
        <a href="#hero" :class="{active: activeSection==='hero'}">Home</a>
        <a href="#about" :class="{active: activeSection==='about'}">About</a>
        <a href="#services" :class="{active: activeSection==='services'}">Services</a>
        <a href="#team" :class="{active: activeSection==='team'}">Team</a>
        <a href="#contact" :class="{active: activeSection==='contact'}">Contact</a>
      </nav>

      <!-- Hamburger Animated -->
      <button
        class="hamburger"
        :class="{ active: open }"
        @click="open = !open"
        aria-label="menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

    </div>

    <!-- Overlay -->
    <Transition name="fade">
      <div v-if="open" class="overlay" @click="open=false"></div>
    </Transition>

    <!-- Mobile Panel -->
    <Transition name="mobile-menu">
      <div v-if="open" class="mobile-panel">
        <nav>
          <a @click="open=false" href="#hero" :class="{active: activeSection==='hero'}">Home</a>
          <a @click="open=false" href="#about" :class="{active: activeSection==='about'}">About</a>
          <a @click="open=false" href="#services" :class="{active: activeSection==='service'}">Services</a>
          <a @click="open=false" href="#team" :class="{active: activeSection==='team'}">Team</a>
          <a @click="open=false" href="#contact" :class="{active: activeSection==='contact'}">Contact</a>
        </nav>
      </div>
    </Transition>

  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watch } from "vue"

const open = ref(false)
const headerRef = ref(null)
const activeSection = ref("hero")

const sections = ["hero","about","services","team","contact"]

/* click outside close */
const handleClickOutside = (e) => {
  if (!open.value) return
  if (headerRef.value && !headerRef.value.contains(e.target)) {
    open.value = false
  }
}

/* lock scroll when menu open */
watch(open, (v) => {
  document.body.style.overflow = v ? "hidden" : ""
})

onMounted(() => {
  document.addEventListener("click", handleClickOutside)

  /* 👉 SCROLL SPY OBSERVER */
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        activeSection.value = e.target.id
      }
    })
  },{
    rootMargin: "-40% 0px -50% 0px",
    threshold: 0
  })

  sections.forEach(id => {
    const el = document.getElementById(id)
    if (el) obs.observe(el)
  })
})

onUnmounted(() => {
  document.removeEventListener("click", handleClickOutside)
})
</script>

<style scoped>
/* ================= HEADER ================= */

.site-header {
  position: sticky;
  top: 0;
  z-index: 80;
  backdrop-filter: blur(12px);
  background: rgba(255,255,255,.88);
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

/* ================= LOGO ================= */

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

/* ================= DESKTOP MENU ================= */

.menu {
  display: none;
  gap: 34px;
  font-weight: 500;
}

.menu a {
  position: relative;
  color: #334155;
  text-decoration: none;
  transition: .25s;
}

/* gold underline grow */
.menu a::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -6px;
  width: 0;
  height: 2px;
  background: linear-gradient(to right,#d4af37,#f6d465);
  transition: .25s;
}

.menu a:hover { 
  color: #1d4ed8; 
}

.menu a:hover::after {
  width: 100%;
}

.menu a.active {
  color: #1d4ed8;
}

.menu a.active::after {
  width: 100%;
}

/* ================= HAMBURGER ================= */

.hamburger {
  width: 30px;
  height: 22px;
  position: relative;
  background: none;
  border: none;
  cursor: pointer;
  z-index: 90;
}

.hamburger span {
  position: absolute;
  left: 0;
  width: 100%;
  height: 3px;
  background: #0f172a;
  border-radius: 2px;
  transition: .35s;
}

.hamburger span:nth-child(1){ top:0 }
.hamburger span:nth-child(2){ top:9px }
.hamburger span:nth-child(3){ bottom:0 }

.hamburger.active span:nth-child(1){
  transform: rotate(45deg);
  top:9px;
}

.hamburger.active span:nth-child(2){
  opacity:0;
}

.hamburger.active span:nth-child(3){
  transform: rotate(-45deg);
  bottom:10px;
}

/* ================= MOBILE PANEL ================= */

.mobile-panel {
  position: fixed;
  top: 72px;
  left: 0;
  right: 0;
  background: rgba(255,255,255,.96);
  backdrop-filter: blur(14px);
  border-bottom: 1px solid #e5e7eb;
  box-shadow: 0 24px 70px rgba(0,0,0,.15);
  z-index: 85;
}

.mobile-panel nav {
  display: flex;
  flex-direction: column;
  padding: 28px;
  gap: 20px;
  font-weight: 600;
}

.mobile-panel a {
  color: #334155;
  text-decoration: none;
  font-size: 16px;
  transition: .2s;
}

.mobile-panel a:hover {
  color: #92400e;
  padding-left: 6px;
}

.mobile-panel a.active {
  color: #1d4ed8;
  padding-left: 6px;
}

/* ================= OVERLAY ================= */

.overlay {
  position: fixed;
  inset: 0;
  background: rgba(2,6,23,.35);
  backdrop-filter: blur(3px);
  z-index: 70;
}

/* ================= TRANSITIONS ================= */

.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all .35s cubic-bezier(.22,.8,.2,1);
}

.mobile-menu-enter-from {
  opacity: 0;
  transform: translateY(-20px) scale(.98);
}

.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-12px) scale(.98);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .25s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* ================= RESPONSIVE ================= */

@media (min-width: 768px) {
  .menu { display: flex; }
  .hamburger { display: none; }
}
</style>
