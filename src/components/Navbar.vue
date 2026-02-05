<template>
  <header class="sticky top-0 z-50 bg-white/95 backdrop-blur border-b border-slate-200">
    <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">

      <!-- Logo -->
      <div class="flex items-center gap-2">
        <!-- Bullet kuning kecil -->
        <span class="w-2 h-8 bg-yellow-400 rounded-sm"></span>
        <div class="text-xl font-semibold tracking-wide text-slate-900">
          PROSPERITY LAW FIRM
        </div>
      </div>

      <!-- Menu Desktop -->
      <nav class="hidden md:flex gap-8 font-medium text-slate-700">
        <a href="#hero" class="hover:text-blue-700 transition">Home</a>
        <a href="#about" class="hover:text-blue-700 transition">About</a>
        <a href="#services" class="hover:text-blue-700 transition">Services</a>
        <a href="#team" class="hover:text-blue-700 transition">Team</a>
        <a href="#contact" class="hover:text-blue-700 transition">Contact</a>
      </nav>

      <!-- Hamburger -->
      <button
        class="md:hidden text-2xl text-slate-800"
        @click="open = !open"
      >
        ☰
      </button>

    </div>

    <!-- Mobile Menu -->
    <Transition name="mobile-menu">
        <div
            v-if="open"
            class="md:hidden bg-white border-t shadow-lg"
        >
            <nav class="flex flex-col p-6 gap-4 font-medium">
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
    import { ref } from 'vue'
    const open = ref(false)
</script>

<style scoped>
    .mobile-menu-enter-active,
    .mobile-menu-leave-active {
    transition: all 0.25s ease;
    }

    .mobile-menu-enter-from,
    .mobile-menu-leave-to {
    opacity: 0;
    transform: translateY(-10px);
    }

    .mobile-menu-enter-to,
    .mobile-menu-leave-from {
    opacity: 1;
    transform: translateY(0);
    }
</style>
