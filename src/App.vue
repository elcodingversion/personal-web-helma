<template>
  <div id="portfolio">

    <!-- NAV -->
    <nav :class="{ scrolled }">
      <a class="nav-logo" href="#hero">{{ name.toLowerCase().split(' ').join('') }}.dev</a>
      <ul class="nav-links">
        <li v-for="link in navLinks" :key="link.id">
          <a :href="'#' + link.id" :class="{ active: activeSection === link.id }">{{ link.label }}</a>
        </li>
      </ul>
    </nav>

    <!-- HERO -->
    <section id="hero">
      <div class="hero-inner">
        <div class="hero-left">
          <p class="hero-eyebrow">Fresh Graduate · Junior Software Developer · {{ location }}</p>
          <h1 class="hero-name">
            {{ name.split(' ')[0] }}<br />
            <em>{{ name.split(' ').slice(1).join(' ') || 'Developer' }}</em>
          </h1>
          <p class="hero-tagline">{{ tagline }}</p>
          <div class="hero-actions">
            <a class="btn-primary" href="#projects">Lihat Proyek →</a>
            <a class="btn-outline" href="#contact">Hubungi Saya</a>
          </div>
          <div class="hero-stats">
            <div class="stat" v-for="s in stats" :key="s.label">
              <span class="stat-num">{{ s.num }}</span>
              <span class="stat-label">{{ s.label }}</span>
            </div>
          </div>
        </div>
        <div class="hero-right">
          <div class="photo-frame">
            <!-- Ganti src dengan path foto kamu, contoh: src="/src/assets/foto.jpg" -->
         <img :src="'./src/assets/self.png'" alt="Foto Profil" class="hero-photo" />
            <div class="photo-badge">
              <span class="badge-dot"></span>
              Tersedia untuk hire
            </div>
          </div>
        </div>
      </div>
      <div class="hero-scroll">Scroll</div>
    </section>

    <!-- ABOUT -->
    <section id="about">
      <p class="section-label">01 / Tentang</p>
      <div class="about-grid">
        <div class="about-text fade-in">
          <h2>Membangun solusi digital yang <em>nyata & berdampak.</em></h2>
          <p>{{ about }}</p>
          <p>Selain coding, saya juga menjalankan bisnis AI photo editing dengan <strong>500+ klien</strong> — gabungan antara kreativitas dan teknologi yang saya geluti setiap hari.</p>
        </div>
        <div class="about-details fade-in">
          <div v-for="d in details" :key="d.label" class="detail-row">
            <span class="detail-label">{{ d.label }}</span>
            <span class="detail-value">{{ d.value }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- SKILLS -->
    <section id="skills">
      <p class="section-label">02 / Keahlian</p>
      <div class="skills-grid">
        <div class="skill-card fade-in" v-for="cat in skillCats" :key="cat.name">
          <p class="skill-cat">{{ cat.name }}</p>
          <h3>{{ cat.title }}</h3>
          <div class="skill-tags">
            <span class="skill-tag" v-for="t in cat.tags" :key="t">{{ t }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- PROJECTS -->
    <section id="projects">
      <p class="section-label">03 / Proyek</p>
      <div class="projects-list">
        <div class="project-item fade-in" v-for="(p, i) in projects" :key="p.title">
          <div class="project-header">
            <div class="project-meta">
              <span class="project-num">0{{ i + 1 }}</span>
              <span class="project-type">{{ p.type }}</span>
            </div>
            <div class="project-status" :class="p.statusClass">{{ p.status }}</div>
          </div>
          <h3 class="project-title">{{ p.title }}</h3>
          <p class="project-desc">{{ p.desc }}</p>
          <div class="project-tech">
            <span class="tech-pill" v-for="t in p.tech" :key="t">{{ t }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- EXPERIENCE -->
    <section id="experience">
      <p class="section-label">04 / Pengalaman</p>
      <div class="exp-list">
        <div class="exp-item fade-in" v-for="e in experiences" :key="e.role">
          <div class="exp-left">
            <div class="exp-period">{{ e.period }}</div>
            <div class="exp-duration">{{ e.duration }}</div>
          </div>
          <div class="exp-right">
            <div class="exp-top">
              <div>
                <h3 class="exp-role">{{ e.role }}</h3>
                <p class="exp-company">{{ e.company }}</p>
              </div>
              <div class="exp-badge" v-if="e.badge">{{ e.badge }}</div>
            </div>
            <p class="exp-desc">{{ e.desc }}</p>
            <div class="exp-tags" v-if="e.tags">
              <span class="exp-tag" v-for="t in e.tags" :key="t">{{ t }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact">
      <p class="section-label">05 / Kontak</p>
      <div class="contact-inner">
        <div class="fade-in">
          <h2 class="contact-heading">Mari <em>berkolaborasi.</em></h2>
          <p class="contact-sub">Terbuka untuk peluang kerja, freelance, dan kolaborasi proyek. Saya juga open untuk klien AI photo editing!</p>
        </div>
        <div class="contact-cards fade-in">
          <a class="contact-card" href="mailto:helmarezqikao@gmail.com">
            <span class="cc-icon">✉</span>
            <span class="cc-label">Email</span>
            <span class="cc-value">helmarezqika@gmail.com</span>
          </a>
          <a class="contact-card" href="https://www.linkedin.com/in/helma-liana-rezqika-065832291/">
            <span class="cc-icon">in</span>
            <span class="cc-label">LinkedIn</span>
            <span class="cc-value">helmalianarezqika</span>
          </a>
          <a class="contact-card" href="https://github.com/elcodingversion">
            <span class="cc-icon">&lt;/&gt;</span>
            <span class="cc-label">GitHub</span>
            <span class="cc-value">github.com/elcodingversion</span>
          </a>
          <a class="contact-card" href="https://www.instagram.com/helmarezqika/">
            <span class="cc-icon">ig</span>
            <span class="cc-label">Instagram</span>
            <span class="cc-value">helmarezqika</span>
          </a>
        </div>
      </div>
    </section>

    <footer>
      <span>© 2026 {{ name }} · Purwakarta, Indonesia</span>
      <span>Built with Vue.js + Vite</span>
    </footer>

  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// ── EDIT DATA DI SINI ─────────────────────────────────
const name = ref('Helma Liana Rezqika')
const location = ref('Purwakarta, Jawa Barat')
const tagline = ref('Web Developer & AI Enthusiast. Saya membangun aplikasi web dengan Laravel & Vue.js, sekaligus menjalankan bisnis AI photo editing dengan 500+ klien aktif.')
const about = ref('Fresh graduate SMK jurusan RPL dengan pengalaman nyata di dunia industri. Selama PKL di PT. Pratama Solusi Teknologi, saya terlibat langsung dalam pengembangan sistem manajemen siswa berbasis Laravel yang mendapat nilai rata-rata 87. Saya percaya teknologi adalah alat untuk menciptakan dampak nyata.')

const navLinks = [
  { id: 'about', label: 'Tentang' },
  { id: 'skills', label: 'Skill' },
  { id: 'projects', label: 'Proyek' },
  { id: 'experience', label: 'Pengalaman' },
  { id: 'contact', label: 'Kontak' },
]

const stats = [
  { num: '3+', label: 'Proyek Selesai' },
  { num: '500+', label: 'Klien AI Foto' },
  { num: '3 bln', label: 'Pengalaman Industri' },
]

const details = [
  { label: 'Lokasi', value: 'Purwakarta, Jawa Barat' },
  { label: 'Pendidikan', value: 'SMKN 2 Purwakarta — Rekayasa Perangkat Lunak' },
  { label: 'Status', value: 'Fresh Graduate · Open to Work' },
  { label: 'Spesialisasi', value: 'Full Stack · Laravel · Vue.js · Boostsrap· PHP' },
  { label: 'Bisnis', value: 'AI Photo Editing · 500+ Klien' },
  { label: 'Tools AI', value: 'Gemini AI · Google Flow · Claude Ai' },
]

const skillCats = [
  {
    name: 'Backend',
    title: 'Server & Database',
    tags: ['Laravel', 'PHP', 'MySQL', 'MVC Pattern', 'Eloquent ORM'],
  },
  {
    name: 'Frontend',
    title: 'Antarmuka Web',
    tags: ['Vue.js', 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Blade Template'],
  },
  {
    name: 'AI & Creative',
    title: 'AI & Desain',
    tags: ['Gemini AI', 'Google Flow', 'AI Photo Editing','Prompt Engineering','Canva' ],
  },
  {
    name: 'Tools',
    title: 'Workflow & Dev',
    tags: ['Git', 'GitHub', 'VS Code', 'Laragon', 'Figma', 'XAMPP','Antigravity'],
  },

  {
    name: 'Productivty',
    title: 'Office',
    tags: ['MS Office', 'Google Docs', 'Spreadsheets'],
  },
]

const projects = [
  {
    title: 'TaskMate — Sistem Manajemen Siswa',
    type: 'Web Application',
    desc: 'Aplikasi manajemen siswa berbasis Laravel yang dikembangkan saat PKL di PT. Pratama Solusi Teknologi. Fitur meliputi manajemen data siswa, absensi, nilai, dan laporan. Mendapat nilai rata-rata 87 dari supervisor industri.',
    tech: ['Laravel', 'PHP', 'MySQL', 'Blade', 'Bootstrap'],
    status: 'Berfungsi ✓',
    statusClass: 'status-green',
  },
  {
    title: 'Sistem Peminjaman Buku Perpustakaan',
    type: 'Web Application',
    desc: 'Sistem informasi perpustakaan sekolah untuk mengelola peminjaman dan pengembalian buku. Dilengkapi fitur pencarian koleksi, riwayat peminjaman, dan notifikasi keterlambatan.',
    tech: ['Laravel', 'PHP', 'MySQL', 'Blade', 'Bootstrap'],
    status: 'Berfungsi ✓',
    statusClass: 'status-green',
  },
  {
    title: 'Thrift Shop E-Commerce',
    type: 'E-Commerce',
    desc: 'Platform jual beli pakaian thrift secara online. Fitur lengkap meliputi katalog produk, keranjang belanja, manajemen pesanan, dan panel admin untuk mengelola stok.',
    tech: ['Laravel', 'PHP', 'MySQL', 'JavaScript', 'CSS3'],
    status: 'Berfungsi ✓',
    statusClass: 'status-green',
  },
  {
    title: 'Bisnis AI Photo Editing',
    type: 'Business · Creative',
    desc: 'Menjalankan layanan editing foto berbasis AI menggunakan Gemini AI dan Google Flow. Telah melayani 500+ klien dengan hasil foto berkualitas tinggi dalam waktu singkat.',
    tech: ['Gemini AI', 'Google Flow', 'AI Tools', 'Prompt Engineering'],
    status: '500+ Klien',
    statusClass: 'status-blue',
  },
]

const experiences = [
  {
    period: 'Jun 2025 — Nov 2025',
    duration: '4 Bulan',
    role: 'Full Stack Developer (PKL)',
    company: 'PT. Pratama Solusi Teknologi',
    badge: 'Nilai 87',
    desc: 'Terlibat langsung dalam pengembangan TaskMate, sistem manajemen siswa berbasis Laravel. Bertanggung jawab pada pengembangan fitur backend, desain database, dan integrasi antarmuka. Mendapat nilai PKL rata-rata 87.',
    tags: ['Laravel', 'PHP', 'MySQL', 'Full Stack', 'Tim Profesional'],
  },
  {
    period: '2024 — Sekarang',
    duration: 'Ongoing',
    role: 'AI Photo Editing Entrepreneur',
    company: 'Bisnis Mandiri · Remote',
    badge: '500+ Klien',
    desc: 'Membangun dan menjalankan bisnis jasa editing foto berbasis AI secara mandiri. Memanfaatkan Gemini AI dan Google Flow untuk menghasilkan hasil edit berkualitas tinggi dengan efisiensi tinggi. Berhasil menangani lebih dari 500 klien.',
    tags: ['Gemini AI', 'Google Flow', 'Entrepreneurship', 'Client Management'],
  },

   {
    period: '2024 — 2025',
    duration: 'Finished',
    role: 'Pengurus & Pemateri Ekstrakulikuler Programming X-TIK SMKN 2 Purwakarta',
    company: 'Sekolah · Organisasi',
    desc: 'Menjadi pemateri aktif, menjelaskan konsep dasar pemrograman, algoritma, dan pengembangan web kepada siswa. Membantu siswa memahami teknologi terkini seperti AI dan mendorong minat mereka dalam bidang teknologi.',
    tags: ['Vscode', 'Java Script', 'HTML', 'CSS'],
  },
  {
    period: '2022 — 2025',
    duration: '3 Tahun',
    role: 'Siswa RPL',
    company: 'SMK Negeri 2 Purwakarta — Rekayasa Perangkat Lunak · Purwakarta',
    badge: null,
    desc: 'Menempuh pendidikan jurusan Rekayasa Perangkat Lunak dengan fokus pada pengembangan web. Mengerjakan berbagai proyek praktik mulai dari sistem perpustakaan, e-commerce, hingga sistem manajemen.',
    tags: ['Web Development', 'PHP', 'Laravel', 'Database', 'OOP'],
  },
]
// ─────────────────────────────────────────────────────

const scrolled = ref(false)
const activeSection = ref('hero')

const handleScroll = () => {
  scrolled.value = window.scrollY > 50
  const secs = ['hero', 'about', 'skills', 'projects', 'experience', 'contact']
  for (let i = secs.length - 1; i >= 0; i--) {
    const el = document.getElementById(secs[i])
    if (el && window.scrollY >= el.offsetTop - 160) {
      activeSection.value = secs[i]
      break
    }
  }
  document.querySelectorAll('.fade-in').forEach(el => {
    if (el.getBoundingClientRect().top < window.innerHeight * 0.88) {
      el.classList.add('visible')
    }
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@300;400;500&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --black: #0c0b0a;
  --white: #f6f5f1;
  --gray-50:  #f0efe9;
  --gray-100: #e4e3dd;
  --gray-300: #b0aea8;
  --gray-500: #787570;
  --gray-700: #3e3d3a;
  --serif: 'DM Serif Display', serif;
  --mono:  'DM Mono', monospace;
  --sans:  'DM Sans', sans-serif;
  --fs-display: clamp(2.8rem, 7vw, 6rem);
  --fs-h2: clamp(1.7rem, 3.5vw, 2.8rem);
}

html { scroll-behavior: smooth; }
body {
  font-family: var(--sans);
  background: var(--white);
  color: var(--black);
  font-size: 0.95rem;
  line-height: 1.75;
  overflow-x: hidden;
}

/* ── NAV ── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 1.2rem 5vw;
  transition: background 0.3s, border-color 0.3s, backdrop-filter 0.3s;
  border-bottom: 1px solid transparent;
}
nav.scrolled {
  background: rgba(246,245,241,0.9);
  backdrop-filter: blur(14px);
  border-color: var(--gray-100);
}
.nav-logo {
  font-family: var(--mono); font-size: 0.82rem;
  letter-spacing: 0.04em; color: var(--black); text-decoration: none;
}
.nav-links { display: flex; gap: 2rem; list-style: none; }
.nav-links a {
  font-family: var(--mono); font-size: 0.75rem;
  letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--gray-500); text-decoration: none; transition: color 0.2s;
}
.nav-links a:hover, .nav-links a.active { color: var(--black); }

/* ── SECTIONS ── */
section { padding: 7rem 5vw; }
.section-label {
  font-family: var(--mono); font-size: 0.75rem;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--gray-300); margin-bottom: 3.5rem;
  display: flex; align-items: center; gap: 1rem;
}
.section-label::after {
  content: ''; display: block;
  height: 1px; width: 40px; background: var(--gray-300);
}

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column; justify-content: center;
  border-bottom: 1px solid var(--gray-100);
  position: relative; padding-top: 6rem;
}
.hero-inner {
  display: grid; grid-template-columns: 1fr 420px;
  gap: 5vw; align-items: center;
}
.hero-eyebrow {
  font-family: var(--mono); font-size: 0.75rem;
  letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--gray-500); margin-bottom: 1.25rem;
}
.hero-name {
  font-family: var(--serif);
  font-size: var(--fs-display);
  line-height: 1.0; letter-spacing: -0.02em;
  margin-bottom: 1rem;
}
.hero-name em { font-style: italic; color: var(--gray-500); }
.hero-tagline {
  max-width: 44ch; color: var(--gray-500);
  font-size: 1rem; line-height: 1.65; margin-bottom: 2.5rem;
}
.hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 3rem; }
.btn-primary {
  display: inline-flex; align-items: center;
  font-family: var(--mono); font-size: 0.78rem;
  letter-spacing: 0.08em; text-transform: uppercase;
  background: var(--black); color: var(--white);
  padding: 0.75rem 1.5rem; text-decoration: none;
  transition: opacity 0.2s;
}
.btn-primary:hover { opacity: 0.75; }
.btn-outline {
  display: inline-flex; align-items: center;
  font-family: var(--mono); font-size: 0.78rem;
  letter-spacing: 0.08em; text-transform: uppercase;
  border: 1px solid var(--gray-300); color: var(--black);
  padding: 0.75rem 1.5rem; text-decoration: none;
  transition: border-color 0.2s;
}
.btn-outline:hover { border-color: var(--black); }
.hero-stats {
  display: flex; gap: 2.5rem; flex-wrap: wrap;
  padding-top: 2rem; border-top: 1px solid var(--gray-100);
}
.stat { display: flex; flex-direction: column; }
.stat-num {
  font-family: var(--serif); font-size: 2rem;
  line-height: 1; margin-bottom: 0.25rem;
}
.stat-label {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.1em; text-transform: uppercase; color: var(--gray-300);
}

/* Photo */
.hero-right { display: flex; justify-content: flex-end; }
.photo-frame {
  position: relative; width: 100%; max-width: 360px;
}
.hero-photo {
  width: 100%; aspect-ratio: 3/4;
  object-fit: cover; display: block;
  filter: grayscale(15%);
}
.photo-badge {
  position: absolute; bottom: -1rem; left: -1rem;
  background: var(--white); border: 1px solid var(--gray-100);
  padding: 0.6rem 1rem;
  font-family: var(--mono); font-size: 0.72rem;
  letter-spacing: 0.05em; color: var(--gray-700);
  display: flex; align-items: center; gap: 0.5rem;
}
.badge-dot {
  width: 7px; height: 7px; border-radius: 50%;
  background: #22c55e;
  animation: pulse 2s ease-in-out infinite;
}
@keyframes pulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(0.85); }
}

.hero-scroll {
  position: absolute; right: 5vw; bottom: 3rem;
  writing-mode: vertical-rl;
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.1em; color: var(--gray-300);
  display: flex; align-items: center; gap: 0.75rem;
}
.hero-scroll::after {
  content: ''; display: block;
  width: 1px; height: 44px; background: var(--gray-300);
  animation: scrollAnim 2s ease-in-out infinite;
}
@keyframes scrollAnim {
  0%,100% { transform: scaleY(1); opacity: 1; }
  50% { transform: scaleY(0.35); opacity: 0.3; }
}

/* ── ABOUT ── */
#about { border-bottom: 1px solid var(--gray-100); }
.about-grid {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 6vw; align-items: start;
}
.about-text h2 {
  font-family: var(--serif); font-size: var(--fs-h2);
  line-height: 1.15; margin-bottom: 1.5rem;
}
.about-text em { font-style: italic; color: var(--gray-500); }
.about-text p { color: var(--gray-700); margin-bottom: 1.1rem; }
.about-text strong { color: var(--black); font-weight: 500; }
.detail-row {
  display: flex; justify-content: space-between; align-items: baseline;
  padding: 0.85rem 0; border-bottom: 1px solid var(--gray-100);
  font-size: 0.875rem; gap: 1rem;
}
.detail-row:first-child { border-top: 1px solid var(--gray-100); }
.detail-label {
  font-family: var(--mono); font-size: 0.7rem;
  letter-spacing: 0.09em; text-transform: uppercase; color: var(--gray-300);
  flex-shrink: 0;
}
.detail-value { color: var(--black); text-align: right; }

/* ── SKILLS ── */
#skills { border-bottom: 1px solid var(--gray-100); }
.skills-grid {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 2px; background: var(--gray-100);
  border: 1px solid var(--gray-100);
}
.skill-card { background: var(--white); padding: 2rem 1.75rem; }
.skill-cat {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--gray-300); margin-bottom: 0.75rem;
}
.skill-card h3 {
  font-family: var(--serif); font-size: 1.4rem; margin-bottom: 1rem;
}
.skill-tags { display: flex; flex-wrap: wrap; gap: 0.45rem; }
.skill-tag {
  font-family: var(--mono); font-size: 0.7rem;
  padding: 0.3rem 0.7rem; border: 1px solid var(--gray-100);
  color: var(--gray-700); letter-spacing: 0.03em;
}

/* ── PROJECTS ── */
#projects { border-bottom: 1px solid var(--gray-100); }
.projects-list {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2px; background: var(--gray-100); border: 1px solid var(--gray-100);
}
.project-item {
  background: var(--white); padding: 2rem 1.75rem;
  display: flex; flex-direction: column; gap: 0.75rem;
  transition: background 0.2s;
}
.project-item:hover { background: var(--gray-50); }
.project-header { display: flex; justify-content: space-between; align-items: center; }
.project-meta { display: flex; align-items: center; gap: 0.75rem; }
.project-num {
  font-family: var(--mono); font-size: 0.68rem;
  color: var(--gray-300); letter-spacing: 0.05em;
}
.project-type {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.06em; text-transform: uppercase; color: var(--gray-300);
}
.project-status {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.04em; padding: 0.25rem 0.6rem;
  border: 1px solid;
}
.status-green { color: #166534; border-color: #bbf7d0; background: #f0fdf4; }
.status-blue  { color: #1e3a8a; border-color: #bfdbfe; background: #eff6ff; }
.project-title { font-family: var(--serif); font-size: 1.25rem; line-height: 1.2; }
.project-desc { font-size: 0.85rem; color: var(--gray-500); line-height: 1.65; flex: 1; }
.project-tech { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: auto; padding-top: 0.5rem; }
.tech-pill {
  font-family: var(--mono); font-size: 0.65rem;
  border: 1px solid var(--gray-100); color: var(--gray-500);
  padding: 0.2rem 0.55rem;
}

/* ── EXPERIENCE ── */
#experience { border-bottom: 1px solid var(--gray-100); }
.exp-item {
  display: grid; grid-template-columns: 160px 1fr;
  gap: 3rem; padding: 2.5rem 0;
  border-bottom: 1px solid var(--gray-100);
}
.exp-item:first-child { border-top: 1px solid var(--gray-100); }
.exp-left { padding-top: 0.2rem; }
.exp-period {
  font-family: var(--mono); font-size: 0.72rem;
  letter-spacing: 0.04em; color: var(--gray-500); margin-bottom: 0.25rem;
}
.exp-duration {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.06em; color: var(--gray-300); text-transform: uppercase;
}
.exp-top { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 0.75rem; }
.exp-role { font-family: var(--serif); font-size: 1.25rem; margin-bottom: 0.2rem; }
.exp-company {
  font-family: var(--mono); font-size: 0.75rem;
  color: var(--gray-500); letter-spacing: 0.04em;
}
.exp-badge {
  font-family: var(--mono); font-size: 0.68rem;
  border: 1px solid var(--gray-100); color: var(--gray-700);
  padding: 0.25rem 0.65rem; flex-shrink: 0;
}
.exp-desc { font-size: 0.875rem; color: var(--gray-700); line-height: 1.7; margin-bottom: 0.85rem; }
.exp-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
.exp-tag {
  font-family: var(--mono); font-size: 0.68rem;
  color: var(--gray-500); border: 1px solid var(--gray-100);
  padding: 0.2rem 0.55rem;
}

/* ── CONTACT ── */
#contact {}
.contact-inner { max-width: 900px; }
.contact-heading {
  font-family: var(--serif);
  font-size: var(--fs-display);
  line-height: 1.0; letter-spacing: -0.02em; margin-bottom: 1rem;
}
.contact-heading em { font-style: italic; color: var(--gray-300); }
.contact-sub { color: var(--gray-500); max-width: 46ch; margin-bottom: 3rem; }
.contact-cards {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2px; background: var(--gray-100); border: 1px solid var(--gray-100);
}
.contact-card {
  background: var(--white); padding: 1.5rem;
  display: flex; flex-direction: column; gap: 0.3rem;
  text-decoration: none; color: inherit;
  transition: background 0.2s;
}
.contact-card:hover { background: var(--gray-50); }
.cc-icon {
  font-family: var(--mono); font-size: 0.85rem;
  color: var(--gray-300); margin-bottom: 0.5rem;
}
.cc-label {
  font-family: var(--mono); font-size: 0.68rem;
  letter-spacing: 0.1em; text-transform: uppercase; color: var(--gray-300);
}
.cc-value { font-size: 0.85rem; color: var(--black); }

/* ── FOOTER ── */
footer {
  border-top: 1px solid var(--gray-100);
  padding: 2rem 5vw;
  display: flex; justify-content: space-between; align-items: center;
  font-family: var(--mono); font-size: 0.7rem;
  letter-spacing: 0.05em; color: var(--gray-300);
}

/* ── FADE-IN ── */
.fade-in { opacity: 0; transform: translateY(22px); transition: opacity 0.7s cubic-bezier(.22,.6,.36,1), transform 0.7s cubic-bezier(.22,.6,.36,1); }
.fade-in.visible { opacity: 1; transform: translateY(0); }

/* ── RESPONSIVE ── */
@media (max-width: 900px) {
  .hero-inner { grid-template-columns: 1fr; }
  .hero-right { display: none; }
  .about-grid { grid-template-columns: 1fr; }
}
@media (max-width: 640px) {
  .exp-item { grid-template-columns: 1fr; gap: 0.5rem; }
  .nav-links { display: none; }
  .hero-scroll { display: none; }
  .hero-stats { gap: 1.5rem; }
  footer { flex-direction: column; gap: 0.5rem; text-align: center; }
}
</style>
