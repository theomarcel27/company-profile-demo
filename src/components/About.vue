<template>
  <section
    id="about"
    class="relative bg-slate-50 py-20 md:py-28"
  >
    <div class="max-w-screen-2xl mx-auto px-6 md:px-10 lg:px-16">
      <!-- Heading -->
      <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-6 mb-16">
        <div>
          <p class="text-xs font-semibold tracking-[0.25em] text-yellow-500 uppercase mb-2">
            About
          </p>
          <h2 class="text-2xl md:text-3xl font-semibold text-slate-900 leading-snug">
            Firma Hukum dengan Fokus pada Solusi & Hasil
          </h2>
        </div>
        <p class="max-w-xl text-sm md:text-base text-slate-600">
          Prosperity Law Firm mendampingi perusahaan dan individu dengan solusi hukum
          strategis di bidang korporasi, kepailitan, dan litigasi, membantu Anda menavigasi
          dinamika bisnis dan regulasi Indonesia dengan percaya diri.
        </p>
      </div>

      <!-- Cards 2x2 -->
      <div class="grid sm:grid-cols-2 gap-6">
        <!-- Card 1 -->
        <div class="group bg-white rounded-2xl p-6 border border-slate-100 shadow-md hover:-translate-y-2 hover:shadow-lg transition duration-300 flex items-start gap-4">
          <AcademicCapIcon class="w-10 h-10 text-yellow-500 flex-shrink-0"/>
          <div>
            <h3 class="text-sm font-semibold text-slate-900 mb-1">Spesialisasi Korporasi & Kepailitan</h3>
            <p class="text-xs text-slate-600 leading-relaxed">
              Fokus pada hukum bisnis, restrukturisasi, dan penyelamatan usaha yang berkelanjutan.
            </p>
          </div>
        </div>

        <!-- Card 2 -->
        <div class="group bg-white rounded-2xl p-6 border border-slate-100 shadow-md hover:-translate-y-2 hover:shadow-lg transition duration-300 flex items-start gap-4">
          <ChartBarIcon class="w-10 h-10 text-blue-500 flex-shrink-0"/>
          <div>
            <h3 class="text-sm font-semibold text-slate-900 mb-1">Pendekatan Analitis & Strategis</h3>
            <p class="text-xs text-slate-600 leading-relaxed">
              Setiap perkara ditangani dengan riset mendalam dan strategi yang disesuaikan dengan target klien.
            </p>
          </div>
        </div>

        <!-- Card 3 -->
        <div class="group bg-white rounded-2xl p-6 border border-slate-100 shadow-md hover:-translate-y-2 hover:shadow-lg transition duration-300 flex items-start gap-4">
          <HandThumbUpIcon class="w-10 h-10 text-emerald-500 flex-shrink-0"/>
          <div>
            <h3 class="text-sm font-semibold text-slate-900 mb-1">Berorientasi pada Klien</h3>
            <p class="text-xs text-slate-600 leading-relaxed">
              Komunikasi transparan di setiap tahap agar keputusan hukum selaras dengan tujuan klien.
            </p>
          </div>
        </div>

        <!-- Card 4 -->
        <div class="group bg-white rounded-2xl p-6 border border-slate-100 shadow-md hover:-translate-y-2 hover:shadow-lg transition duration-300 flex items-start gap-4">
          <ShieldCheckIcon class="w-10 h-10 text-slate-700 flex-shrink-0"/>
          <div>
            <h3 class="text-sm font-semibold text-slate-900 mb-1">Solusi Jangka Panjang</h3>
            <p class="text-xs text-slate-600 leading-relaxed">
              Tidak hanya menyelesaikan sengketa, tetapi juga melindungi dan menguatkan posisi hukum bisnis Anda.
            </p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { AcademicCapIcon, ChartBarIcon, HandThumbUpIcon, ShieldCheckIcon } from '@heroicons/vue/24/solid'
</script>
