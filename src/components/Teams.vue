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

    <!-- ===== MANAGING PARTNER ===== -->
    <div class="mp-card" :class="{ show }">
      <div>
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
          dirClass(i),
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
    bio: "Managing Partner dengan fokus hukum korporasi dan perdata. Memiliki latar belakang Sarjana Hukum dan Magister Kenotariatan serta pengalaman strategis sebagai Head of Legal & Corporate Secretary di grup perusahaan nasional. Berpengalaman dalam strategi hukum korporasi, kepatuhan regulasi, manajemen risiko, dan tata kelola perusahaan."
  },
  {
    role: "Senior Partner",
    name: "Theodora Rotua Batubara, S.H., S.E., M.Si",
    photo: "images/teams/cowo2.jpg",
    pos: "center 5%",
    bio: "Profesional multidisipliner di bidang hukum, akuntansi, dan perpajakan dengan pengalaman lebih dari 15 tahun. Menangani pemeriksaan hingga sengketa pajak tingkat banding. Pemegang sertifikasi Kuasa Hukum Pajak, Konsultan Pajak, Advokat, Mediator, Likuidator, Auditor, dan Kurator."
  },
  {
    role: "Junior Associate",
    name: "Najla Fernanda Rizanty, S.H.",
    photo: "images/teams/cewe1.jpg",
    pos: "center 40%",
    bio: "Lulusan Sarjana Hukum, telah menyelesaikan PKPA dan UPA serta bersertifikasi Certified Contract Drafter (BNSP). Berpengalaman di litigasi dan non-litigasi, pendampingan korporasi, drafting dan review kontrak serta dokumen hukum perusahaan."
  },
  {
    role: "Junior Associate",
    name: "Adrian Ramdani Pardomuan, S.H.",
    photo: "images/teams/cowo3.jpg",
    pos: "center 5%",
    bio: "Konsultan hukum dengan pengalaman perkara pidana, perdata, dan korporasi. Aktif di bidang non-litigasi termasuk pendirian PT, perizinan usaha, dan HKI. Dikenal dengan pendekatan analitis dan solusi hukum yang praktis serta berorientasi hasil."
  }
]

const managing = members[0]
const others = computed(() => members.slice(1))

const teamRef = ref(null)
const show = ref(false)

const dirClass = (i) => {
  if (i === 0) return "from-left"
  if (i === 1) return "from-bottom"
  return "from-right"
}

onMounted(() => {
  const obs = new IntersectionObserver(
    ([e]) => { if (e.isIntersecting) show.value = true },
    {
      threshold: 0.12,
      rootMargin: "0px 0px -10% 0px"
    }
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

/* HEAD */

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

/* MP CARD */

.mp-card {
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
  transform:translateY(60px) scale(.97);
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
}

.mp-info h3 {
  font-size:26px;
  margin:10px 0 16px;
}

.mp-bio {
  line-height:1.85;
  font-size:15px;
  text-align:justify;
  color:#475569;
}

/* GRID */

.grid {
  width: 100%;
  display:grid;
  gap:26px;
  grid-template-columns: 1fr;
}

@media (min-width: 640px) {
  .grid { grid-template-columns: 1fr 1fr; }
}

@media (min-width: 1024px) {
  .grid { grid-template-columns: repeat(3,1fr); }
}

/* MEMBER CARD */

.member {
  background:white;
  border-radius:18px;
  overflow:hidden;
  border:1px solid #e5e7eb;
  box-shadow:0 18px 50px rgba(15,23,42,.09);
  transition:all .45s cubic-bezier(.2,.8,.2,1);
  opacity:0;
  filter: blur(6px);
}

/* entrance */

.member.from-left { transform: translateX(-80px); }
.member.from-right { transform: translateX(80px); }
.member.from-bottom { transform: translateY(80px); }

.member.show {
  opacity:1;
  transform:none;
  filter: blur(0);
}

/* stagger */

.member.show:nth-child(1){ transition-delay:.15s }
.member.show:nth-child(2){ transition-delay:.30s }
.member.show:nth-child(3){ transition-delay:.45s }

/* hover */

.member:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow:0 36px 100px rgba(15,23,42,.18);
}

/* content */

.photo {
  width:100%;
  height:250px;
  object-fit:cover;
}

.info {
  padding:20px;
  text-align:center;
}

.info h3 {
    margin-top: 10px;
    margin-bottom: 10px;   /* jarak ke bio */
    line-height: 1.35;
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
}

.bio {
  font-size:14px;
  color:#64748b;
  line-height:1.6;
  text-align:justify;
}


@media (max-width: 640px) {

  .mp-card {
    grid-template-columns:1fr;
    padding:20px;
    gap:20px;
    margin-bottom: 0px;
  }

  .mp-photo {
    height:300px;
  }

  /* animasi dipendekin biar trigger */
  .member.from-left,
  .member.from-right,
  .member.from-bottom {
    transform: translateY(40px);
  }

  .info {
    padding: 22px 18px 24px;
  }

  .info .role {
    display: inline-block;
    margin-bottom: 12px;   /* jarak ke nama */
  }

  .info h3 {
    margin-top: 6px;
    margin-bottom: 12px;   /* jarak ke bio */
    line-height: 1.35;
  }

  .info .bio {
    margin-top: 8px;
    line-height: 1.7;
  }

}

</style>
