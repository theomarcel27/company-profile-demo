<template>
<section id="team" class="team" ref="teamRef">

  <div class="container">

    <!-- HEAD -->
    <div class="head">
      <h2>OUR TEAM</h2>
      <p>
        Tim profesional dengan keahlian multidisiplin dan pengalaman praktis
        dalam hukum korporasi, perpajakan, dan litigasi.
      </p>
    </div>

    <!-- ===== MANAGING PARTNER SPOTLIGHT ===== -->
    <div class="mp-card" :class="show ? 'show' : ''">
      <div class="mp-photo-wrap">
        <img :src="managing.photo"
             :style="{ objectPosition: managing.pos }"
             class="mp-photo">
      </div>

      <div class="mp-info">
        <span class="role">{{ managing.role }}</span>
        <h3>{{ managing.name }}</h3>
        <p class="mp-bio">{{ managing.bio }}</p>
      </div>
    </div>

    <!-- ===== OTHER MEMBERS ===== -->
    <div class="grid">

      <div
        class="member"
        v-for="(m,i) in others"
        :key="m.name"
        :class="[
          i === 0 ? 'from-left' :
          i === 1 ? 'from-bottom' :
          'from-right',
          show ? 'show' : ''
        ]"
      >
        <img :src="m.photo"
             :style="{ objectPosition: m.pos }"
             class="photo" />

        <div class="info">
          <span class="role">{{ m.role }}</span>
          <h3>{{ m.name }}</h3>
          <p class="bio">{{ m.bio }}</p>
        </div>
      </div>

    </div>

  </div>
</section>
</template>

<script setup>
import { ref, onMounted, computed } from "vue"

const members = [
  {
    role: "Managing Partner",
    name: "Calvin Pratama, S.H., M.Kn.",
    photo: "images/teams/cowo1.jpg",
    pos: "center 30%",
    bio: "Calvin Pratama, S.H., M.Kn. adalah Managing Partner Prosperity Law Firm dengan fokus utama pada hukum korporasi dan perdata. Lulusan Sarjana Hukum dan Magister Kenotariatan Universitas Airlangga ini dikenal memiliki fondasi akademik kuat yang berpadu dengan pengalaman praktis tingkat tinggi.Sebelum mendirikan firma, ia memegang posisi strategis sebagai Head of Legal & Corporate Secretary di beberapa grup perusahaan nasional besar, menangani strategi hukum korporasi, kepatuhan regulasi, manajemen risiko, dan tata kelola perusahaan. Dengan pendekatan yang presisi, strategis, dan berorientasi solusi, Calvin memimpin firma untuk memberikan layanan hukum yang bernilai tambah, terpercaya, dan berkelanjutan bagi setiap klien."
  },
  {
    role: "Senior Partner",
    name: "Theodora Rotua Batubara, S.H., S.E., M.Si",
    photo: "images/teams/cowo2.jpg",
    pos: "center 5%",
    bio: "Theodora Rotua Batubara adalah profesional multidisipliner di bidang hukum, akuntansi, dan perpajakan dengan pengalaman lebih dari 15 tahun. Berpengalaman menangani pemeriksaan, keberatan, dan sengketa pajak hingga tingkat banding. Pemegang sertifikasi Kuasa Hukum Pajak & Konsultan Pajak IKPI, advokat (PERADIc, AAI, IKADIN), serta tersertifikasi sebagai Mediator, Likuidator, Auditor, dan Kurator."
  },
  {
    role: "Junior Associate",
    name: "Najla Fernanda Rizanty, S.H.",
    photo: "images/teams/cewe1.jpg",
    pos: "center 40%",
    bio: "Najla Fernanda Rizanty adalah lulusan Sarjana Hukum Universitas Brawijaya (2023), telah menyelesaikan PKPA dan UPA, serta bersertifikasi Certified Contract Drafter (BNSP). Berpengalaman dalam penanganan perkara litigasi dan non-litigasi serta pendampingan hukum korporasi. Fokus pada Corporate Law dan Manpower Law, dengan keahlian drafting dan review kontrak, perjanjian komersial, serta dokumen hukum perusahaan."
  },
  {
    role: "Junior Associate",
    name: "Adrian Ramdani Pardomuan, S.H.",
    photo: "images/teams/cowo3.jpg",
    pos: "center 5%",
    bio: "Adrian Ramdani Pardomuan adalah lulusan Sarjana Hukum Universitas Jenderal Soedirman dengan pengalaman menangani perkara pidana, perdata, dan korporasi. Terlibat dalam konsultasi, pendampingan, serta perumusan strategi hukum untuk klien individu dan perusahaan. Aktif di bidang non-litigasi, termasuk pendirian PT, perizinan usaha, serta pendaftaran merek dan hak kekayaan intelektual. Dikenal dengan pendekatan analitis dan solusi hukum yang praktis serta berorientasi hasil."
  }
]

const managing = members[0]
const others = computed(() => members.slice(1))

const teamRef = ref(null)
const show = ref(false)

onMounted(() => {
  const obs = new IntersectionObserver(
    ([e]) => { if (e.isIntersecting) show.value = true },
    { threshold: 0.3 }
  )
  obs.observe(teamRef.value)
})
</script>

<style scoped>

.team {
  position: relative;
  padding: 70px 0;
  background:
    radial-gradient(circle at 20% 10%, rgba(212,175,55,.08), transparent 40%),
    radial-gradient(circle at 80% 90%, rgba(212,175,55,.06), transparent 45%),
    linear-gradient(to bottom,#f8fafc,#eef2f7,#e7ecf3);
}

/* subtle pattern */

.team::after {
  content:"";
  position:absolute;
  inset:0;
  background-image:
    linear-gradient(rgba(15,23,42,.05) 1px, transparent 1px),
    linear-gradient(90deg, rgba(15,23,42,.05) 1px, transparent 1px);
  background-size:40px 40px;
  pointer-events:none;
}

.container {
  max-width: 1200px;
  margin: auto;
  padding: 0 16px;
  position: relative;
  z-index: 2;
}

/* ===== HEAD ===== */

.head {
  text-align: center;
  max-width: 760px;
  margin: 0 auto 56px;
}

.head h2 {
  font-size: 36px;
  color: #0f172a;
}

.head h2::after {
  content:"";
  display:block;
  width:70px;
  height:3px;
  margin:12px auto 0;
  background:linear-gradient(to right,#d4af37,#f6d465);
  border-radius:3px;
}

.head p {
  color:#475569;
  font-size:17px;
  line-height:1.7;
}

/* ================= MP CARD ================= */

.mp-card {
  position: relative;
  display:grid;
  grid-template-columns: 420px 1fr;
  gap: 42px;
  background:white;
  border-radius:22px;
  padding:30px;
  border:1px solid #e5e7eb;
  box-shadow:0 30px 90px rgba(15,23,42,.14);
  margin-bottom:60px;

  opacity:0;
  transform:translateY(70px) scale(.97);
  transition:.9s cubic-bezier(.2,.8,.2,1);
  overflow:hidden;
}

.mp-card::before {
  content:"";
  position:absolute;
  inset:0 0 auto 0;
  height:4px;
  background: linear-gradient(to right,#d4af37,#f6d465);
}

.mp-card.show {
  opacity:1;
  transform:none;
}

.mp-photo {
  width:100%;
  height:400px;
  object-fit:cover;
  border-radius:18px;
  background:#e5e7eb;
  transition: transform .6s ease;
}

.mp-info h3 {
  font-size:26px;
  margin:10px 0 16px;
  color:#0f172a;
}

.mp-bio {
  color:#475569;
  line-height:1.85;
  font-size:15px;
  text-align:justify;
}

/* ================= GRID ================= */

.grid {
  max-width: 1100px;      /* samakan rasa lebarnya */
  margin: 0 auto;
  display:grid;
  gap:26px;
  grid-template-columns: 1fr;   /* mobile dulu */
}

/* tablet */

@media (min-width: 640px) {
  .grid {
    grid-template-columns: 1fr 1fr;
  }
}

/* desktop */

@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(3,1fr);
  }
}

/* ================= MEMBER ================= */

.member {
  position: relative;
  background:white;
  border-radius:18px;
  overflow:hidden;
  border:1px solid #e5e7eb;
  box-shadow:0 18px 50px rgba(15,23,42,.09);
  transition:all .45s cubic-bezier(.2,.8,.2,1);
  opacity:0;
  filter: blur(6px);
}

/* subtle gold corner glow */
.member::before {
  content:"";
  position:absolute;
  inset:-1px;
  background: linear-gradient(120deg, transparent, rgba(212,175,55,.25));
  opacity:0;
  transition:.4s;
}

.member:hover {
  transform: translateY(-10px) scale(1.015);
  box-shadow:0 36px 100px rgba(15,23,42,.18);
}


/* entrance directions */

.member.from-left { transform: translateX(-90px); }
.member.from-right { transform: translateX(90px); }
.member.from-bottom { transform: translateY(90px); }

.member.show {
  opacity:1;
  transform:none;
  filter: blur(0);
}

/* stagger */

.member.show:nth-child(1){ transition-delay:.15s }
.member.show:nth-child(2){ transition-delay:.30s }
.member.show:nth-child(3){ transition-delay:.45s }


/* content */

.photo {
  width:100%;
  height:250px;
  object-fit:cover;
  background:#f1f5f9;
  transition: transform .5s ease;
}

.info {
  padding:20px;
  text-align:center;
}

.role {
  font-size:11px;
  letter-spacing:.2em;
  text-transform:uppercase;
  background: linear-gradient(to right,#fef3c7,#fde68a);
  color:#92400e;
  padding:7px 14px;
  border-radius:999px;
  font-weight:700;
  box-shadow: inset 0 1px 0 rgba(255,255,255,.7);
}

.info h3 {
  margin:10px 0 6px;
  font-size:16px;
  color:#0f172a;
}

.bio {
  font-size:14px;
  color:#64748b;
  line-height:1.6;
  text-align: justify;
}

/* ================= MOBILE MP FIX ================= */

@media (max-width: 900px) {
  .mp-card {
    grid-template-columns:1fr;
    padding:20px;
    gap:20px;
  }

  .mp-photo {
    height:300px;
  }

  .mp-info h3 {
    font-size:20px;
  }

  .mp-bio {
    font-size:14px;
  }
}

</style>
