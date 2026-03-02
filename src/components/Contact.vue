<script setup>
  import { 
    PhoneIcon, 
    DevicePhoneMobileIcon, 
    EnvelopeIcon 
  } from '@heroicons/vue/24/outline'
</script>

<template>
  <section id="contact" class="contact" ref="teamRef">
    <footer class="footer">

      <div class="container footer-top">

        <div class="footer-left">
          <h2>Digital<br>Solutions</h2>
          <p class="tag">
            Digital & Technology Solutions for Modern Business
          </p>
        </div>

        <div class="footer-links">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#hero">Home</a></li>
            <li><a href="#about">About Us</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#team">Our Team</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>

        <div class="footer-contact">
          <h4>Headquarters</h4> 
          
          <p class="addr">
            The Chancery Building<br>
            5 Chancery Lane, Holborn<br>
            London, WC2A 1LG<br>
            United Kingdom
          </p>

          <div class="contact-list">
            <div class="contact-item">
              <PhoneIcon class="footer-icon" />
              <span>+44 20 7946 0123</span>
            </div>
            <div class="contact-item">
              <DevicePhoneMobileIcon class="footer-icon" />
              <span>+44 7700 900 456</span>
            </div>
            <div class="contact-item">
              <EnvelopeIcon class="footer-icon" />
              <span>contact@professional-portfolio.uk</span>
            </div>
          </div>

          <div class="map">
            <iframe
              loading="lazy"
              allowfullscreen
              referrerpolicy="no-referrer-when-downgrade"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2482.905193427438!2d-0.11357602337626358!3d51.5149302718151!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x48761b4db1369b77%3A0x673960010c7323b9!2s5%20Chancery%20Ln%2C%20London%20WC2A%201LG%2C%20UK!5e0!3m2!1sen!2sid!4v1709350000000!5m2!1sen!2sid">
            </iframe>
          </div>

        </div><!-- footer-contact -->

      </div><!-- container -->

      <div class="footer-bottom">
        © 2026 Professional Portfolio. All rights reserved.
        Digital & Technology Services.
      </div>

    </footer>
  </section>
</template>


<style scoped>

.footer {
  position: relative;
  background:
    radial-gradient(circle at 30% 20%, rgba(255,255,255,.06), transparent 40%),
    radial-gradient(circle at 70% 80%, rgba(212,175,55,.10), transparent 45%),
    linear-gradient(135deg,#0b1220,#020617,#0b1220);
  color: #e5e7eb;
  overflow: hidden;
}

/* subtle pattern */

.footer::after {
  content:"";
  position:absolute;
  top:0;
  left:0;
  right:0;
  height:2px;
  background: linear-gradient(to right,
      transparent,
      #d4af37,
      #f6d465,
      transparent);
}

/* ===== TOP GRID ===== */

.footer-top {
  max-width: 1200px;
  margin: auto;
  padding: 80px 16px 60px;
  display: grid;
  gap: 48px;
  grid-template-columns: 1.2fr .8fr 1fr;
  position: relative;
  z-index: 2;
}

/* ===== LEFT TITLE ===== */

.footer-left h2 {
  font-size: 48px;
  line-height: 1.05;
  font-weight: 900;
  color: white;
  letter-spacing: -.02em;
}

.footer-left h2::after {
  content:"";
  display:block;
  width:80px;
  height:3px;
  margin-top:18px;
  border-radius:3px;
  background: linear-gradient(to right,#d4af37,#f6d465);
}

.tag {
  margin-top: 20px;
  color: #94a3b8;
  font-size: 20px;
  max-width: 380px;
  line-height: 1.6;
}

/* ===== HEADINGS ===== */

.footer-links h4,
.footer-contact h4 {
  color: white;
  font-size: 20px;
  letter-spacing: .12em;
  text-transform: uppercase;
  margin-bottom: 18px;
  opacity:.9;
}

/* ===== LINKS ===== */

.footer-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
  font-size: 15px;
}

.footer-links li {
  margin-bottom: 12px;
}

.footer-links a {
  color: #cbd5f1;
  text-decoration: none;
  font-size: 14px;
  transition: .25s;
  position: relative;
}

.footer-links a::before {
  content:"";
  position:absolute;
  left:-10px;
  top:50%;
  width:0;
  height:2px;
  background:#facc15;
  transition:.25s;
}

.footer-links a:hover {
  color: #fde68a;
  padding-left: 10px;
}

.footer-links a:hover::before {
  width:6px;
}

/* ===== ADDRESS ===== */

.addr {
  font-size: 15px;
  line-height: 1.7;
  color: #cbd5f1;
  margin-bottom: 16px;
}

/* ===== CONTACT & ICONS ===== */
.addr {
  font-size: 15px;
  line-height: 1.7;
  color: #cbd5f1;
  margin-bottom: 16px;
}

.contact-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 24px;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 12px;
  color: #e2e8f0;
  font-size: 15px;
}

.footer-icon {
  width: 20px;
  height: 20px;
  color: #d4af37; /* Gold color to match theme */
  flex-shrink: 0;
}

/* ===== MAP ===== */

.map {
  width: 100%;
  height: 170px;
  border-radius: 14px;
  overflow: hidden;
  border: 1px solid #1f2937;
  box-shadow: 0 10px 30px rgba(0,0,0,.35);
  transition:.4s;
}

.map:hover {
  transform: translateY(-4px);
  box-shadow: 0 18px 50px rgba(0,0,0,.45);
}

.map iframe {
  width: 100%;
  height: 100%;
  border: 0;
  filter: grayscale(.2) contrast(1.05);
}

/* ===== BOTTOM BAR ===== */

.footer-bottom {
  text-align: center;
  padding: 22px 16px;
  font-size: 13px;
  color: #94a3b8;
  border-top: 1px solid rgba(255,255,255,.08);
  background: rgba(0,0,0,.25);
  backdrop-filter: blur(4px);
}

/* ===== RESPONSIVE ===== */

@media (max-width: 900px) {

  .footer-top {
    grid-template-columns: 1fr;
    gap: 36px;
  }

  .footer-left h2 {
    font-size: 34px;
  }

  .tag {
    max-width: none;
  }

  .map {
    height: 200px;
  }
}

</style>
