<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SubZero — Stop Paying for Things You Forgot</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #0D1B2A;
    --navy-mid: #162435;
    --navy-light: #1E3148;
    --off-white: #F0EEE9;
    --mint: #00E5A0;
    --mint-dim: #00b87e;
    --slate: #8A9BB0;
    --red: #E84855;
    --card-bg: #162435;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--navy);
    color: var(--off-white);
    font-family: 'Inter', sans-serif;
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 24px 48px;
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(13, 27, 42, 0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }

  .logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 22px;
    letter-spacing: -0.5px;
    color: var(--off-white);
  }
  .logo span { color: var(--mint); }

  nav a.nav-cta {
    background: var(--mint);
    color: var(--navy);
    font-family: 'Inter', sans-serif;
    font-weight: 600;
    font-size: 14px;
    padding: 10px 22px;
    border-radius: 6px;
    text-decoration: none;
    transition: background 0.2s;
  }
  nav a.nav-cta:hover { background: var(--mint-dim); }

  /* HERO */
  .hero {
    max-width: 860px;
    margin: 0 auto;
    padding: 96px 24px 80px;
    text-align: center;
  }

  .leak-ticker {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 48px;
    align-items: center;
  }

  .ticker-row {
    display: flex;
    align-items: center;
    gap: 12px;
    background: rgba(232, 72, 85, 0.08);
    border: 1px solid rgba(232, 72, 85, 0.2);
    border-radius: 8px;
    padding: 10px 20px;
    font-family: 'Inter', sans-serif;
    font-size: 14px;
    color: var(--slate);
    opacity: 0;
    transform: translateY(6px);
    animation: fadeSlideIn 0.4s ease forwards;
  }

  .ticker-row:nth-child(1) { animation-delay: 0.1s; }
  .ticker-row:nth-child(2) { animation-delay: 0.5s; }
  .ticker-row:nth-child(3) { animation-delay: 0.9s; }
  .ticker-row:nth-child(4) { animation-delay: 1.3s; }
  .ticker-row:nth-child(5) { animation-delay: 1.7s; }

  @keyframes fadeSlideIn {
    to { opacity: 1; transform: translateY(0); }
  }

  .ticker-name {
    flex: 1;
    text-align: left;
    font-weight: 500;
    color: var(--off-white);
  }

  .ticker-date { color: var(--slate); font-size: 12px; }

  .ticker-amount {
    color: var(--red);
    font-weight: 600;
    font-size: 15px;
    min-width: 60px;
    text-align: right;
  }

  .ticker-badge {
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.6px;
    background: rgba(232, 72, 85, 0.15);
    color: var(--red);
    padding: 3px 8px;
    border-radius: 4px;
  }

  .hero-eyebrow {
    font-family: 'Inter', sans-serif;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeSlideIn 0.4s ease 2.1s forwards;
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(38px, 6vw, 68px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -2px;
    color: var(--off-white);
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeSlideIn 0.5s ease 2.3s forwards;
  }

  h1 em {
    font-style: normal;
    color: var(--mint);
  }

  .hero-sub {
    font-size: 18px;
    color: var(--slate);
    max-width: 520px;
    margin: 0 auto 40px;
    line-height: 1.6;
    opacity: 0;
    animation: fadeSlideIn 0.5s ease 2.5s forwards;
  }

  .hero-sub strong { color: var(--off-white); font-weight: 500; }

  .cta-group {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    opacity: 0;
    animation: fadeSlideIn 0.5s ease 2.7s forwards;
  }

  .cta-form {
    display: flex;
    gap: 8px;
    width: 100%;
    max-width: 440px;
  }

  .cta-form input {
    flex: 1;
    background: var(--navy-light);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 8px;
    padding: 14px 18px;
    font-size: 15px;
    color: var(--off-white);
    font-family: 'Inter', sans-serif;
    outline: none;
    transition: border-color 0.2s;
  }

  .cta-form input::placeholder { color: var(--slate); }
  .cta-form input:focus { border-color: var(--mint); }

  .cta-form button {
    background: var(--mint);
    color: var(--navy);
    border: none;
    border-radius: 8px;
    padding: 14px 24px;
    font-size: 15px;
    font-weight: 700;
    font-family: 'Syne', sans-serif;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    white-space: nowrap;
  }

  .cta-form button:hover { background: var(--mint-dim); }
  .cta-form button:active { transform: scale(0.98); }

  .cta-note {
    font-size: 12px;
    color: var(--slate);
  }

  /* SOCIAL PROOF */
  .social-proof {
    text-align: center;
    padding: 32px 24px 64px;
    opacity: 0;
    animation: fadeSlideIn 0.5s ease 3s forwards;
  }

  .social-proof p {
    font-size: 13px;
    color: var(--slate);
    margin-bottom: 16px;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    font-weight: 600;
  }

  .avatars {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: -8px;
  }

  .avatar {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    border: 2px solid var(--navy);
    margin-left: -8px;
    font-size: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
  }

  .avatar:first-child { margin-left: 0; }
  .a1 { background: #5B8CFF; }
  .a2 { background: #FF7B54; }
  .a3 { background: #A855F7; }
  .a4 { background: #F59E0B; }
  .a5 { background: #10B981; }

  .waitlist-count {
    margin-left: 12px;
    font-size: 14px;
    color: var(--off-white);
    font-weight: 500;
  }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: linear-gradient(to right, transparent, rgba(255,255,255,0.07), transparent);
    margin: 0 48px;
  }

  /* HOW IT WORKS */
  .how {
    max-width: 900px;
    margin: 0 auto;
    padding: 80px 24px;
  }

  .section-label {
    font-size: 12px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: var(--mint);
    margin-bottom: 16px;
    text-align: center;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 4vw, 42px);
    font-weight: 700;
    letter-spacing: -1px;
    text-align: center;
    margin-bottom: 56px;
    line-height: 1.15;
  }

  .steps {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
  }

  .step {
    background: var(--card-bg);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    padding: 28px;
  }

  .step-icon {
    width: 44px;
    height: 44px;
    border-radius: 10px;
    background: rgba(0, 229, 160, 0.1);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    margin-bottom: 16px;
  }

  .step h3 {
    font-family: 'Syne', sans-serif;
    font-size: 17px;
    font-weight: 700;
    margin-bottom: 8px;
    letter-spacing: -0.3px;
  }

  .step p {
    font-size: 14px;
    color: var(--slate);
    line-height: 1.6;
  }

  /* SAVINGS COUNTER */
  .savings-strip {
    background: var(--navy-mid);
    border-top: 1px solid rgba(255,255,255,0.05);
    border-bottom: 1px solid rgba(255,255,255,0.05);
    padding: 48px 24px;
    text-align: center;
  }

  .savings-strip .big-number {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 8vw, 96px);
    font-weight: 800;
    letter-spacing: -3px;
    color: var(--mint);
    line-height: 1;
    margin-bottom: 12px;
  }

  .savings-strip p {
    font-size: 17px;
    color: var(--slate);
    max-width: 400px;
    margin: 0 auto;
  }

  .savings-strip p strong { color: var(--off-white); }

  /* TESTIMONIALS */
  .testimonials {
    max-width: 900px;
    margin: 0 auto;
    padding: 80px 24px;
  }

  .testi-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }

  .testi-card {
    background: var(--card-bg);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    padding: 28px;
  }

  .testi-card blockquote {
    font-size: 15px;
    color: var(--off-white);
    line-height: 1.65;
    margin-bottom: 20px;
    font-style: italic;
  }

  .testi-author {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .testi-avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    font-size: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    flex-shrink: 0;
  }

  .testi-name { font-size: 14px; font-weight: 600; color: var(--off-white); }
  .testi-handle { font-size: 12px; color: var(--slate); }

  .testi-savings {
    margin-left: auto;
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--mint);
  }

  /* FINAL CTA */
  .final-cta {
    text-align: center;
    padding: 80px 24px 100px;
    max-width: 600px;
    margin: 0 auto;
  }

  .final-cta h2 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(30px, 5vw, 48px);
    font-weight: 800;
    letter-spacing: -1.5px;
    line-height: 1.1;
    margin-bottom: 16px;
  }

  .final-cta p {
    color: var(--slate);
    font-size: 16px;
    margin-bottom: 36px;
  }

  .final-cta .cta-form {
    margin: 0 auto;
  }

  /* FOOTER */
  footer {
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 28px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  footer .logo { font-size: 18px; }
  footer p { font-size: 13px; color: var(--slate); }

  /* SUCCESS STATE */
  .success-msg {
    display: none;
    background: rgba(0, 229, 160, 0.1);
    border: 1px solid rgba(0, 229, 160, 0.3);
    border-radius: 8px;
    padding: 14px 20px;
    color: var(--mint);
    font-size: 14px;
    font-weight: 500;
    text-align: center;
    max-width: 440px;
    margin: 0 auto;
  }

  /* RESPONSIVE */
  @media (max-width: 700px) {
    nav { padding: 18px 20px; }
    .steps { grid-template-columns: 1fr; }
    .testi-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 8px; text-align: center; }
    .divider { margin: 0 20px; }
  }

  @media (prefers-reduced-motion: reduce) {
    .ticker-row, .hero-eyebrow, h1, .hero-sub, .cta-group, .social-proof {
      opacity: 1;
      transform: none;
      animation: none;
    }
  }
</style>
</head>
<body>

<nav>
  <div class="logo">Sub<span>Zero</span></div>
  <a href="#waitlist" class="nav-cta">Join waitlist</a>
</nav>

<!-- HERO -->
<section class="hero">
  <!-- Animated subscription leak ticker -->
  <div class="leak-ticker">
    <div class="ticker-row">
      <span class="ticker-name">Adobe Creative Cloud</span>
      <span class="ticker-date">Last used 8 months ago</span>
      <span class="ticker-amount">−$54.99</span>
      <span class="ticker-badge">forgotten</span>
    </div>
    <div class="ticker-row">
      <span class="ticker-name">Duolingo Plus</span>
      <span class="ticker-date">Last used 5 months ago</span>
      <span class="ticker-amount">−$6.99</span>
      <span class="ticker-badge">forgotten</span>
    </div>
    <div class="ticker-row">
      <span class="ticker-name">Calm Premium</span>
      <span class="ticker-date">Last used 11 months ago</span>
      <span class="ticker-amount">−$69.99/yr</span>
      <span class="ticker-badge">forgotten</span>
    </div>
    <div class="ticker-row">
      <span class="ticker-name">Notion Team Plan</span>
      <span class="ticker-date">Last used 3 months ago</span>
      <span class="ticker-amount">−$16.00</span>
      <span class="ticker-badge">forgotten</span>
    </div>
    <div class="ticker-row">
      <span class="ticker-name">LinkedIn Premium</span>
      <span class="ticker-date">Last used 6 months ago</span>
      <span class="ticker-amount">−$39.99</span>
      <span class="ticker-badge">forgotten</span>
    </div>
  </div>

  <p class="hero-eyebrow">Your money is leaking</p>
  <h1>You're paying for<br><em>things you forgot exist</em></h1>
  <p class="hero-sub">SubZero scans your inbox and surfaces every subscription quietly charging you — so you can <strong>kill the ones you don't need</strong> in seconds.</p>

  <div class="cta-group" id="waitlist">
    <form class="cta-form" name="waitlist" method="POST" onsubmit="handleFormSubmit(event)">
      <input type="hidden" name="form-name" value="waitlist" />
      <input type="email" name="email" id="email-input" placeholder="your@email.com" required />
      <button type="submit">Get early access</button>
    </form>
    <p class="cta-note">Free during beta &nbsp;·&nbsp; No credit card &nbsp;·&nbsp; Unsubscribe anytime</p>
  </div>
</section>

<div class="social-proof">
  <p>Already waiting</p>
  <div class="avatars" style="justify-content:center; display:flex; align-items:center;">
    <div class="avatar a1">J</div>
    <div class="avatar a2">M</div>
    <div class="avatar a3">S</div>
    <div class="avatar a4">R</div>
    <div class="avatar a5">K</div>
    <span class="waitlist-count">+1,240 people on the waitlist</span>
  </div>
</div>

<div class="divider"></div>

<!-- HOW IT WORKS -->
<section class="how">
  <p class="section-label">How it works</p>
  <h2 class="section-title">Three steps to stop the bleed</h2>
  <div class="steps">
    <div class="step">
      <div class="step-icon">📬</div>
      <h3>Connect your inbox</h3>
      <p>SubZero reads your email receipts — it never stores messages, only pulls billing patterns. Read-only, always.</p>
    </div>
    <div class="step">
      <div class="step-icon">🔍</div>
      <h3>We find everything</h3>
      <p>Every recurring charge, free trial about to end, and price increase shows up in a single clean dashboard.</p>
    </div>
    <div class="step">
      <div class="step-icon">⚡</div>
      <h3>Cancel in one tap</h3>
      <p>See something you don't need? Hit cancel. We send the cancellation email on your behalf. Done.</p>
    </div>
  </div>
</section>

<!-- SAVINGS COUNTER -->
<div class="savings-strip">
  <div class="big-number">$312</div>
  <p>Average amount our beta users <strong>stopped wasting</strong> in their first month.</p>
</div>

<!-- TESTIMONIALS -->
<section class="testimonials">
  <p class="section-label">Beta feedback</p>
  <h2 class="section-title">People are already surprised</h2>
  <div class="testi-grid">
    <div class="testi-card">
      <blockquote>"I found a $19/month charge I had been paying for two years for a tool I used once. That's $456 just... gone."</blockquote>
      <div class="testi-author">
        <div class="testi-avatar" style="background:#5B8CFF;">A</div>
        <div>
          <div class="testi-name">Alex M.</div>
          <div class="testi-handle">Product designer, NYC</div>
        </div>
        <div class="testi-savings">+$456</div>
      </div>
    </div>
    <div class="testi-card">
      <blockquote>"Turns out I had three separate password manager subscriptions running at the same time. SubZero caught all of them."</blockquote>
      <div class="testi-author">
        <div class="testi-avatar" style="background:#FF7B54;">S</div>
        <div>
          <div class="testi-name">Sara K.</div>
          <div class="testi-handle">Freelance dev, Austin</div>
        </div>
        <div class="testi-savings">+$180</div>
      </div>
    </div>
    <div class="testi-card">
      <blockquote>"Setup took 90 seconds and it immediately flagged a gym app I signed up for during COVID. Still charging me."</blockquote>
      <div class="testi-author">
        <div class="testi-avatar" style="background:#A855F7;">R</div>
        <div>
          <div class="testi-name">Raj P.</div>
          <div class="testi-handle">Marketing, London</div>
        </div>
        <div class="testi-savings">+$96</div>
      </div>
    </div>
    <div class="testi-card">
      <blockquote>"The UI is so clean. I checked it once, cancelled four things, and I'm done. I don't even need to think about it again."</blockquote>
      <div class="testi-author">
        <div class="testi-avatar" style="background:#10B981;">L</div>
        <div>
          <div class="testi-name">Lena W.</div>
          <div class="testi-handle">Startup founder, Berlin</div>
        </div>
        <div class="testi-savings">+$210</div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- FINAL CTA -->
<section class="final-cta">
  <h2>Find out what's charging you tonight</h2>
  <p>Join the waitlist — free during beta, no card needed.</p>
  <form class="cta-form" name="waitlist-final" method="POST" onsubmit="handleFormSubmit(event)">
    <input type="hidden" name="form-name" value="waitlist" />
    <input type="email" name="email" id="email-input-2" placeholder="your@email.com" required />
    <button type="submit">Join waitlist</button>
  </form>
</section>

<footer>
  <div class="logo">Sub<span>Zero</span></div>
  <p>© 2026 SubZero · <a href="#" style="color:var(--slate); text-decoration:none;">Privacy</a> · Read-only inbox access, always.</p>
</footer>

<script>
  function handleFormSubmit(event) {
    event.preventDefault();
    
    // Get the email value
    const form = event.target;
    const email = form.querySelector('input[name="email"]').value;
    
    // Optional: Save email to localStorage for the thank you page
    localStorage.setItem('userEmail', email);
    
    // Redirect to thank you page
    window.location.href = 'thank-you.html';
  }
</script>

</body>
</html>