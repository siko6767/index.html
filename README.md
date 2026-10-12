<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#f5f3ff">
<title>Ventorme — Discover Your Future</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Manrope:wght@400;500;600;700;800&display=swap');

:root {
  --purple: #7160f5;
  --purple-dark: #4d3bd5;
  --pink: #f3a6d4;
  --blue: #a8d9ff;
  --ink: #202044;
  --muted: #74758e;
  --white: #fff;
  --surface: rgba(255,255,255,.83);
  --border: rgba(115,101,210,.13);
  --shadow: 0 15px 50px rgba(91,75,180,.10);
}

* { box-sizing: border-box; }

html {
  scroll-behavior: smooth;
  scroll-padding-top: 85px;
}

body {
  margin: 0;
  color: var(--ink);
  background: #f8f8ff;
  font-family: 'DM Sans', sans-serif;
  overflow-x: hidden;
}

button, input, select, textarea { font: inherit; }
button { cursor: pointer; }

button:focus-visible, input:focus-visible,
select:focus-visible, textarea:focus-visible {
  outline: 3px solid #a9a0ff;
  outline-offset: 3px;
}

button:active { transform: scale(.97); }

button, .card, .feature-card, .nav-link {
  transition: transform .25s ease, box-shadow .25s ease,
    background .25s ease, color .25s ease;
}

button:hover { filter: brightness(1.04); }

a { color: inherit; text-decoration: none; }

.hidden { display: none !important; }

.gradient-text {
  background: linear-gradient(100deg,#6355ed,#b46ce8,#ed86c4);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.container {
  width: min(1160px, calc(100% - 40px));
  margin: auto;
}

#progressBar {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  width: 0;
  background: linear-gradient(90deg,#7563ff,#f3a6d4);
  z-index: 2000;
}

.blob {
  position: absolute;
  width: 300px;
  height: 300px;
  border-radius: 50%;
  filter: blur(80px);
  opacity: .45;
  pointer-events: none;
  animation: blobFloat 10s ease-in-out infinite alternate;
}

.blob-one { background: #c6baff; top: 70px; left: -120px; }
.blob-two { background: #ffd0e8; top: 220px; right: -120px; animation-delay: -4s; }

@keyframes blobFloat {
  from { transform: translate(0,0) scale(1); }
  to { transform: translate(40px,-35px) scale(1.12); }
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes float {
  0%,100% { transform: translateY(0) rotate(-2deg); }
  50% { transform: translateY(-14px) rotate(2deg); }
}

@keyframes pulse {
  0%,100% { box-shadow: 0 0 0 0 rgba(113,96,245,.2); }
  50% { box-shadow: 0 0 0 12px rgba(113,96,245,0); }
}

@keyframes shine {
  from { background-position: -200% center; }
  to { background-position: 200% center; }
}

.animate-in { animation: fadeUp .75s both; }
.delay-1 { animation-delay: .12s; }
.delay-2 { animation-delay: .24s; }
.delay-3 { animation-delay: .36s; }

.reveal {
  opacity: 0;
  transform: translateY(25px);
  transition: opacity .7s ease, transform .7s ease;
}

.reveal.visible { opacity: 1; transform: translateY(0); }

/* NAVIGATION */

.topbar {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: rgba(250,249,255,.85);
  backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(113,96,245,.09);
}

.nav-inner {
  min-height: 76px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

.brand {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-family: Manrope, sans-serif;
  font-weight: 800;
  font-size: 22px;
  letter-spacing: -.8px;
  cursor: pointer;
}

.brand-icon {
  width: 37px;
  height: 37px;
  display: grid;
  place-items: center;
  color: white;
  border-radius: 13px;
  background: linear-gradient(140deg,#8375ff,#a66ee9);
  box-shadow: 0 7px 18px #7160f53a;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 25px;
}

.nav-links a {
  font-size: 14px;
  color: #666681;
}

.nav-links a:hover { color: var(--purple); }

.nav-actions {
  display: flex;
  gap: 10px;
  align-items: center;
}

.menu-toggle {
  display: none;
  background: white;
  color: var(--ink);
  border: 1px solid var(--border);
  padding: 10px 13px;
  border-radius: 12px;
}

.primary-btn, .secondary-btn, .danger-btn {
  border: 0;
  padding: 12px 19px;
  border-radius: 12px;
  font-weight: 700;
  font-size: 14px;
}

.primary-btn {
  color: white;
  background: linear-gradient(110deg,#7666ff,#6650e8);
  box-shadow: 0 7px 20px #7160f535;
}

.primary-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 25px #7160f545;
}

.secondary-btn {
  color: #5c4dd3;
  background: #efedff;
}

.danger-btn { color: #c43f64; background: #ffe9f0; }

.small-btn { padding: 8px 11px; font-size: 12px; }

/* LANDING PAGE */

.hero {
  position: relative;
  isolation: isolate;
  padding: 95px 0 75px;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 10% 15%,#eee9ff 0,transparent 42%),
    radial-gradient(ellipse at 85% 30%,#ffe8f4 0,transparent 38%),
    linear-gradient(180deg,#faf9ff,#f6f5ff);
}

.hero-grid {
  display: grid;
  grid-template-columns: 1.05fr .95fr;
  align-items: center;
  gap: 55px;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: #fff;
  border: 1px solid #e9e4ff;
  padding: 9px 13px;
  border-radius: 100px;
  color: #6251dc;
  font-size: 12px;
  font-weight: 700;
  box-shadow: 0 5px 20px #7160f50c;
}

.eyebrow-dot {
  height: 7px;
  width: 7px;
  border-radius: 50%;
  background: #8a79ff;
  animation: pulse 2s infinite;
}

.hero h1 {
  font-family: Manrope, sans-serif;
  font-size: clamp(42px,6vw,73px);
  line-height: 1.08;
  letter-spacing: -3.5px;
  margin: 25px 0 22px;
  font-weight: 800;
}

.hero-description {
  color: #73738e;
  font-size: 17px;
  line-height: 1.85;
  max-width: 480px;
}

.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 13px;
  margin: 30px 0 28px;
}

.hero-note {
  display: flex;
  align-items: center;
  gap: 9px;
  color: #77768e;
  font-size: 12px;
}

.avatar-stack { display: flex; }
.avatar-stack span {
  width: 29px;
  height: 29px;
  border: 2px solid white;
  border-radius: 50%;
  display: grid;
  place-items: center;
  margin-left: -7px;
  background: #e8e1ff;
  font-size: 13px;
}
.avatar-stack span:first-child { margin-left: 0; }

.hero-art {
  min-height: 420px;
  position: relative;
  display: grid;
  place-items: center;
}

.art-orbit {
  position: absolute;
  width: 370px;
  height: 370px;
  border: 1px dashed #b9afff;
  border-radius: 50%;
  animation: spin 45s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

.art-orbit::before, .art-orbit::after {
  content: "✦";
  position: absolute;
  color: #a79bff;
  font-size: 26px;
}
.art-orbit::before { top: 50px; left: 35px; }
.art-orbit::after { bottom: 45px; right: 25px; }

.art-main-card {
  position: relative;
  z-index: 2;
  width: min(100%,360px);
  padding: 24px;
  border: 1px solid #ffffff;
  border-radius: 27px;
  background: rgba(255,255,255,.78);
  backdrop-filter: blur(15px);
  box-shadow: 0 30px 80px #6958d52b;
  animation: float 5s ease-in-out infinite;
}

.art-card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 13px;
  font-weight: 700;
}

.art-icon {
  width: 58px;
  height: 58px;
  border-radius: 18px;
  display: grid;
  place-items: center;
  font-size: 29px;
  background: linear-gradient(140deg,#e6ddff,#f9dff0);
}

.art-main-card h3 { font-size: 21px; margin: 20px 0 8px; }
.art-main-card p { color: var(--muted); font-size: 13px; line-height: 1.6; }

.progress-track {
  height: 7px;
  background: #eeecfb;
  border-radius: 20px;
  overflow: hidden;
  margin: 17px 0;
}

.progress-fill {
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg,#7160f5,#e88fc9);
  transition: width .8s ease;
}

.mini-tags { display: flex; gap: 7px; flex-wrap: wrap; }
.mini-tags span {
  padding: 7px 10px;
  border-radius: 9px;
  background: #f0edff;
  color: #6555d8;
  font-size: 11px;
  font-weight: 700;
}

.float-chip {
  position: absolute;
  z-index: 3;
  padding: 14px 16px;
  background: white;
  border-radius: 17px;
  box-shadow: var(--shadow);
  font-size: 12px;
  font-weight: 700;
  animation: float 4s ease-in-out infinite;
}
.chip-one { top: 35px; right: -5px; }
.chip-two { bottom: 40px; left: -5px; animation-delay: -2s; }

/* GENERAL SECTIONS */

.section { padding: 85px 0; }
.section-heading { text-align: center; max-width: 640px; margin: 0 auto 45px; }
.section-heading .eyebrow { margin-bottom: 15px; }
.section-heading h2 {
  font-family: Manrope, sans-serif;
  font-size: clamp(29px,4vw,45px);
  line-height: 1.2;
  letter-spacing: -1.7px;
  margin: 0 0 14px;
}
.section-heading p { color: var(--muted); line-height: 1.8; }

.features-grid {
  display: grid;
  grid-template-columns: repeat(4,1fr);
  gap: 17px;
}

.feature-card {
  padding: 25px 21px;
  border: 1px solid var(--border);
  border-radius: 19px;
  background: rgba(255,255,255,.8);
  box-shadow: 0 6px 25px #7160f509;
}

.feature-card:hover {
  transform: translateY(-7px);
  box-shadow: var(--shadow);
  border-color: #c7beff;
}

.feature-icon {
  width: 49px;
  height: 49px;
  display: grid;
  place-items: center;
  border-radius: 15px;
  background: linear-gradient(145deg,#ece8ff,#fce6f3);
  font-size: 24px;
  margin-bottom: 20px;
}

.feature-card h3 { font-size: 17px; margin: 0 0 10px; }
.feature-card p { font-size: 13px; line-height: 1.8; color: var(--muted); margin: 0; }

.steps-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 22px;
}

.step-card {
  position: relative;
  padding: 30px;
  border-radius: 20px;
  background: white;
  border: 1px solid var(--border);
}

.step-number {
  font-family: Manrope,sans-serif;
  font-size: 37px;
  font-weight: 800;
  color: #d5ceff;
}

.step-card h3 { margin: 15px 0 8px; }
.step-card p { color: var(--muted); font-size: 14px; line-height: 1.8; }

.cta-section { padding: 20px 0 85px; }

.cta-card {
  position: relative;
  overflow: hidden;
  text-align: center;
  padding: 60px 25px;
  border-radius: 30px;
  background: linear-gradient(120deg,#6d5bf1,#9277ef,#e59bd0);
  color: white;
  box-shadow: 0 20px 60px #7160f52e;
}

.cta-card::before, .cta-card::after {
  content: "";
  position: absolute;
  width: 240px;
  height: 240px;
  border: 1px solid #ffffff30;
  border-radius: 50%;
}
.cta-card::before { top: -130px; left: -60px; }
.cta-card::after { bottom: -170px; right: -60px; }

.cta-card h2 {
  font-family: Manrope,sans-serif;
  font-size: clamp(30px,4vw,46px);
  margin: 0 0 14px;
  letter-spacing: -1.5px;
}
.cta-card p { opacity: .88; margin-bottom: 28px; }
.cta-card .primary-btn { background: white; color: #6251dc; }

/* APP */

.app-shell { min-height: 80vh; padding: 30px 0 75px; }

.app-layout {
  display: grid;
  grid-template-columns: 215px minmax(0,1fr);
  gap: 25px;
  align-items: start;
}

.sidebar {
  position: sticky;
  top: 100px;
  padding: 17px;
  border: 1px solid var(--border);
  background: var(--surface);
  border-radius: 20px;
  backdrop-filter: blur(15px);
}

.sidebar-title {
  padding: 8px 10px 17px;
  color: var(--muted);
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1.3px;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 11px;
  width: 100%;
  padding: 13px 12px;
  margin: 3px 0;
  border: 0;
  border-radius: 12px;
  background: transparent;
  color: #666681;
  text-align: left;
  font-size: 13px;
}

.nav-link:hover { background: #f2efff; color: var(--purple); }
.nav-link.active {
  background: linear-gradient(100deg,#eeebff,#f6eaff);
  color: #5e4dd8;
  font-weight: 700;
}

.nav-icon { width: 20px; text-align: center; font-size: 16px; }

.app-content { min-width: 0; }
.page { animation: fadeUp .45s both; }

.page-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 20px;
  margin: 4px 0 25px;
}

.page-header h2 {
  font-family: Manrope,sans-serif;
  font-size: clamp(25px,3vw,34px);
  letter-spacing: -1px;
  margin: 0 0 8px;
}

.page-header p { color: var(--muted); font-size: 14px; margin: 0; line-height: 1.7; }

.panel {
  padding: 24px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 20px;
  box-shadow: 0 8px 35px #7160f508;
  margin-bottom: 20px;
}

.panel h3 { margin-top: 0; }
.stats-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 14px;
  margin-bottom: 22px;
}

.stat-card {
  background: white;
  border: 1px solid var(--border);
  padding: 20px;
  border-radius: 17px;
  transition: transform .3s ease;
}
.stat-card:hover { transform: translateY(-4px); }
.stat-top { display: flex; align-items: center; justify-content: space-between; }
.stat-icon {
  display: grid;
  place-items: center;
  width: 38px;
  height: 38px;
  border-radius: 12px;
  background: #eeebff;
  font-size: 18px;
}
.stat-card strong { display: block; font-size: 29px; margin-top: 13px; }
.stat-card p { color: var(--muted); font-size: 12px; margin: 5px 0 0; }

.recommendation-banner {
  position: relative;
  overflow: hidden;
  border-radius: 19px;
  padding: 27px;
  color: white;
  background: linear-gradient(120deg,#6755eb,#8873f4 60%,#a98bea);
  margin-bottom: 22px;
}
.recommendation-banner::after {
  content: "✦";
  position: absolute;
  right: 25px;
  top: 5px;
  font-size: 90px;
  opacity: .12;
}
.recommendation-banner h3 { margin-bottom: 8px; }
.recommendation-banner p { font-size: 13px; line-height: 1.7; opacity: .85; }
.recommendation-banner .mini-tags span { background: #ffffff28; color: white; }
.recommendation-banner button { margin-top: 18px; background: white; color: #5c4ad3; }

.section-subtitle {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  margin: 25px 0 15px;
}
.section-subtitle h3 { margin: 0; font-size: 17px; }

.task-row {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 0;
  border-bottom: 1px solid #eeedf7;
}
.task-row:last-child { border-bottom: 0; }
.task-row input[type="checkbox"] { width: 17px; height: 17px; accent-color: var(--purple); }
.task-row .task-text { flex: 1; min-width: 0; overflow-wrap: anywhere; }
.task-row .task-text.done { text-decoration: line-through; color: #9998ad; }
.task-row small { color: var(--muted); display: block; margin-top: 5px; font-size: 11px; }
.task-row button { flex-shrink: 0; }

input, select, textarea {
  width: 100%;
  padding: 12px 13px;
  border-radius: 11px;
  border: 1px solid #e1deef;
  color: var(--ink);
  background: white;
  outline: none;
  margin: 7px 0 15px;
  transition: border .2s, box-shadow .2s;
}
input:focus, select:focus, textarea:focus {
  border-color: #9b8fff;
  box-shadow: 0 0 0 4px #7160f513;
}
textarea { resize: vertical; min-height: 90px; }
label { display: block; font-size: 13px; font-weight: 700; margin-top: 8px; }

.form-grid {
  display: grid;
  grid-template-columns: repeat(2,minmax(0,1fr));
  gap: 0 17px;
}
.full-width { grid-column: 1/-1; }

.career-grid, .university-grid {
  display: grid;
  grid-template-columns: repeat(2,minmax(0,1fr));
  gap: 15px;
}

.career-card, .university-card {
  background: white;
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 19px;
  transition: transform .25s ease, box-shadow .25s ease;
}
.career-card:hover, .university-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow);
}
.career-card h3, .university-card h3 { margin: 13px 0 8px; font-size: 17px; }
.career-card p, .university-card p { color: var(--muted); font-size: 13px; line-height: 1.7; }
.card-actions { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 14px; }

.tag {
  display: inline-block;
  background: #f0edff;
  color: #6554d9;
  padding: 6px 9px;
  border-radius: 100px;
  font-size: 11px;
  font-weight: 700;
}
.status-tag { background: #e9f8f0; color: #32845b; }

.filter-row { display: flex; flex-wrap: wrap; gap: 8px; margin: 15px 0 20px; }
.filter-btn {
  border: 1px solid var(--border);
  border-radius: 100px;
  background: white;
  color: #76758e;
  padding: 9px 14px;
  font-size: 12px;
}
.filter-btn.active { background: #7160f5; color: white; border-color: #7160f5; }

.quiz-question { margin-bottom: 25px; }
.quiz-question h3 { font-size: 16px; margin-bottom: 14px; }
.option-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 10px; }
.option {
  position: relative;
  padding: 16px 12px;
  border: 1px solid #e5e2f2;
  background: white;
  border-radius: 14px;
  text-align: left;
  color: var(--ink);
  font-size: 12px;
  line-height: 1.5;
}
.option span { display: block; font-size: 24px; margin-bottom: 10px; }
.option.selected { border-color: #7160f5; background: #f3f0ff; box-shadow: 0 0 0 2px #7160f51a; }
.option:hover { transform: translateY(-3px); }

.quiz-progress {
  height: 6px;
  background: #eeecf8;
  border-radius: 20px;
  overflow: hidden;
  margin: 17px 0 30px;
}
.quiz-progress div { height: 100%; background: linear-gradient(90deg,#7160f5,#e99bce); transition: width .4s ease; }

.empty-state {
  text-align: center;
  padding: 32px 15px;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.8;
}
.empty-state span { display: block; font-size: 36px; margin-bottom: 12px; }

.toast {
  position: fixed;
  z-index: 3000;
  bottom: 25px;
  left: 50%;
  transform: translate(-50%,20px);
  opacity: 0;
  pointer-events: none;
  padding: 13px 20px;
  border-radius: 13px;
  color: white;
  background: #29234f;
  box-shadow: var(--shadow);
  font-size: 13px;
  transition: .3s ease;
}
.toast.show { opacity: 1; transform: translate(-50%,0); }

footer {
  border-top: 1px solid var(--border);
  padding: 30px 0;
  color: var(--muted);
  font-size: 12px;
  text-align: center;
}

/* RESPONSIVE */

@media (max-width: 900px) {
  .hero-grid { gap: 20px; }
  .features-grid { grid-template-columns: repeat(2,1fr); }
  .app-layout { grid-template-columns: 1fr; }
  .sidebar { position: static; display: flex; flex-wrap: wrap; gap: 5px; }
  .sidebar-title { width: 100%; padding-bottom: 5px; }
  .nav-link { width: auto; flex: 1 1 125px; }
}

@media (max-width: 650px) {
  .container { width: min(100% - 28px,1160px); }
  .nav-inner { min-height: 66px; }
  .nav-links, .nav-actions { display: none; }
  .menu-toggle { display: block; }
  .topbar.menu-open .nav-inner { flex-wrap: wrap; padding-bottom: 12px; }
  .topbar.menu-open .nav-links {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    width: 100%;
    gap: 0;
    order: 3;
  }
  .topbar.menu-open .nav-links a { padding: 12px 5px; }
  .hero { padding: 65px 0 50px; }
  .hero-grid { grid-template-columns: 1fr; }
  .hero h1 { letter-spacing: -2px; }
  .hero-description { font-size: 15px; }
  .hero-art { min-height: 350px; }
  .art-orbit { width: 290px; height: 290px; }
  .art-main-card { max-width: 320px; }
  .chip-one { right: 0; }
  .chip-two { left: 0; }
  .section { padding: 60px 0; }
  .features-grid, .steps-grid { grid-template-columns: 1fr; }
  .stats-grid { grid-template-columns: 1fr; }
  .career-grid, .university-grid { grid-template-columns: 1fr; }
  .option-grid { grid-template-columns: repeat(2,1fr); }
  .page-header { flex-direction: column; }
  .panel { padding: 18px; }
  .form-grid { grid-template-columns: 1fr; }
  .full-width { grid-column: auto; }
  .cta-card { padding: 45px 18px; }
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
    transition-duration: .01ms !important;
  }
  .reveal { opacity: 1; transform: none; }
}
</style>
</head>

<body>
<div id="progressBar"></div>
<div id="toast" class="toast" role="status" aria-live="polite"></div>

<header class="topbar" id="topbar">
  <div class="container nav-inner">
    <a class="brand" href="#landing" onclick="goLanding()">
      <span class="brand-icon">✦</span> Ventorme
    </a>

    <div class="nav-links">
      <a href="#features">Features</a>
      <a href="#how-it-works">How it works</a>
      <a href="#about">About</a>
    </div>

    <div class="nav-actions">
      <button class="primary-btn" onclick="enterApp('home')">Get Started ↗</button>
    </div>

    <button class="menu-toggle" onclick="toggleMenu()" aria-label="Toggle menu">☰</button>
  </div>
</header>

<!-- FIRST PAGE / LANDING -->

<div id="landing">
  <section class="hero" id="hero">
    <div class="blob blob-one"></div>
    <div class="blob blob-two"></div>

    <div class="container hero-grid">
      <div>
        <div class="eyebrow animate-in">
          <span class="eyebrow-dot"></span>
          YOUR FUTURE STARTS HERE
        </div>

        <h1 class="animate-in delay-1">
          Discover your future.<br>
          <span class="gradient-text">Build your path.</span>
        </h1>

        <p class="hero-description animate-in delay-2">
          Your interests have potential. Explore careers, discover universities,
          set meaningful goals and turn your dreams into a plan — one step at a time.
        </p>

        <div class="hero-buttons animate-in delay-3">
          <button class="primary-btn" onclick="enterApp('quiz')">Start your journey ↗</button>
          <button class="secondary-btn" onclick="scrollToSection('features')">Explore features ↓</button>
        </div>

        <div class="hero-note animate-in delay-3">
          <div class="avatar-stack">
            <span>🌱</span><span>💡</span><span>🚀</span>
          </div>
          <span>A little progress every day adds up.</span>
        </div>
      </div>

      <div class="hero-art">
        <div class="art-orbit"></div>

        <div class="art-main-card">
          <div class="art-card-header">
            <span>✨ YOUR FUTURE PLAN</span>
            <span>•••</span>
          </div>

          <div class="art-icon">🚀</div>
          <h3>Your next chapter</h3>
          <p>Big dreams become achievable when you break them into small steps.</p>

          <div class="progress-track"><div class="progress-fill" style="width:72%"></div></div>

          <div class="art-card-header">
            <span>Explore your potential</span>
            <span style="color:#7665ee">72%</span>
          </div>

          <div class="mini-tags" style="margin-top:17px">
            <span>Career discovery</span>
            <span>University goals</span>
            <span>New skills</span>
          </div>
        </div>

        <div class="float-chip chip-one">💡 Find what inspires you</div>
        <div class="float-chip chip-two">🌸 Progress, not perfection</div>
      </div>
    </div>
  </section>

  <section class="section" id="features">
    <div class="container">
      <div class="section-heading reveal">
        <div class="eyebrow">YOUR PERSONAL TOOLKIT</div>
        <h2>Everything you need to <span class="gradient-text">move forward.</span></h2>
        <p>From discovering what you love to organizing the steps that get you there.</p>
      </div>

      <div class="features-grid">
        <article class="feature-card reveal">
          <div class="feature-icon">🧭</div>
          <h3>Career Discovery</h3>
          <p>Explore career paths, understand useful skills and discover new possibilities.</p>
        </article>

        <article class="feature-card reveal">
          <div class="feature-icon">🎓</div>
          <h3>University Shortlist</h3>
          <p>Save universities, compare programs and keep track of your application plans.</p>
        </article>

        <article class="feature-card reveal">
          <div class="feature-icon">📝</div>
          <h3>Personal Planner</h3>
          <p>Turn big goals into manageable tasks and celebrate each completed step.</p>
        </article>

        <article class="feature-card reveal">
          <div class="feature-icon">🌷</div>
          <h3>Your Own Space</h3>
          <p>Save your interests, career favorites and personal plans in one place.</p>
        </article>
      </div>
    </div>
  </section>

  <section class="section" id="how-it-works" style="background:linear-gradient(180deg,#f4f1ff,#faf9ff)">
    <div class="container">
      <div class="section-heading reveal">
        <div class="eyebrow">SIMPLE BY DESIGN</div>
        <h2>Three steps. <span class="gradient-text">A clearer direction.</span></h2>
        <p>You don't need to have everything figured out. Just begin.</p>
      </div>

      <div class="steps-grid">
        <article class="step-card reveal">
          <div class="step-number">01</div>
          <div class="feature-icon">🔎</div>
          <h3>Explore</h3>
          <p>Discover your interests and browse career paths you may not have considered.</p>
        </article>

        <article class="step-card reveal">
          <div class="step-number">02</div>
          <div class="feature-icon">🗺️</div>
          <h3>Make a plan</h3>
          <p>Shortlist universities, identify your goals and organize your next steps.</p>
        </article>

        <article class="step-card reveal">
          <div class="step-number">03</div>
          <div class="feature-icon">🌟</div>
          <h3>Keep growing</h3>
          <p>Track your progress, update your plans and keep learning along the way.</p>
        </article>
      </div>
    </div>
  </section>

  <section class="section" id="about">
    <div class="container">
      <div class="section-heading reveal">
        <div class="eyebrow">OUR PHILOSOPHY</div>
        <h2>Your future is not a test result.</h2>
        <p>
          Ventorme is a place to explore, experiment and make informed choices.
          Our career quiz offers ideas, not fixed labels. Your interests can change,
          your skills can grow, and your path can evolve.
        </p>
      </div>
    </div>
  </section>

  <section class="cta-section">
    <div class="container">
      <div class="cta-card reveal">
        <h2>Ready to start your next chapter?</h2>
        <p>Your future doesn't need to be perfectly planned. It just needs a first step.</p>
        <button class="primary-btn" onclick="enterApp('quiz')">Discover your possibilities ↗</button>
      </div>
    </div>
  </section>
</div>

<!-- APP AREA -->

<div id="app" class="hidden">
  <div class="app-shell">
    <div class="container app-layout">

      <aside class="sidebar">
        <div class="sidebar-title">YOUR WORKSPACE</div>
        <button class="nav-link active" data-page="home" onclick="showPage('home')"><span class="nav-icon">⌂</span> Dashboard</button>
        <button class="nav-link" data-page="quiz" onclick="showPage('quiz')"><span class="nav-icon">✧</span> Career Quiz</button>
        <button class="nav-link" data-page="careers" onclick="showPage('careers')"><span class="nav-icon">◎</span> Explore Careers</button>
        <button class="nav-link" data-page="universities" onclick="showPage('universities')"><span class="nav-icon">▤</span> Universities</button>
        <button class="nav-link" data-page="tasks" onclick="showPage('tasks')"><span class="nav-icon">☑</span> My Tasks</button>
        <button class="nav-link" data-page="settings" onclick="showPage('settings')"><span class="nav-icon">⚙</span> Settings</button>
        <button class="nav-link" onclick="goLanding()"><span class="nav-icon">↩</span> Back to Home</button>
      </aside>

      <div class="app-content">

        <!-- DASHBOARD -->
        <section id="page-home" class="page">
          <div class="page-header">
            <div>
              <h2 id="greeting">Welcome to Ventorme! 👋</h2>
              <p>Your future is full of possibilities. Keep going!</p>
            </div>
            <button class="primary-btn" onclick="showPage('quiz')">Discover careers ↗</button>
          </div>

          <div class="stats-grid">
            <div class="stat-card">
              <div class="stat-top"><span>Pending tasks</span><span class="stat-icon">📝</span></div>
              <strong id="taskCount">0</strong><p>Small steps count.</p>
            </div>
            <div class="stat-card">
              <div class="stat-top"><span>Universities</span><span class="stat-icon">🎓</span></div>
              <strong id="uniCount">0</strong><p>Your shortlist.</p>
            </div>
            <div class="stat-card">
              <div class="stat-top"><span>Saved careers</span><span class="stat-icon">💜</span></div>
              <strong id="careerCount">0</strong><p>Ideas worth exploring.</p>
            </div>
          </div>

          <div class="recommendation-banner">
            <h3>✨ Your career journey</h3>
            <p id="homeRecommendation">Discover your interests and find career paths to explore.</p>
            <div class="mini-tags" id="homeCareerTags">
              <span>Explore</span><span>Learn</span><span>Grow</span>
            </div>
            <button class="primary-btn" onclick="showPage('quiz')">Take career quiz →</button>
          </div>

          <div class="panel">
            <div class="section-subtitle">
              <h3>Upcoming tasks</h3>
              <button class="secondary-btn small-btn" onclick="showPage('tasks')">View all →</button>
            </div>
            <div id="homeTasks"></div>
          </div>

          <div class="panel">
            <div class="section-subtitle"><h3>Your saved careers</h3>
              <button class="secondary-btn small-btn" onclick="showPage('careers')">Explore →</button>
            </div>
            <div id="homeSavedCareers" class="mini-tags"></div>
          </div>
        </section>

        <!-- QUIZ -->
        <section id="page-quiz" class="page hidden">
          <div class="page-header">
            <div>
              <h2>Career Discovery ✨</h2>
              <p>A few questions to help you explore possible directions.</p>
            </div>
          </div>

          <div class="panel">
            <div class="section-subtitle">
              <span id="quizStepLabel">Question 1 of 4</span>
              <span id="quizPercent" class="tag">25%</span>
            </div>
            <div class="quiz-progress"><div id="quizProgressFill" style="width:25%"></div></div>

            <div id="quizQuestionArea"></div>

            <div style="display:flex;justify-content:space-between;gap:10px;margin-top:25px">
              <button class="secondary-btn" id="quizBack" onclick="previousQuestion()">← Back</button>
              <button class="primary-btn" id="quizNext" onclick="nextQuestion()">Next →</button>
            </div>
          </div>

          <div id="quizResult" class="panel hidden"></div>
        </section>

        <!-- CAREERS -->
        <section id="page-careers" class="page hidden">
          <div class="page-header">
            <div>
              <h2>Explore Careers 💡</h2>
              <p>Search, discover and save paths that interest you.</p>
            </div>
          </div>

          <div class="panel">
            <input id="careerSearch" placeholder="🔎 Search careers or skills..." oninput="renderCareers()">
            <select id="careerCategory" onchange="renderCareers()">
              <option value="all">All categories</option>
              <option value="technology">Technology</option>
              <option value="business">Business</option>
              <option value="science">Science</option>
              <option value="creative">Creative</option>
              <option value="people">People and society</option>
              <option value="law">Law and justice</option>
            </select>
            <div id="careerList" class="career-grid"></div>
          </div>

          <div class="panel">
            <div class="section-subtitle"><h3>💜 Your saved careers</h3></div>
            <div id="savedCareers" class="career-grid"></div>
          </div>
        </section>

        <!-- UNIVERSITIES -->
        <section id="page-universities" class="page hidden">
          <div class="page-header">
            <div>
              <h2>University Shortlist 🎓</h2>
              <p>Keep your university research organized in one place.</p>
            </div>
          </div>

          <div class="panel">
            <h3>Add a university</h3>
            <form id="universityForm">
              <div class="form-grid">
                <div>
                  <label for="uniName">University name *</label>
                  <input id="uniName" placeholder="e.g. Stanford University" required>
                </div>
                <div>
                  <label for="uniCountry">Country *</label>
                  <input id="uniCountry" placeholder="e.g. United States" required>
                </div>
                <div>
                  <label for="uniProgram">Program or major</label>
                  <input id="uniProgram" placeholder="e.g. Computer Science">
                </div>
                <div>
                  <label for="uniStatus">Application status</label>
                  <select id="uniStatus">
                    <option>Interested</option>
                    <option>Researching</option>
                    <option>Preparing application</option>
                    <option>Applied</option>
                    <option>Accepted</option>
                  </select>
                </div>
                <div class="full-width">
                  <label for="uniNotes">Notes</label>
                  <textarea id="uniNotes" placeholder="Deadlines, requirements, scholarships..."></textarea>
                </div>
              </div>
              <button class="primary-btn" type="submit">+ Add university</button>
            </form>
          </div>

          <div class="panel">
            <div class="section-subtitle"><h3>My universities</h3><span class="tag" id="universityLabel">0 saved</span></div>
            <div id="universityList" class="university-grid"></div>
          </div>
        </section>

        <!-- TASKS -->
        <section id="page-tasks" class="page hidden">
          <div class="page-header">
            <div>
              <h2>My Task Planner 📝</h2>
              <p>Turn your goals into small, manageable steps.</p>
            </div>
          </div>

          <div class="panel">
            <h3>Add a new task</h3>
            <form id="taskForm">
              <label for="taskInput">What would you like to do?</label>
              <input id="taskInput" placeholder="e.g. Research IELTS requirements" required>
              <label for="taskDate">Due date (optional)</label>
              <input id="taskDate" type="date">
              <button class="primary-btn" type="submit">+ Add task</button>
            </form>
          </div>

          <div class="panel">
            <div class="section-subtitle">
              <h3>Your checklist</h3><span class="tag" id="taskProgressLabel">0 completed</span>
            </div>
            <div class="filter-row">
              <button class="filter-btn active" data-filter="all" onclick="setTaskFilter('all')">All tasks</button>
              <button class="filter-btn" data-filter="pending" onclick="setTaskFilter('pending')">Pending</button>
              <button class="filter-btn" data-filter="done" onclick="setTaskFilter('done')">Completed</button>
            </div>
            <div id="taskList"></div>
            <button class="danger-btn small-btn" style="margin-top:20px" onclick="clearCompletedTasks()">Clear completed</button>
          </div>
        </section>

        <!-- SETTINGS -->
        <section id="page-settings" class="page hidden">
          <div class="page-header">
            <div>
              <h2>Your Settings ⚙️</h2>
              <p>Make your workspace feel like yours.</p>
            </div>
          </div>

          <div class="panel">
            <h3>Personal profile</h3>
            <form id="settingsForm">
              <label for="userName">Your name</label>
              <input id="userName" placeholder="What should we call you?">

              <label for="studyStage">Current study stage</label>
              <select id="studyStage">
                <option>School student</option>
                <option>Preparing for university</option>
                <option>University student</option>
                <option>Exploring career options</option>
              </select>

              <label for="userInterests">Your interests</label>
              <textarea id="userInterests" placeholder="Technology, business, science..."></textarea>

              <button class="primary-btn" type="submit">Save changes ✓</button>
            </form>
          </div>

          <div class="panel">
            <h3>Data management</h3>
            <p style="color:var(--muted);font-size:13px;line-height:1.8">
              Your data is saved in local browser storage on this device.
              It is not synchronized to an online account.
            </p>
            <button class="danger-btn" onclick="clearAllData()">Delete all app data</button>
          </div>
        </section>

      </div>
    </div>
  </div>
</div>

<footer>
  <div class="container">
    <div class="brand" style="justify-content:center;margin-bottom:12px">
      <span class="brand-icon">✦</span> Ventorme
    </div>
    <p>Made for curious minds and ambitious futures. ✨</p>
    <p>Explore at your own pace. Your journey is yours.</p>
  </div>
</footer>

<script>
const CAREERS = [
  {id:"software",name:"Software Engineer",category:"technology",icon:"💻",description:"Design, build and maintain software, applications and digital tools.",skills:"Programming, logic, problem-solving"},
  {id:"data",name:"Data Analyst",category:"technology",icon:"📊",description:"Study data to identify patterns and support decisions.",skills:"Statistics, spreadsheets, analytical thinking"},
  {id:"ai",name:"Machine Learning Engineer",category:"technology",icon:"🤖",description:"Develop systems that learn patterns from data.",skills:"Programming, mathematics, statistics"},
  {id:"cyber",name:"Cybersecurity Specialist",category:"technology",icon:"🔐",description:"Help protect systems, networks and information.",skills:"Networking, investigation, problem-solving"},
  {id:"business",name:"Business Analyst",category:"business",icon:"📈",description:"Understand business problems and suggest improvements.",skills:"Analysis, communication, organization"},
  {id:"finance",name:"Financial Analyst",category:"business",icon:"💰",description:"Analyze financial information to support planning.",skills:"Mathematics, economics, attention to detail"},
  {id:"marketing",name:"Marketing Specialist",category:"business",icon:"📣",description:"Research audiences and develop communication strategies.",skills:"Creativity, research, communication"},
  {id:"scientist",name:"Research Scientist",category:"science",icon:"🔬",description:"Investigate questions through research and experiments.",skills:"Research, critical thinking, patience"},
  {id:"biotech",name:"Biotechnology Specialist",category:"science",icon:"🧬",description:"Apply biology to develop useful technologies and solutions.",skills:"Biology, laboratory skills, analysis"},
  {id:"designer",name:"UX/UI Designer",category:"creative",icon:"🎨",description:"Create clear, useful and enjoyable digital experiences.",skills:"Design, empathy, creative problem-solving"},
  {id:"writer",name:"Content Writer",category:"creative",icon:"✍️",description:"Communicate ideas through clear and engaging writing.",skills:"Writing, research, language"},
  {id:"psychologist",name:"Psychologist",category:"people",icon:"🧠",description:"Study behavior and help people understand psychological challenges.",skills:"Listening, research, empathy"},
  {id:"teacher",name:"Teacher",category:"people",icon:"📚",description:"Help students learn, grow and develop skills.",skills:"Communication, patience, planning"},
  {id:"lawyer",name:"Lawyer",category:"law",icon:"⚖️",description:"Research legal questions and help people understand their rights.",skills:"Reasoning, writing, research"},
  {id:"investigator",name:"Investigator",category:"law",icon:"🔎",description:"Gather and evaluate information to clarify events and evidence.",skills:"Observation, analysis, attention to detail"}
];

const STORAGE_KEY = "ventormeAppDataV2";

const DEFAULT_DATA = () => ({
  name:"",
  stage:"School student",
  interests:"",
  tasks:[],
  universities:[],
  savedCareers:[],
  recommendation:null
});

function loadData() {
  try {
    const saved = JSON.parse(localStorage.getItem(STORAGE_KEY));
    return Object.assign(DEFAULT_DATA(), saved || {});
  } catch {
    return DEFAULT_DATA();
  }
}

let data = loadData();
let taskFilter = "all";
let currentQuizStep = 0;
let quizAnswers = {interest:"",strength:"",environment:"",goal:""};

const QUIZ_QUESTIONS = [
  {
    key:"interest",
    title:"What interests you most?",
    options:[
      ["technology","💻","Technology and programming"],
      ["business","📈","Business and leadership"],
      ["science","🔬","Science and research"],
      ["creative","🎨","Art and creative work"],
      ["people","🧠","Psychology and helping people"],
      ["law","⚖️","Law, justice and investigation"]
    ]
  },
  {
    key:"strength",
    title:"What is one of your strengths?",
    options:[
      ["logic","🧩","Logical thinking"],
      ["communication","💬","Communication"],
      ["creativity","🎨","Creativity"],
      ["analysis","🔎","Research and analysis"],
      ["leadership","🌟","Leadership and organization"]
    ]
  },
  {
    key:"environment",
    title:"What kind of work sounds interesting?",
    options:[
      ["independent","🎧","Independent project work"],
      ["team","🤝","Working with a team"],
      ["research","🧪","Research and experiments"],
      ["people","💗","Working directly with people"]
    ]
  },
  {
    key:"goal",
    title:"What is a future goal?",
    optional:true,
    options:[
      ["study","🎓","Study at university"],
      ["skills","🚀","Build new skills"],
      ["career","🧭","Find a career direction"],
      ["abroad","🌍","Explore studying abroad"]
    ]
  }
];

function saveData() {
  try {
    localStorage.setItem(STORAGE_KEY,JSON.stringify(data));
  } catch {
    showToast("Could not save data in this browser.");
  }
  renderAll();
}

function escapeHTML(value) {
  return String(value ?? "").replace(/[&<>"']/g, char => ({
    "&":"&amp;",
    "<":"&lt;",
    ">":"&gt;",
    '"':"&quot;",
    "'":"&#39;"
  })[char]);
}

function makeId() {
  return Date.now().toString(36)+Math.random().toString(36).slice(2,8);
}

function showToast(message) {
  const toast = document.getElementById("toast");
  toast.textContent = message;
  toast.classList.add("show");
  clearTimeout(showToast.timer);
  showToast.timer = setTimeout(()=>toast.classList.remove("show"),2600);
}

function enterApp(page="home") {
  document.getElementById("landing").classList.add("hidden");
  document.getElementById("app").classList.remove("hidden");
  document.getElementById("topbar").classList.remove("menu-open");
  showPage(page);
  window.scrollTo({top:0,behavior:"smooth"});
}

function goLanding() {
  document.getElementById("app").classList.add("hidden");
  document.getElementById("landing").classList.remove("hidden");
  document.getElementById("topbar").classList.remove("menu-open");
  window.scrollTo({top:0,behavior:"smooth"});
}

function scrollToSection(id) {
  document.getElementById(id)?.scrollIntoView({behavior:"smooth"});
  document.getElementById("topbar").classList.remove("menu-open");
}

function toggleMenu() {
  document.getElementById("topbar").classList.toggle("menu-open");
}

function showPage(page) {
  document.querySelectorAll(".app-content .page").forEach(el=>el.classList.add("hidden"));
  const target = document.getElementById("page-"+page);
  if (target) target.classList.remove("hidden");

  document.querySelectorAll(".sidebar .nav-link[data-page]").forEach(btn=>{
    btn.classList.toggle("active",btn.dataset.page===page);
  });

  renderAll();
  window.scrollTo({top:0,behavior:"smooth"});
}

function renderDashboard() {
  document.getElementById("greeting").textContent =
    data.name ? `Welcome back, ${data.name}! 👋` : "Welcome to Ventorme! 👋";

  document.getElementById("taskCount").textContent =
    data.tasks.filter(task=>!task.done).length;
  document.getElementById("uniCount").textContent = data.universities.length;
  document.getElementById("careerCount").textContent = data.savedCareers.length;

  const rec = document.getElementById("homeRecommendation");
  const tags = document.getElementById("homeCareerTags");

  if (data.recommendation?.careers?.length) {
    rec.textContent = "Based on your quiz answers, here are a few career directions worth exploring.";
    tags.innerHTML = data.recommendation.careers.slice(0,4)
      .map(c=>`<span>${escapeHTML(c.name)}</span>`).join("");
  } else {
    rec.textContent = "Your next chapter starts with curiosity. Take the quiz to discover career ideas.";
    tags.innerHTML = "<span>Explore</span><span>Learn</span><span>Grow</span>";
  }

  const pending = data.tasks.filter(task=>!task.done).slice(0,5);
  document.getElementById("homeTasks").innerHTML = pending.length
    ? pending.map(task=>`
      <div class="task-row">
        <input type="checkbox" aria-label="Complete task" onchange="toggleTask('${task.id}')">
        <div class="task-text">${escapeHTML(task.text)}
          ${task.date?`<small>Due: ${escapeHTML(task.date)}</small>`:""}
        </div>
        <button class="secondary-btn small-btn" onclick="showPage('tasks')">View</button>
      </div>`).join("")
    : '<div class="empty-state"><span>🌷</span>No pending tasks. Add a small goal to get started.</div>';

  const saved = CAREERS.filter(c=>data.savedCareers.includes(c.id));
  document.getElementById("homeSavedCareers").innerHTML = saved.length
    ? saved.slice(0,5).map(c=>`<span>${c.icon} ${escapeHTML(c.name)}</span>`).join("")
    : '<span>No saved careers yet — explore some possibilities!</span>';
}

/* QUIZ */

function renderQuizQuestion() {
  const q = QUIZ_QUESTIONS[currentQuizStep];
  const selected = quizAnswers[q.key];

  document.getElementById("quizStepLabel").textContent =
    `Question ${currentQuizStep+1} of ${QUIZ_QUESTIONS.length}`;
  document.getElementById("quizPercent").textContent =
    `${Math.round((currentQuizStep+1)/QUIZ_QUESTIONS.length*100)}%`;
  document.getElementById("quizProgressFill").style.width =
    `${(currentQuizStep+1)/QUIZ_QUESTIONS.length*100}%`;

  let html = `<div class="quiz-question">
    <h3>${currentQuizStep+1}. ${q.title}</h3>
    <div class="option-grid">
    ${q.options.map(([value,icon,label])=>`
      <button type="button" class="option ${selected===value?"selected":""}"
        onclick="selectQuizAnswer('${q.key}','${value}')">
        <span>${icon}</span>${escapeHTML(label)}
      </button>`).join("")}
    </div>`;

  if (q.key==="goal") {
    html += `<label for="quizGoal">Tell us more (optional)</label>
      <input id="quizGoal" placeholder="For example: study abroad"
      value="${escapeHTML(quizAnswers.goalText||"")}"
      oninput="quizAnswers.goalText=this.value">`;
  }
  html += "</div>";

  document.getElementById("quizQuestionArea").innerHTML = html;
  document.getElementById("quizBack").style.visibility =
    currentQuizStep===0?"hidden":"visible";
  document.getElementById("quizNext").textContent =
    currentQuizStep===QUIZ_QUESTIONS.length-1?"See my results ✨":"Next →";
}

function selectQuizAnswer(key,value) {
  quizAnswers[key]=value;
  renderQuizQuestion();
}

function nextQuestion() {
  const q = QUIZ_QUESTIONS[currentQuizStep];
  if (!quizAnswers[q.key] && !q.optional) {
    showToast("Choose an answer to continue.");
    return;
  }

  if (currentQuizStep<QUIZ_QUESTIONS.length-1) {
    currentQuizStep++;
    renderQuizQuestion();
  } else {
    finishQuiz();
  }
}

function previousQuestion() {
  if (currentQuizStep>0) {
    currentQuizStep--;
    renderQuizQuestion();
  }
}

function finishQuiz() {
  const interest = quizAnswers.interest;
  const strength = quizAnswers.strength;
  const environment = quizAnswers.environment;

  const strengthMatches = {
    logic:["software","ai","cyber","data"],
    communication:["marketing","teacher","lawyer","writer"],
    creativity:["designer","marketing","software","writer"],
    analysis:["data","business","scientist","investigator"],
    leadership:["business","marketing","teacher","lawyer"]
  };

  const preferred = strengthMatches[strength]||[];
  let results = CAREERS.filter(c=>c.category===interest);

  results.sort((a,b)=>{
    let scoreA = preferred.includes(a.id)?2:0;
    let scoreB = preferred.includes(b.id)?2:0;
    if (environment==="research" && ["scientist","data","biotech"].includes(a.id)) scoreA++;
    if (environment==="research" && ["scientist","data","biotech"].includes(b.id)) scoreB++;
    if (environment==="people" && ["psychologist","teacher","lawyer"].includes(a.id)) scoreA++;
    if (environment==="people" && ["psychologist","teacher","lawyer"].includes(b.id)) scoreB++;
    return scoreB-scoreA;
  });

  if (!results.length) results = CAREERS.slice(0,4);
  results = results.slice(0,4);

  data.recommendation = {
    careers:results.map(c=>({id:c.id,name:c.name,category:c.category,description:c.description,skills:c.skills,icon:c.icon})),
    goal:quizAnswers.goalText||quizAnswers.goal||"Explore your possibilities"
  };
  saveData();

  document.getElementById("quizQuestionArea").classList.add("hidden");
  document.getElementById("quizBack").classList.add("hidden");
  document.getElementById("quizNext").classList.add("hidden");

  const result = document.getElementById("quizResult");
  result.classList.remove("hidden");
  result.innerHTML = `
    <div class="recommendation-banner">
      <h3>🌟 Your next possibilities</h3>
      <p>Your answers can help you explore these career directions. They are suggestions, not a fixed prediction.</p>
    </div>
    <div class="career-grid">
      ${results.map(c=>`
        <div class="career-card">
          <div class="feature-icon">${c.icon}</div>
          <span class="tag">${escapeHTML(c.category)}</span>
          <h3>${escapeHTML(c.name)}</h3>
          <p>${escapeHTML(c.description)}</p>
          <p><strong>Useful skills:</strong> ${escapeHTML(c.skills)}</p>
          <button class="primary-btn small-btn" onclick="toggleSavedCareer('${c.id}')">
            ${data.savedCareers.includes(c.id)?"★ Saved":"♡ Save career"}
          </button>
        </div>`).join("")}
    </div>
    <div class="card-actions" style="margin-top:22px">
      <button class="primary-btn" onclick="showPage('careers')">Explore all careers →</button>
      <button class="secondary-btn" onclick="restartQuiz()">Retake quiz</button>
      <button class="secondary-btn" onclick="showPage('home')">Dashboard</button>
    </div>`;

  result.scrollIntoView({behavior:"smooth",block:"start"});
  showToast("Your career suggestions are ready ✨");
}

function restartQuiz() {
  currentQuizStep=0;
  quizAnswers={interest:"",strength:"",environment:"",goal:""};
  document.getElementById("quizQuestionArea").classList.remove("hidden");
  document.getElementById("quizBack").classList.remove("hidden");
  document.getElementById("quizNext").classList.remove("hidden");
  document.getElementById("quizResult").classList.add("hidden");
  renderQuizQuestion();
}

/* CAREERS */

function renderCareers() {
  const search=(document.getElementById("careerSearch")?.value||"").toLowerCase();
  const category=document.getElementById("careerCategory")?.value||"all";

  const results=CAREERS.filter(c=>
    (category==="all"||c.category===category)&&
    (c.name.toLowerCase().includes(search)||
     c.description.toLowerCase().includes(search)||
     c.skills.toLowerCase().includes(search))
  );

  document.getElementById("careerList").innerHTML=results.length
    ?results.map(c=>`
      <article class="career-card">
        <div class="feature-icon">${c.icon}</div>
        <span class="tag">${escapeHTML(c.category)}</span>
        <h3>${escapeHTML(c.name)}</h3>
        <p>${escapeHTML(c.description)}</p>
        <p><strong>Skills:</strong> ${escapeHTML(c.skills)}</p>
        <div class="card-actions">
          <button class="primary-btn small-btn" onclick="toggleSavedCareer('${c.id}')">
            ${data.savedCareers.includes(c.id)?"★ Saved":"♡ Save career"}
          </button>
          <button class="secondary-btn small-btn" onclick="addCareerTask('${c.id}')">+ Research task</button>
        </div>
      </article>`).join("")
    :'<div class="empty-state"><span>🔎</span>No careers found. Try a different search.</div>';

  const saved=CAREERS.filter(c=>data.savedCareers.includes(c.id));
  document.getElementById("savedCareers").innerHTML=saved.length
    ?saved.map(c=>`
      <article class="career-card">
        <span class="tag">${c.icon} ${escapeHTML(c.category)}</span>
        <h3>${escapeHTML(c.name)}</h3>
        <p>${escapeHTML(c.description)}</p>
        <button class="danger-btn small-btn" onclick="toggleSavedCareer('${c.id}')">Remove</button>
      </article>`).join("")
    :'<div class="empty-state"><span>💜</span>Save careers you want to explore later.</div>';
}

function toggleSavedCareer(id) {
  if (data.savedCareers.includes(id)) {
    data.savedCareers=data.savedCareers.filter(item=>item!==id);
    showToast("Career removed from saved list.");
  } else {
    data.savedCareers.push(id);
    showToast("Career saved! 💜");
  }
  saveData();
}

function addCareerTask(id) {
  const career=CAREERS.find(c=>c.id===id);
  if (!career) return;
  data.tasks.push({id:makeId(),text:`Research career: ${career.name}`,date:"",done:false});
  saveData();
  showToast("Research task added to your planner.");
}

/* UNIVERSITIES */

function addUniversity(event) {
  event.preventDefault();

  const university={
    id:makeId(),
    name:document.getElementById("uniName").value.trim(),
    country:document.getElementById("uniCountry").value.trim(),
    program:document.getElementById("uniProgram").value.trim(),
    status:document.getElementById("uniStatus").value,
    notes:document.getElementById("uniNotes").value.trim()
  };

  if (!university.name||!university.country) {
    showToast("Please enter the university and country.");
    return;
  }

  data.universities.push(university);
  document.getElementById("universityForm").reset();
  saveData();
  showToast("University added to your shortlist 🎓");
}

function renderUniversities() {
  document.getElementById("universityLabel").textContent=`${data.universities.length} saved`;

  document.getElementById("universityList").innerHTML=data.universities.length
    ?data.universities.map(uni=>`
      <article class="university-card">
        <span class="tag">🎓 ${escapeHTML(uni.country)}</span>
        <h3>${escapeHTML(uni.name)}</h3>
        ${uni.program?`<p><strong>Program:</strong> ${escapeHTML(uni.program)}</p>`:""}
        <label>Application status</label>
        <select onchange="updateUniversityStatus('${uni.id}',this.value)">
          ${["Interested","Researching","Preparing application","Applied","Accepted"].map(status=>
            `<option ${uni.status===status?"selected":""}>${status}</option>`
          ).join("")}
        </select>
        ${uni.notes?`<p><strong>Notes:</strong> ${escapeHTML(uni.notes)}</p>`:""}
        <button class="danger-btn small-btn" onclick="deleteUniversity('${uni.id}')">Remove</button>
      </article>`).join("")
    :'<div class="empty-state"><span>🎓</span>Your shortlist is waiting to be created. Add a university above.</div>';
}

function updateUniversityStatus(id,status) {
  const uni=data.universities.find(u=>u.id===id);
  if (!uni) return;
  uni.status=status;
  saveData();
  showToast("Application status updated.");
}

function deleteUniversity(id) {
  data.universities=data.universities.filter(u=>u.id!==id);
  saveData();
  showToast("University removed.");
}

/* TASKS */

function addTask(event) {
  event.preventDefault();
  const text=document.getElementById("taskInput").value.trim();
  const date=document.getElementById("taskDate").value;

  if (!text) {
    showToast("Write a task first.");
    return;
  }

  data.tasks.push({id:makeId(),text,date,done:false});
  document.getElementById("taskForm").reset();
  saveData();
  showToast("Task added. You've got this! ✨");
}

function toggleTask(id) {
  const task=data.tasks.find(t=>t.id===id);
  if (!task) return;
  task.done=!task.done;
  saveData();
  if (task.done) showToast("One more step completed! 🌟");
}

function deleteTask(id) {
  data.tasks=data.tasks.filter(t=>t.id!==id);
  saveData();
  showToast("Task deleted.");
}

function setTaskFilter(filter) {
  taskFilter=filter;
  document.querySelectorAll("[data-filter]").forEach(btn=>
    btn.classList.toggle("active",btn.dataset.filter===filter)
  );
  renderTasks();
}

function clearCompletedTasks() {
  if (!data.tasks.some(t=>t.done)) {
    showToast("No completed tasks to clear.");
    return;
  }
  if (confirm("Delete all completed tasks?")) {
    data.tasks=data.tasks.filter(t=>!t.done);
    saveData();
    showToast("Completed tasks cleared.");
  }
}

function renderTasks() {
  const completed=data.tasks.filter(t=>t.done).length;
  document.getElementById("taskProgressLabel").textContent=`${completed} completed`;

  const tasks=data.tasks.filter(t=>
    taskFilter==="all"||
    (taskFilter==="pending"&&!t.done)||
    (taskFilter==="done"&&t.done)
  );

  document.getElementById("taskList").innerHTML=tasks.length
    ?tasks.map(task=>`
      <div class="task-row">
        <input type="checkbox" aria-label="Mark task completed"
          ${task.done?"checked":""} onchange="toggleTask('${task.id}')">
        <div class="task-text ${task.done?"done":""}">
          ${escapeHTML(task.text)}
          ${task.date?`<small>Due: ${escapeHTML(task.date)}</small>`:""}
        </div>
        <button class="danger-btn small-btn" onclick="deleteTask('${task.id}')">Delete</button>
      </div>`).join("")
    :'<div class="empty-state"><span>🌷</span>No tasks here right now.</div>';
}

/* SETTINGS */

function saveSettings(event) {
  event.preventDefault();
  data.name=document.getElementById("userName").value.trim();
  data.stage=document.getElementById("studyStage").value;
  data.interests=document.getElementById("userInterests").value.trim();
  saveData();
  showToast("Your settings have been saved 💜");
}

function loadSettings() {
  document.getElementById("userName").value=data.name||"";
  document.getElementById("studyStage").value=data.stage||"School student";
  document.getElementById("userInterests").value=data.interests||"";
}

function clearAllData() {
  if (!confirm("Delete your saved tasks, universities, careers, quiz results and settings? This cannot be undone.")) return;

  localStorage.removeItem(STORAGE_KEY);
  data=DEFAULT_DATA();
  restartQuiz();
  loadSettings();
  renderAll();
  showPage("home");
  showToast("Your app data has been cleared.");
}

/* ANIMATIONS + INITIALIZATION */

function renderAll() {
  renderDashboard();
  renderCareers();
  renderUniversities();
  renderTasks();
  loadSettings();
}

function initRevealAnimations() {
  const elements=document.querySelectorAll(".reveal");
  if (!("IntersectionObserver" in window)) {
    elements.forEach(el=>el.classList.add("visible"));
    return;
  }

  const observer=new IntersectionObserver(entries=>{
    entries.forEach(entry=>{
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  },{threshold:.12});

  elements.forEach(el=>observer.observe(el));
}

window.addEventListener("scroll",()=>{
  const scrollable=document.documentElement.scrollHeight-window.innerHeight;
  const progress=scrollable>0?window.scrollY/scrollable*100:0;
  document.getElementById("progressBar").style.width=progress+"%";
});

document.getElementById("quizQuestionArea").classList.remove("hidden");
document.getElementById("quizResult").classList.add("hidden");

document.getElementById("universityForm").addEventListener("submit",addUniversity);
document.getElementById("taskForm").addEventListener("submit",addTask);
document.getElementById("settingsForm").addEventListener("submit",saveSettings);

renderQuizQuestion();
renderAll();
initRevealAnimations();
</script>
</body>
</html>
