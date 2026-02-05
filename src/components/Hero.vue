<template>
  <section
    id="hero"
    class="relative min-h-[80vh] flex items-center text-white overflow-hidden"
  >

    <!-- Background Image -->
    <div class="absolute inset-0">
      <img
        src="/images/office-building.jpg"
        alt="Prosperity Law Firm Office"
        class="w-full h-full object-cover scale-105"
      />
      <!-- Dark cinematic gradient -->
      <div class="absolute inset-0 bg-gradient-to-br from-slate-950/90 via-slate-900/80 to-slate-900/60"></div>
    </div>

    <!-- Glow accents -->
    <div class="absolute -top-32 -left-32 w-[500px] h-[500px] bg-yellow-400/10 rounded-full blur-3xl"></div>
    <div class="absolute top-1/2 -right-32 w-[500px] h-[500px] bg-blue-500/10 rounded-full blur-3xl"></div>

    <!-- Content -->
    <div class="relative max-w-screen-2xl mx-auto px-6 md:px-10 lg:px-16 pt-32 pb-24">

      <div class="max-w-4xl animate-fade">

        <!-- Badge / Label -->
        <div class="inline-flex items-center gap-2 mb-6 px-4 py-2 rounded-full bg-white/10 border border-white/20 backdrop-blur text-xs tracking-wider uppercase text-yellow-300">
          ⚖ Prosperity Law Firm
        </div>

        <!-- Headline -->
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-semibold leading-tight mb-6">
          Mitra Hukum Tepercaya<br class="hidden md:block" />
          <span class="text-yellow-300">untuk Bisnis & Individu</span>
        </h1>

        <!-- Description -->
        <p class="text-lg text-slate-200/90 mb-10 leading-relaxed">
          Memberikan solusi hukum strategis dan profesional dengan spesialisasi di hukum korporasi,
          kepailitan, dan litigasi. Didukung tim advokat berpengalaman yang siap mendampingi setiap
          langkah hukum Anda.
        </p>

        <!-- Buttons -->
        <div class="flex flex-wrap gap-5">

          <a
            href="#contact"
            class="group inline-flex items-center gap-2 px-8 py-4 rounded-full bg-yellow-400 text-slate-900 font-semibold text-sm shadow-lg hover:bg-yellow-300 transition duration-300"
          >
            Jadwalkan Konsultasi
            <span class="group-hover:translate-x-1 transition">→</span>
          </a>

          <a
            href="#services"
            class="inline-flex items-center gap-2 px-8 py-4 rounded-full border border-white/40 text-sm font-medium hover:bg-white/10 backdrop-blur transition duration-300"
          >
            Lihat Layanan
          </a>

        </div>

      </div>

    </div>
  </section>
</template>

<style scoped>
/* Simple fade-in animation for hero content */
.animate-fade {
  animation: fadeUp 0.9s ease-out both;
}

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>