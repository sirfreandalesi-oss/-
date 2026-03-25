<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Binance - سجل الآن واستلم أرباحك</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --gold: #F0B90B;
      --gold-dim: #c99a08;
      --gold-glow: rgba(240,185,11,0.35);
      --black: #0a0a0a;
      --dark: #111111;
      --card: #161616;
      --text: #f5f5f5;
      --muted: #888;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Cairo', sans-serif;
      background: var(--black);
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ─── NOISE OVERLAY ─── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
      opacity: 0.5;
    }

    /* ─── GRID LINES ─── */
    body::after {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(rgba(240,185,11,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(240,185,11,0.03) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }

    /* ─── GLOW ORBS ─── */
    .orb {
      position: fixed;
      border-radius: 50%;
      filter: blur(120px);
      pointer-events: none;
      z-index: 0;
      animation: drift 12s ease-in-out infinite alternate;
    }
    .orb-1 { width: 600px; height: 600px; background: rgba(240,185,11,0.08); top: -200px; right: -200px; }
    .orb-2 { width: 400px; height: 400px; background: rgba(240,185,11,0.05); bottom: -100px; left: -100px; animation-delay: -6s; }

    @keyframes drift {
      from { transform: translate(0,0) scale(1); }
      to   { transform: translate(40px, 30px) scale(1.08); }
    }

    /* ─── NAVBAR ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 20px 60px;
      background: linear-gradient(to bottom, rgba(10,10,10,0.95), transparent);
      backdrop-filter: blur(4px);
    }
    .logo {
      display: flex; align-items: center; gap: 10px;
      font-size: 1.5rem; font-weight: 900; color: var(--gold);
      letter-spacing: -0.5px;
    }
    .logo svg { width: 32px; height: 32px; }
    .nav-badge {
      font-size: 0.75rem; font-weight: 700;
      color: #000;
      background: var(--gold);
      padding: 3px 10px; border-radius: 20px;
    }

    /* ─── HERO ─── */
    .hero {
      position: relative; z-index: 1;
      min-height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      text-align: center;
      padding: 120px 24px 80px;
    }

    .badge-top {
      display: inline-flex; align-items: center; gap: 8px;
      border: 1px solid rgba(240,185,11,0.3);
      background: rgba(240,185,11,0.06);
      color: var(--gold);
      font-size: 0.8rem; font-weight: 700;
      padding: 7px 18px; border-radius: 50px;
      margin-bottom: 36px;
      animation: fadeDown 0.8s ease both;
    }
    .badge-top::before { content: '●'; font-size: 0.5rem; animation: pulse 1.5s ease infinite; }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

    .hero-title {
      font-size: clamp(1.6rem, 4vw, 3rem);
      font-weight: 900;
      line-height: 1.1;
      letter-spacing: -1px;
      animation: fadeUp 0.9s ease 0.2s both;
    }
    .hero-title .line-accent { color: var(--gold); position: relative; display: inline-block; }


    .hero-sub {
      margin-top: 24px;
      font-size: clamp(1rem, 2.5vw, 1.25rem);
      color: var(--muted);
      font-weight: 400;
      max-width: 560px;
      line-height: 1.8;
      animation: fadeUp 0.9s ease 0.4s both;
    }

    /* ─── STATS ROW ─── */
    .stats {
      display: flex; gap: 40px;
      margin-top: 52px;
      animation: fadeUp 0.9s ease 0.6s both;
      flex-wrap: wrap; justify-content: center;
    }
    .stat { text-align: center; }
    .stat-num {
      font-size: 2rem; font-weight: 900; color: var(--gold);
      line-height: 1;
    }
    .stat-label { font-size: 0.75rem; color: var(--muted); margin-top: 4px; font-weight: 700; }
    .stat-div { width: 1px; background: rgba(255,255,255,0.08); align-self: stretch; }

    /* ─── CTA BUTTON ─── */
    .cta-wrap {
      margin-top: 52px;
      animation: fadeUp 0.9s ease 0.8s both;
    }

    .btn-cta {
      display: inline-flex; align-items: center; gap: 14px;
      background: var(--gold);
      color: #000;
      font-family: 'Cairo', sans-serif;
      font-weight: 900;
      font-size: 1.15rem;
      padding: 18px 46px;
      border-radius: 60px;
      border: none; cursor: pointer;
      text-decoration: none;
      position: relative; overflow: hidden;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
      box-shadow: 0 0 40px var(--gold-glow), 0 8px 32px rgba(0,0,0,0.4);
    }
    .btn-cta::before {
      content: '';
      position: absolute; top: 0; left: -100%; width: 100%; height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
      transition: left 0.5s ease;
    }
    .btn-cta:hover::before { left: 100%; }
    .btn-cta:hover {
      transform: translateY(-3px) scale(1.02);
      box-shadow: 0 0 60px var(--gold-glow), 0 16px 48px rgba(0,0,0,0.5);
    }
    .btn-cta:active { transform: translateY(0) scale(0.98); }
    .btn-icon { font-size: 1.2rem; }

    /* ─── FEATURES ─── */
    .features {
      position: relative; z-index: 1;
      padding: 80px 60px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 24px;
      max-width: 1100px; margin: 0 auto;
    }
    .feat-card {
      background: var(--card);
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 20px;
      padding: 36px 32px;
      position: relative; overflow: hidden;
      transition: transform 0.25s ease, border-color 0.25s ease;
    }
    .feat-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0; height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), transparent);
      opacity: 0; transition: opacity 0.3s;
    }
    .feat-card:hover { transform: translateY(-6px); border-color: rgba(240,185,11,0.2); }
    .feat-card:hover::before { opacity: 1; }

    .feat-icon {
      font-size: 2.2rem; margin-bottom: 20px;
      display: inline-flex; align-items: center; justify-content: center;
      width: 60px; height: 60px;
      background: rgba(240,185,11,0.08);
      border-radius: 14px;
    }
    .feat-title { font-size: 1.05rem; font-weight: 900; margin-bottom: 10px; }
    .feat-desc { font-size: 0.875rem; color: var(--muted); line-height: 1.7; font-weight: 400; }

    /* ─── STEPS ─── */
    .steps-section {
      position: relative; z-index: 1;
      padding: 60px 60px 100px;
      max-width: 900px; margin: 0 auto; text-align: center;
    }
    .section-label {
      font-size: 0.8rem; font-weight: 900; letter-spacing: 3px;
      color: var(--gold); text-transform: uppercase; margin-bottom: 14px;
    }
    .section-title { font-size: clamp(1.8rem, 4vw, 2.6rem); font-weight: 900; line-height: 1.2; }
    .steps-grid {
      margin-top: 52px;
      display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
    }
    .step {
      display: flex; flex-direction: column; align-items: center;
      gap: 14px;
    }
    .step-num {
      width: 52px; height: 52px;
      border-radius: 50%;
      border: 2px solid var(--gold);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem; font-weight: 900; color: var(--gold);
      background: rgba(240,185,11,0.05);
      position: relative;
    }
    .step-num::after {
      content: '';
      position: absolute; inset: -6px;
      border-radius: 50%;
      border: 1px dashed rgba(240,185,11,0.2);
    }
    .step-text { font-size: 0.9rem; color: var(--muted); font-weight: 700; }

    /* ─── BOTTOM CTA BANNER ─── */
    .banner {
      position: relative; z-index: 1;
      margin: 0 40px 60px;
      background: linear-gradient(135deg, #1a1500 0%, #1c1200 50%, #0f0e00 100%);
      border: 1px solid rgba(240,185,11,0.2);
      border-radius: 28px;
      padding: 64px 48px;
      text-align: center;
      overflow: hidden;
    }
    .banner::before {
      content: '';
      position: absolute; top: -60px; left: 50%; transform: translateX(-50%);
      width: 300px; height: 200px;
      background: radial-gradient(ellipse, rgba(240,185,11,0.15), transparent 70%);
      pointer-events: none;
    }
    .banner-title { font-size: clamp(1.6rem, 4vw, 2.4rem); font-weight: 900; }
    .banner-sub { margin-top: 12px; color: var(--muted); font-size: 1rem; }
    .banner .btn-cta { margin-top: 36px; }

    /* ─── FOOTER ─── */
    footer {
      position: relative; z-index: 1;
      text-align: center; padding: 28px;
      color: #444; font-size: 0.78rem; border-top: 1px solid rgba(255,255,255,0.04);
    }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      from { opacity:0; transform: translateY(30px); }
      to   { opacity:1; transform: translateY(0); }
    }
    @keyframes fadeDown {
      from { opacity:0; transform: translateY(-20px); }
      to   { opacity:1; transform: translateY(0); }
    }

    /* ─── SCROLL REVEAL ─── */
    .reveal { opacity:0; transform: translateY(40px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.visible { opacity:1; transform: none; }

    @media (max-width: 768px) {
      nav { padding: 16px 24px; }
      .features, .steps-section { padding: 40px 24px; }
      .banner { margin: 0 16px 40px; padding: 40px 24px; }
    }
  </style>
</head>
<body>

  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>

  <!-- NAVBAR -->
  <nav>
    <div class="logo">
      <svg viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M16 2L19.5 5.5L13 12L9.5 8.5L16 2Z" fill="#F0B90B"/>
        <path d="M22.5 8.5L26 12L19.5 18.5L16 15L22.5 8.5Z" fill="#F0B90B"/>
        <path d="M9.5 8.5L13 12L6.5 18.5L3 15L9.5 8.5Z" fill="#F0B90B"/>
        <path d="M16 15L19.5 18.5L16 22L12.5 18.5L16 15Z" fill="#F0B90B"/>
        <path d="M13 19L16 22L19 19L22.5 22.5L16 29L9.5 22.5L13 19Z" fill="#F0B90B"/>
      </svg>
      Binance
    </div>
    <span class="nav-badge">عرض حصري</span>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="badge-top">انضم إلى أكبر منصة تداول في العالم</div>

    <h1 class="hero-title">
      سجّل الآن<br/>وابدأ في<br/>
      <span class="line-accent">استلام الأرباح</span>
    </h1>

    <p class="hero-sub">
      منصة Binance تمنحك أدوات التداول الأكثر تطوراً في العالم.<br/>
      ابدأ رحلتك المالية اليوم واستثمر في مستقبلك.
    </p>

    <div class="stats">
      <div class="stat">
        <div class="stat-num">185M+</div>
        <div class="stat-label">مستخدم نشط</div>
      </div>
      <div class="stat-div"></div>
      <div class="stat">
        <div class="stat-num">350+</div>
        <div class="stat-label">عملة رقمية</div>
      </div>
      <div class="stat-div"></div>
      <div class="stat">
        <div class="stat-num">0.1%</div>
        <div class="stat-label">أقل رسوم تداول</div>
      </div>
    </div>

    <div class="cta-wrap">
      <a
        href="https://www.binance.com/referral/earn-together/refer2earn-usdc/claim?hl=ar&ref=GRO_28502_1OTEK&utm_source=default"
        target="_blank"
        rel="noopener noreferrer"
        class="btn-cta"
      >
        <span class="btn-icon">🚀</span>
        سجل الآن في Binance
      </a>
    </div>
  </section>



  <!-- STEPS -->
  <section class="steps-section reveal">
    <div class="section-label">كيف تبدأ</div>
    <h2 class="section-title">ثلاث خطوات فقط للبدء</h2>
    <div class="steps-grid">
      <div class="step">
        <div class="step-num">١</div>
        <div class="step-text">اضغط على زر التسجيل وأنشئ حسابك المجاني</div>
      </div>
      <div class="step">
        <div class="step-num">٢</div>
        <div class="step-text">تحقق من هويتك بخطوات بسيطة وسريعة</div>
      </div>
      <div class="step">
        <div class="step-num">٣</div>
        <div class="step-text">ابدأ التداول واستلم أرباحك مباشرةً</div>
      </div>
    </div>
  </section>



  <!-- FOOTER -->
  <footer>
    <p>© 2025 Binance. جميع الحقوق محفوظة. التداول ينطوي على مخاطر.</p>
  </footer>

  <script>
    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          setTimeout(() => e.target.classList.add('visible'), i * 100);
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.15 });
    reveals.forEach(el => observer.observe(el));

    // Parallax orbs on mouse move
    document.addEventListener('mousemove', (e) => {
      const x = (e.clientX / window.innerWidth - 0.5) * 30;
      const y = (e.clientY / window.innerHeight - 0.5) * 30;
      document.querySelector('.orb-1').style.transform = `translate(${x}px, ${y}px)`;
      document.querySelector('.orb-2').style.transform = `translate(${-x}px, ${-y}px)`;
    });
  </script>
</body>
</html>
