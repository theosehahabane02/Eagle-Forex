# Eagle-Forex
Website for forex 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Eagle Forex</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --gold: #C9A84C;
    --gold-light: #F0D080;
    --dark: #0A0C10;
    --dark2: #12151B;
    --dark3: #1C2030;
    --white: #F5F3EE;
    --muted: #8A8F9E;
  }
  body { font-family: 'DM Sans', sans-serif; background: var(--dark); color: var(--white); min-height: 100vh; }

  nav { display: flex; align-items: center; justify-content: space-between; padding: 1.2rem 2rem; background: rgba(10,12,16,0.97); border-bottom: 1px solid rgba(201,168,76,0.15); position: sticky; top: 0; z-index: 100; }
  .logo { font-family: 'Bebas Neue', sans-serif; font-size: 1.8rem; letter-spacing: 3px; color: var(--gold); display: flex; align-items: center; gap: 10px; }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a { color: var(--muted); text-decoration: none; font-size: 0.9rem; font-weight: 500; letter-spacing: 0.5px; transition: color 0.2s; cursor: pointer; }
  .nav-links a:hover, .nav-links a.active { color: var(--gold); }
  .nav-cta { background: var(--gold); color: var(--dark); padding: 0.5rem 1.3rem; border-radius: 4px; font-weight: 600; font-size: 0.85rem; border: none; cursor: pointer; letter-spacing: 0.5px; transition: background 0.2s; }
  .nav-cta:hover { background: var(--gold-light); }

  .page { display: none; }
  .page.active { display: block; }

  .ticker { background: var(--gold); color: var(--dark); padding: 0.4rem 0; overflow: hidden; white-space: nowrap; font-size: 0.78rem; font-weight: 700; letter-spacing: 0.5px; }
  .ticker-inner { display: inline-block; animation: ticker 22s linear infinite; }
  @keyframes ticker { from { transform: translateX(0); } to { transform: translateX(-50%); } }

  .hero { min-height: 88vh; display: flex; flex-direction: column; justify-content: center; padding: 4rem 2rem 2rem; position: relative; overflow: hidden; }
  .hero-bg { position: absolute; inset: 0; background: radial-gradient(ellipse 70% 60% at 60% 40%, rgba(201,168,76,0.07) 0%, transparent 70%); pointer-events: none; }
  .hero-grid { position: absolute; inset: 0; background-image: linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px), linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px); background-size: 60px 60px; pointer-events: none; }
  .hero-tag { display: inline-block; background: rgba(201,168,76,0.1); color: var(--gold); border: 1px solid rgba(201,168,76,0.3); padding: 0.35rem 1rem; border-radius: 2px; font-size: 0.78rem; letter-spacing: 2px; text-transform: uppercase; font-weight: 600; margin-bottom: 1.5rem; }
  .hero h1 { font-family: 'Bebas Neue', sans-serif; font-size: clamp(3.5rem, 9vw, 7rem); line-height: 0.95; letter-spacing: 2px; margin-bottom: 1.5rem; max-width: 700px; }
  .hero h1 span { color: var(--gold); }
  .hero p { font-size: 1.05rem; color: var(--muted); max-width: 480px; line-height: 1.7; margin-bottom: 2.5rem; }
  .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn-primary { background: var(--gold); color: var(--dark); padding: 0.85rem 2rem; border-radius: 4px; font-weight: 600; font-size: 0.95rem; border: none; cursor: pointer; transition: all 0.2s; }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-1px); }
  .btn-outline { background: transparent; color: var(--white); padding: 0.85rem 2rem; border-radius: 4px; font-weight: 500; font-size: 0.95rem; border: 1px solid rgba(255,255,255,0.2); cursor: pointer; transition: all 0.2s; }
  .btn-outline:hover { border-color: var(--gold); color: var(--gold); }

  .stats-bar { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 1px; background: rgba(201,168,76,0.1); border-top: 1px solid rgba(201,168,76,0.1); border-bottom: 1px solid rgba(201,168,76,0.1); }
  .stat { padding: 1.5rem 2rem; background: var(--dark); }
  .stat-num { font-family: 'Bebas Neue', sans-serif; font-size: 2.2rem; color: var(--gold); letter-spacing: 1px; }
  .stat-label { font-size: 0.8rem; color: var(--muted); letter-spacing: 0.5px; margin-top: 2px; }

  .section { padding: 4rem 2rem; }
  .section-tag { font-size: 0.75rem; letter-spacing: 3px; text-transform: uppercase; color: var(--gold); font-weight: 600; margin-bottom: 0.75rem; }
  .section-title { font-family: 'Bebas Neue', sans-serif; font-size: clamp(2rem, 5vw, 3rem); letter-spacing: 2px; margin-bottom: 1rem; }

  .features { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1px; background: rgba(201,168,76,0.08); border: 1px solid rgba(201,168,76,0.08); border-radius: 8px; overflow: hidden; margin-top: 2.5rem; }
  .feature { background: var(--dark2); padding: 2rem 1.5rem; }
  .feature-icon { font-size: 1.5rem; margin-bottom: 1rem; }
  .feature h3 { font-size: 1rem; font-weight: 600; margin-bottom: 0.5rem; }
  .feature p { font-size: 0.85rem; color: var(--muted); line-height: 1.6; }

  .lessons-header { padding: 3rem 2rem 1.5rem; border-bottom: 1px solid rgba(201,168,76,0.1); }
  .lessons-header h1 { font-family: 'Bebas Neue', sans-serif; font-size: 2.8rem; letter-spacing: 2px; }
  .filter-bar { display: flex; gap: 0.5rem; margin-top: 1.5rem; flex-wrap: wrap; }
  .filter-btn { padding: 0.4rem 1rem; border-radius: 3px; font-size: 0.8rem; font-weight: 500; border: 1px solid rgba(255,255,255,0.1); background: transparent; color: var(--muted); cursor: pointer; transition: all 0.2s; }
  .filter-btn.active, .filter-btn:hover { border-color: var(--gold); color: var(--gold); background: rgba(201,168,76,0.08); }

  .lessons-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1px; background: rgba(201,168,76,0.08); margin: 1px; }
  .lesson-card { background: var(--dark2); padding: 1.5rem; cursor: pointer; transition: background 0.2s; }
  .lesson-card:hover { background: var(--dark3); }
  .lesson-badge { display: inline-block; padding: 0.25rem 0.6rem; border-radius: 2px; font-size: 0.7rem; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; margin-bottom: 1rem; }
  .badge-free { background: rgba(29,158,117,0.15); color: #4ecca3; border: 1px solid rgba(29,158,117,0.2); }
  .badge-premium { background: rgba(201,168,76,0.12); color: var(--gold); border: 1px solid rgba(201,168,76,0.25); }
  .lesson-card h3 { font-size: 1rem; font-weight: 600; margin-bottom: 0.5rem; line-height: 1.4; }
  .lesson-card p { font-size: 0.82rem; color: var(--muted); line-height: 1.6; margin-bottom: 1rem; }
  .lesson-meta { display: flex; align-items: center; justify-content: space-between; font-size: 0.78rem; color: var(--muted); }

  .contact-wrap { max-width: 600px; margin: 0 auto; padding: 3rem 2rem; }
  .contact-wrap h1 { font-family: 'Bebas Neue', sans-serif; font-size: 2.8rem; letter-spacing: 2px; margin-bottom: 0.5rem; }
  .form-group { margin-bottom: 1.2rem; }
  .form-group label { display: block; font-size: 0.82rem; color: var(--muted); margin-bottom: 0.4rem; }
  .form-group input, .form-group textarea, .form-group select { width: 100%; background: var(--dark2); border: 1px solid rgba(201,168,76,0.15); border-radius: 4px; padding: 0.75rem 1rem; color: var(--white); font-family: 'DM Sans', sans-serif; font-size: 0.9rem; outline: none; transition: border-color 0.2s; }
  .form-group input:focus, .form-group textarea:focus { border-color: var(--gold); }
  .form-group textarea { height: 120px; resize: vertical; }
  .form-group select option { background: var(--dark2); }
  .form-submit { width: 100%; background: var(--gold); color: var(--dark); padding: 0.9rem; border-radius: 4px; font-weight: 700; font-size: 0.95rem; border: none; cursor: pointer; margin-top: 0.5rem; transition: background 0.2s; }
  .form-submit:hover { background: var(--gold-light); }
  .contact-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 2.5rem; }
  .contact-card { background: var(--dark2); border: 1px solid rgba(201,168,76,0.1); border-radius: 6px; padding: 1.2rem; }
  .contact-card .cc-label { font-size: 0.75rem; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 0.4rem; }
  .contact-card .cc-val { font-size: 0.9rem; color: var(--white); font-weight: 500; }
  .form-success { text-align: center; padding: 2rem; }

  .modal-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.85); z-index: 200; display: none; align-items: center; justify-content: center; padding: 1rem; }
  .modal-overlay.open { display: flex; }
  .modal { background: var(--dark2); border: 1px solid rgba(201,168,76,0.2); border-radius: 8px; max-width: 480px; width: 100%; padding: 2rem; position: relative; }
  .modal-close { position: absolute; top: 1rem; right: 1rem; background: none; border: none; color: var(--muted); font-size: 1.2rem; cursor: pointer; }
  .modal h2 { font-family: 'Bebas Neue', sans-serif; font-size: 1.8rem; letter-spacing: 2px; margin-bottom: 0.5rem; }
  .modal p { color: var(--muted); font-size: 0.88rem; margin-bottom: 1.5rem; line-height: 1.6; }
  .modal-cta { width: 100%; background: var(--gold); color: var(--dark); padding: 0.85rem; border-radius: 4px; font-weight: 700; border: none; cursor: pointer; margin-top: 1rem; font-size: 0.95rem; }
  .modal-footer { text-align: center; margin-top: 1rem; font-size: 0.8rem; color: var(--muted); }

  .whatsapp-float { position: fixed; bottom: 1.5rem; right: 1.5rem; background: #25D366; color: white; width: 52px; height: 52px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.5rem; cursor: pointer; box-shadow: 0 4px 20px rgba(37,211,102,0.3); z-index: 99; border: none; transition: transform 0.2s; }
  .whatsapp-float:hover { transform: scale(1.08); }

  @media (max-width: 600px) {
    .nav-links { display: none; }
    .hero h1 { font-size: 3rem; }
    .contact-cards { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="ticker">
  <span class="ticker-inner">
    EUR/USD 1.0842 &#9650;0.12% &nbsp;&nbsp;|&nbsp;&nbsp; GBP/USD 1.2710 &#9660;0.08% &nbsp;&nbsp;|&nbsp;&nbsp; USD/JPY 151.34 &#9650;0.23% &nbsp;&nbsp;|&nbsp;&nbsp; XAU/USD 2,341.50 &#9650;0.47% &nbsp;&nbsp;|&nbsp;&nbsp; USD/ZAR 18.62 &#9660;0.15% &nbsp;&nbsp;|&nbsp;&nbsp; BTC/USD 69,204 &#9650;1.2% &nbsp;&nbsp;|&nbsp;&nbsp; EUR/USD 1.0842 &#9650;0.12% &nbsp;&nbsp;|&nbsp;&nbsp; GBP/USD 1.2710 &#9660;0.08% &nbsp;&nbsp;|&nbsp;&nbsp; USD/JPY 151.34 &#9650;0.23% &nbsp;&nbsp;|&nbsp;&nbsp; XAU/USD 2,341.50 &#9650;0.47% &nbsp;&nbsp;|&nbsp;&nbsp; USD/ZAR 18.62 &#9660;0.15% &nbsp;&nbsp;|&nbsp;&nbsp; BTC/USD 69,204 &#9650;1.2% &nbsp;&nbsp;|&nbsp;&nbsp;
  </span>
</div>

<nav>
  <div class="logo">
    <svg width="28" height="28" viewBox="0 0 32 32" fill="none">
      <path d="M16 2L28 10V22L16 30L4 22V10L16 2Z" stroke="#C9A84C" stroke-width="1.5" fill="none"/>
      <path d="M16 6L10 14H16L13 26L22 14H16L19 6H16Z" fill="#C9A84C"/>
    </svg>
    EAGLE FOREX
  </div>
  <ul class="nav-links">
    <li><a class="active" onclick="showPage('home',this)">Home</a></li>
    <li><a onclick="showPage('lessons',this)">Lessons</a></li>
    <li><a onclick="showPage('contact',this)">Contact</a></li>
  </ul>
  <button class="nav-cta" onclick="openModal()">Join Now</button>
</nav>

<!-- HOME -->
<div id="page-home" class="page active">
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-grid"></div>
    <div class="hero-tag">&#9650; Professional Forex Education</div>
    <h1>Master<br/>The <span>Markets.</span><br/>Trade Smarter.</h1>
    <p>Eagle Forex equips you with real-world trading knowledge &#8212; from reading charts to executing high-probability trades with confidence.</p>
    <div class="hero-btns">
      <button class="btn-primary" onclick="goLessons()">Browse Lessons</button>
      <button class="btn-outline" onclick="openModal()">Get Free Access</button>
    </div>
  </section>

  <div class="stats-bar">
    <div class="stat"><div class="stat-num">500+</div><div class="stat-label">Students Trained</div></div>
    <div class="stat"><div class="stat-num">30+</div><div class="stat-label">Lessons Available</div></div>
    <div class="stat"><div class="stat-num">5+</div><div class="stat-label">Years Experience</div></div>
    <div class="stat"><div class="stat-num">24/7</div><div class="stat-label">Community Support</div></div>
  </div>

  <section class="section">
    <div class="section-tag">Why Eagle Forex</div>
    <div class="section-title">BUILT FOR SERIOUS<br/>TRADERS</div>
    <div class="features">
      <div class="feature"><div class="feature-icon">&#128196;</div><h3>PDF Lesson Library</h3><p>Structured PDF lessons you can study at your own pace, anywhere, anytime.</p></div>
      <div class="feature"><div class="feature-icon">&#128202;</div><h3>Technical Analysis</h3><p>Learn chart patterns, indicators, and price action strategies that actually work.</p></div>
      <div class="feature"><div class="feature-icon">&#128737;</div><h3>Risk Management</h3><p>Protect your capital with professional-grade risk and money management systems.</p></div>
      <div class="feature"><div class="feature-icon">&#129504;</div><h3>Trading Psychology</h3><p>Build the mindset and discipline that separates profitable traders from the rest.</p></div>
    </div>
  </section>
</div>

<!-- LESSONS -->
<div id="page-lessons" class="page">
  <div class="lessons-header">
    <div class="section-tag">Curriculum</div>
    <h1>LESSONS LIBRARY</h1>
    <p style="color:var(--muted);margin-top:0.5rem;font-size:0.9rem;">Free lessons open to all. Premium lessons require membership.</p>
    <div class="filter-bar">
      <button class="filter-btn active" onclick="filterLessons('all',this)">All</button>
      <button class="filter-btn" onclick="filterLessons('free',this)">Free</button>
      <button class="filter-btn" onclick="filterLessons('premium',this)">Premium</button>
      <button class="filter-btn" onclick="filterLessons('beginner',this)">Beginner</button>
      <button class="filter-btn" onclick="filterLessons('intermediate',this)">Intermediate</button>
      <button class="filter-btn" onclick="filterLessons('advanced',this)">Advanced</button>
    </div>
  </div>
  <div class="lessons-grid" id="lessons-grid"></div>
</div>

<!-- CONTACT -->
<div id="page-contact" class="page">
  <div class="contact-wrap">
    <div class="section-tag">Get In Touch</div>
    <h1>CONTACT US</h1>
    <p style="color:var(--muted);margin-bottom:2.5rem;font-size:0.95rem;line-height:1.6;">Have questions about our lessons or membership? Send us a message and we'll get back to you shortly.</p>
    <div id="contact-form">
      <div class="form-group"><label>Full Name</label><input type="text" id="cf-name" placeholder="Your name"/></div>
      <div class="form-group"><label>Email Address</label><input type="email" id="cf-email" placeholder="your@email.com"/></div>
      <div class="form-group"><label>Topic</label>
        <select id="cf-topic">
          <option>General Enquiry</option>
          <option>Membership &amp; Pricing</option>
          <option>Lesson Content</option>
          <option>Technical Support</option>
        </select>
      </div>
      <div class="form-group"><label>Message</label><textarea id="cf-msg" placeholder="Write your message here..."></textarea></div>
      <button class="form-submit" onclick="submitContact()">Send Message</button>
    </div>
    <div id="contact-success" class="form-success" style="display:none;">
      <div style="font-size:3rem;margin-bottom:1rem;">&#9989;</div>
      <h3 style="font-size:1.2rem;color:var(--gold);margin-bottom:0.5rem;">Message Sent!</h3>
      <p style="color:var(--muted);font-size:0.9rem;">Thanks for reaching out. We'll reply within 24 hours.</p>
    </div>
    <div class="contact-cards">
      <div class="contact-card"><div class="cc-label">Email</div><div class="cc-val">info@eagleforex.co.za</div></div>
      <div class="contact-card"><div class="cc-label">WhatsApp</div><div class="cc-val">+27 60 000 0000</div></div>
    </div>
  </div>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="modal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal()">&#10005;</button>
    <h2>GET FREE ACCESS</h2>
    <p>Join Eagle Forex and unlock beginner lessons instantly &#8212; no credit card required.</p>
    <div class="form-group"><label>Full Name</label><input type="text" placeholder="Your name"/></div>
    <div class="form-group" style="margin-top:0.8rem;"><label>Email Address</label><input type="email" placeholder="your@email.com"/></div>
    <button class="modal-cta" onclick="closeModal()">Create Free Account</button>
    <div class="modal-footer">Already a member? <span style="color:var(--gold);cursor:pointer;">Sign in</span></div>
  </div>
</div>

<button class="whatsapp-float" title="Chat on WhatsApp">&#128172;</button>

<script>
var lessons = [
  {id:1,title:"Introduction to Forex Markets",desc:"What forex is, how it works, and why it's the world's largest financial market.",level:"Beginner",tier:"free",pages:12},
  {id:2,title:"Understanding Currency Pairs",desc:"Major, minor, and exotic pairs explained — and how to read a quote.",level:"Beginner",tier:"free",pages:10},
  {id:3,title:"How to Read Candlestick Charts",desc:"Master the language of price action with this essential visual guide.",level:"Beginner",tier:"free",pages:18},
  {id:4,title:"Support & Resistance Levels",desc:"Identify key price zones where buyers and sellers consistently react.",level:"Intermediate",tier:"premium",pages:22},
  {id:5,title:"Trend Lines & Market Structure",desc:"Learn to trade with the trend and spot high-probability setups.",level:"Intermediate",tier:"premium",pages:20},
  {id:6,title:"Risk Management Fundamentals",desc:"Lot sizing, stop losses, and protecting your account from blowouts.",level:"Beginner",tier:"free",pages:15},
  {id:7,title:"Moving Averages Mastery",desc:"Simple, exponential, and weighted — when and how to use each.",level:"Intermediate",tier:"premium",pages:19},
  {id:8,title:"Fibonacci Retracements",desc:"Use golden ratio levels to time entries and set precision targets.",level:"Advanced",tier:"premium",pages:24},
  {id:9,title:"Trading Psychology & Discipline",desc:"Control emotions, stick to your plan, and trade like a professional.",level:"Intermediate",tier:"premium",pages:17},
  {id:10,title:"Building a Trading Plan",desc:"Create your personalised rules-based system for consistent results.",level:"Advanced",tier:"premium",pages:28},
  {id:11,title:"Price Action Strategies",desc:"Trade naked charts using pure price movement — no indicators needed.",level:"Advanced",tier:"premium",pages:32},
  {id:12,title:"Fundamental Analysis Basics",desc:"How news events, central banks, and economic data move the market.",level:"Intermediate",tier:"free",pages:14},
];

var currentFilter = 'all';

function renderLessons(filter) {
  var grid = document.getElementById('lessons-grid');
  var filtered = filter === 'all' ? lessons : lessons.filter(function(l){ return l.tier === filter || l.level.toLowerCase() === filter; });
  grid.innerHTML = filtered.map(function(l){ return '<div class="lesson-card"><span class="lesson-badge '+(l.tier==='free'?'badge-free':'badge-premium')+'">'+(l.tier==='free'?'Free':'Premium')+'</span><h3>'+l.title+'</h3><p>'+l.desc+'</p><div class="lesson-meta"><span>'+l.level+' &bull; '+l.pages+' pages</span><span>'+(l.tier==='premium'?'&#128274;':'&#8595; PDF')+'</span></div></div>'; }).join('');
}

function filterLessons(filter, btn) {
  currentFilter = filter;
  document.querySelectorAll('.filter-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  renderLessons(filter);
}

function showPage(page, linkEl) {
  document.querySelectorAll('.page').forEach(function(p){ p.classList.remove('active'); });
  document.getElementById('page-'+page).classList.add('active');
  document.querySelectorAll('.nav-links a').forEach(function(a){ a.classList.remove('active'); });
  if (linkEl) linkEl.classList.add('active');
  if (page === 'lessons') renderLessons(currentFilter);
  window.scrollTo(0,0);
}

function goLessons() {
  showPage('lessons', document.querySelectorAll('.nav-links a')[1]);
}

function openModal() { document.getElementById('modal').classList.add('open'); }
function closeModal() { document.getElementById('modal').classList.remove('open'); }

function submitContact() {
  if (!document.getElementById('cf-name').value || !document.getElementById('cf-email').value) {
    alert('Please fill in your name and email.');
    return;
  }
  document.getElementById('contact-form').style.display = 'none';
  document.getElementById('contact-success').style.display = 'block';
}

document.getElementById('modal').addEventListener('click', function(e) {
  if (e.target === this) closeModal();
});
</script>
</body>
</html>
