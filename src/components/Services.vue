<template>
  <section id="services" class="services">
    <div class="container">

      <!-- HEAD -->
      <div class="head">
        <h2>OUR SERVICES</h2>
        <p class="sub">
          Layanan hukum strategis untuk korporasi dan individu
          dengan pendekatan terukur dan berorientasi hasil.
        </p>
      </div>

      <!-- GRID -->
      <div class="grid">
        <div class="card" v-for="s in services" :key="s.title">
          <component :is="s.icon" class="icon"/>
          <h3>{{ s.title }}</h3>
          <p>{{ s.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  BuildingOfficeIcon,
  ScaleIcon,
  ShieldExclamationIcon,
  DocumentTextIcon,
  BanknotesIcon,
  UserGroupIcon,
  BriefcaseIcon,
  HandRaisedIcon
} from '@heroicons/vue/24/solid'

const services = [
  {
    title: "Corporate & Commercial Law",
    desc: "Pendirian perusahaan, perjanjian komersial, dan kepatuhan regulasi.",
    icon: BuildingOfficeIcon
  },
  {
    title: "Dispute Resolution",
    desc: "Negosiasi, mediasi, arbitrase, dan penyelesaian sengketa.",
    icon: ScaleIcon
  },
  {
    title: "Criminal Defence",
    desc: "Pendampingan perkara pidana individu dan korporasi.",
    icon: ShieldExclamationIcon
  },
  {
    title: "Litigation",
    desc: "Representasi klien di seluruh tingkat peradilan.",
    icon: DocumentTextIcon
  },
  {
    title: "Bankruptcy & PKPU",
    desc: "Kepailitan dan restrukturisasi utang.",
    icon: BanknotesIcon
  },
  {
    title: "Family Law",
    desc: "Perceraian dan perkara keluarga.",
    icon: UserGroupIcon
  },
  {
    title: "Labour Law",
    desc: "Perjanjian kerja dan sengketa industrial.",
    icon: BriefcaseIcon
  },
  {
    title: "Non-Litigation",
    desc: "Legal opinion, due diligence, drafting dokumen.",
    icon: HandRaisedIcon
  }
]
</script>

<style scoped>
.services {
  position: relative;
  padding: 50px 0 80px;
  background: linear-gradient(
    to bottom,
    #0f172a 0%,
    #16213e 55%,
    #1e2f55 100%
  );
  color: white;
  scroll-margin-top: 120px;
  overflow: hidden;
}

/* ===== smooth blend from about wave ===== */

.services::before {
  content: "";
  position: absolute;
  top: -60px;
  left: 0;
  width: 100%;
  height: 120px;
  background: linear-gradient(
    to bottom,
    rgba(15,23,42,0),
    rgba(15,23,42,0.85)
  );
  pointer-events: none;
}

/* ===== container ===== */

.container {
  max-width: 1200px;
  margin: auto;
  padding: 0 24px;
  position: relative;
  z-index: 2;
}

/* ===== head ===== */

.head {
  text-align: center;
  max-width: 760px;
  margin: 0 auto 60px;
}

.head h2 {
  font-size: 40px;
  margin-bottom: 14px;
  position: relative;
  letter-spacing: .02em;
}

.head h2::after {
  content: "";
  display: block;
  width: 80px;
  height: 3px;
  margin: 18px auto 0;
  background: linear-gradient(to right,#d4af37,#f6d465);
  border-radius: 3px;
}

.sub {
  color: #94a3b8;
  line-height: 1.7;
  font-size: 17px;
}

/* ===== grid ===== */

.grid {
  display: grid;
  gap: 26px;
}

@media (min-width: 700px) {
  .grid {
    grid-template-columns: 1fr 1fr;
  }
}

/* ===== card ===== */

.card {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.10);
  border-radius: 18px;
  padding: 26px;
  transition: all .35s ease;
  position: relative;
  overflow: hidden;
  backdrop-filter: blur(2px);
  animation: cardIn .6s ease both;
}

/* gold hover sweep */
.card::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    120deg,
    transparent,
    rgba(212,175,55,.14)
  );
  opacity: 0;
  transition: .35s;
}

.card:hover {
  transform: translateY(-10px);
  background: rgba(255,255,255,0.09);
  border-color: rgba(212,175,55,0.35);
}

.card:hover::after {
  opacity: 1;
}

/* ===== icon ===== */

.icon {
  width: 30px;
  height: 30px;
  color: #d4af37;
  background: rgba(212,175,55,0.14);
  padding: 6px;
  border-radius: 10px;
  margin-bottom: 14px;
  box-shadow: 0 4px 16px rgba(212,175,55,0.15);
}

/* ===== text ===== */

.card h3 {
  font-size: 18px;
  margin-bottom: 8px;
  color: #f8fafc;
  font-weight: 700;
  letter-spacing: .01em;
}

.card p {
  font-size: 15px;
  color: #94a3b8;
  line-height: 1.65;
}

/* ===== reveal anim ===== */

@keyframes cardIn {
  from {
    opacity: 0;
    transform: translateY(28px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* ===== mobile ===== */

@media (max-width: 768px) {
  .services {
    padding: 70px 0 60px;
  }

  .head h2 {
    font-size: 26px;
  }

  .sub {
    font-size: 15px;
  }
}

</style>
