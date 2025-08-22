# Queens-bartending-site
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Ivy’s Mobile Bar — Elevated Mobile Bartending</title>
  <meta name="description" content="Ivy’s Mobile Bar brings a bespoke craft‑cocktail experience to weddings, parties, and corporate events. Elevated mobile bartending with style, service, and seasonal menus." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@500;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #0f1116;        /* deep ink */
      --fg: #e6e8ee;        /* soft white */
      --muted:#aeb3c2;      /* slate */
      --brand:#84d6b5;      /* sage-mint */
      --brand-2:#b8a2ff;    /* soft lavender */
      --accent:#f1c27d;     /* honey */
      --card:#151827;       /* glass base */
      --stroke: rgba(255,255,255,.08);
      --shadow: 0 10px 30px rgba(0,0,0,.35), 0 2px 10px rgba(0,0,0,.2);
      --radius: 18px;
    }
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body{
      margin:0; color:var(--fg); background: radial-gradient(60% 80% at 70% 10%, rgba(132,214,181,.12), transparent 60%),
               radial-gradient(50% 80% at 10% 10%, rgba(184,162,255,.14), transparent 60%),
               linear-gradient(180deg, #0c0e14 0%, #0f1116 40%, #0b0d12 100%);
      font: 16px/1.6 "Inter", system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
      overflow-x:hidden;
    }
    h1, h2, h3 { font-family: "Playfair Display", Georgia, serif; line-height:1.15; letter-spacing:.2px; }
    .container { width:min(1120px, 92%); margin-inline:auto; }
    a { color:inherit; text-decoration:none; }
    .btn{ display:inline-flex; align-items:center; gap:.6rem; border:1px solid var(--stroke); padding:.9rem 1.1rem; border-radius:999px; background:linear-gradient(180deg, rgba(255,255,255,.07), rgba(255,255,255,.02));
          box-shadow: var(--shadow); backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px); color:var(--fg); transition:.25s ease; }
    .btn:hover{ transform:translateY(-2px); border-color: rgba(255,255,255,.18); }
    .btn.primary{ background: linear-gradient(180deg, rgba(132,214,181,.22), rgba(132,214,181,.08)); border-color: rgba(132,214,181,.35); }
    .chip{ display:inline-flex; align-items:center; gap:.5rem; padding:.35rem .7rem; border-radius:999px; border:1px solid var(--stroke);
           background: rgba(255,255,255,.02); font-size:.8rem; color:var(--muted) }

    /* NAV */
    header{ position:sticky; top:0; z-index:50; backdrop-filter:saturate(140%) blur(8px); -webkit-backdrop-filter: blur(8px);
            background: linear-gradient(180deg, rgba(15,17,22,.85), rgba(15,17,22,.55)); border-bottom:1px solid var(--stroke); }
    .nav{ display:flex; align-items:center; justify-content:space-between; padding:.9rem 0; }
    .brand{ display:flex; align-items:center; gap:.8rem; font-weight:700; letter-spacing:.4px; }
    .logo{ width:38px; height:38px; border-radius:12px; background: conic-gradient(from 210deg, var(--brand) 10deg, var(--brand-2) 120deg, #222 300deg);
           border:1px solid rgba(255,255,255,.18); box-shadow:0 6px 18px rgba(132,214,181,.18), inset 0 0 22px rgba(255,255,255,.05); }
    nav ul{ display:flex; gap:1.1rem; list-style:none; margin:0; padding:0; }
    .nav a{ color:var(--muted); font-weight:500; padding:.6rem .8rem; border-radius:10px; }
    .nav a:hover{ color:var(--fg); background:rgba(255,255,255,.04) }
    .hamburger{ display:none; background:none; border:none; color:var(--fg); font-size:1.4rem; }
    @media (max-width: 880px){
      nav ul{ display:none; position:absolute; left:0; right:0; top:64px; background:rgba(15,17,22,.98); border-bottom:1px solid var(--stroke);
              padding:1rem; flex-direction:column; gap:.4rem; }
      nav ul.open{ display:flex; }
      .hamburger{ display:block; }
    }

    /* HERO */
    .hero{ position:relative; padding: 6.8rem 0 4.8rem; overflow:hidden; }
    .hero-grid{ display:grid; grid-template-columns: 1.1fr .9fr; gap:2rem; align-items:center; }
    @media (max-width: 980px){ .hero-grid{ grid-template-columns: 1fr; } }
    .title{ font-size: clamp(2.4rem, 5vw, 4rem); margin:0 0 .9rem; }
    .subtitle{ color:var(--muted); font-size:1.1rem; max-width:58ch; }
    .hero-card{ border:1px solid var(--stroke); background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
                border-radius:var(--radius); padding:1rem; box-shadow: var(--shadow); }
    .media{ aspect-ratio: 4 / 3; width:100%; border-radius: calc(var(--radius) - 4px); overflow:hidden; position:relative; }
    .media img{ width:100%; height:100%; object-fit:cover; display:block; filter: saturate(1.05) contrast(1.05); }
    .sparkle{ position:absolute; inset:0; background: radial-gradient(180px 140px at 20% 20%, rgba(184,162,255,.2), transparent 60%),
                                     radial-gradient(220px 180px at 90% 40%, rgba(132,214,181,.18), transparent 60%),
                                     radial-gradient(300px 200px at 50% 90%, rgba(241,194,125,.14), transparent 60%); mix-blend:screen; pointer-events:none; }

    /* SECTIONS */
    section { padding: 4.5rem 0; }
    .section-title{ font-size: clamp(1.6rem, 3vw, 2.2rem); margin:0 0 1rem }
    .kicker{ color:var(--brand); text-transform:uppercase; letter-spacing: .16em; font-weight:700; font-size:.78rem; }

    /* CARDS */
    .grid-3{ display:grid; grid-template-columns: repeat(3, 1fr); gap:1.1rem; }
    @media (max-width: 900px){ .grid-3{ grid-template-columns: 1fr; } }
    .card{ border:1px solid var(--stroke); background:linear-gradient(180deg, rgba(255,255,255,.05), rgba(255,255,255,.02)); padding:1.2rem; border-radius:var(--radius); box-shadow: var(--shadow); }
    .card h3{ margin:.2rem 0 .4rem; font-size:1.2rem }
    .card p{ color:var(--muted); margin:.1rem 0 .6rem }

    /* PRICING */
    .pricing{ display:grid; grid-template-columns: repeat(3, 1fr); gap:1.1rem; }
    @media (max-width: 980px){ .pricing{ grid-template-columns: 1fr; } }
    .price-card{ position:relative; overflow:hidden; }
    .badge{ position:absolute; top:1rem; right:1rem; font-size:.72rem; }
    .price{ font-size:2rem; font-weight:700; margin:.6rem 0 1rem }
    .features{ list-style:none; margin:0; padding:0; display:grid; gap:.5rem }
    .features li{ display:flex; align-items:flex-start; gap:.6rem; }
    .dot{ width:8px; height:8px; border-radius:999px; background:linear-gradient(180deg, var(--brand), var(--brand-2)); margin-top:.47rem }

    /* GALLERY */
    .gallery{ display:grid; grid-template-columns: repeat(6, 1fr); gap:.6rem }
    .gallery .g{ border-radius:14px; overflow:hidden; aspect-ratio: 1 / 1; border:1px solid var(--stroke); }
    .gallery img{ width:100%; height:100%; object-fit:cover; display:block; }
    @media (max-width: 980px){ .gallery{ grid-template-columns: repeat(3, 1fr); } }

    /* TESTIMONIALS */
    .quotes{ display:grid; grid-template-columns: repeat(3, 1fr); gap:1.1rem }
    @media (max-width: 980px){ .quotes{ grid-template-columns: 1fr; } }
    .quote p{ font-style:italic }
    .quote .who{ color:var(--muted); font-size:.95rem }

    /* FORM */
    form{ display:grid; grid-template-columns: repeat(2, 1fr); gap:1rem }
    form .field{ display:flex; flex-direction:column; gap:.4rem }
    form label{ color:var(--muted); font-size:.9rem }
    form input, form select, form textarea{
      background: rgba(255,255,255,.03); color:var(--fg); border:1px solid var(--stroke); border-radius:12px; padding:.85rem .9rem; outline:none;
    }
    form textarea{ min-height:120px; resize:vertical }
    form .full{ grid-column: 1 / -1 }

    /* FOOTER */
    footer{ border-top:1px solid var(--stroke); padding:2.2rem 0; color:var(--muted) }

    /* UTIL */
    .row{ display:flex; align-items:center; gap:1rem; flex-wrap:wrap }
    .spacer{ height: 1.2rem }
    .fade-in{ opacity:0; transform: translateY(14px); transition: .6s ease; }
    .fade-in.show{ opacity:1; transform:none }
  </style>
</head>
<body>
  <!-- NAVBAR -->
  <header>
    <div class="container nav">
      <a href="#top" class="brand" aria-label="Ivy’s Mobile Bar home">
        <div class="logo" aria-hidden="true"></div>
        <span>Ivy’s Mobile Bar</span>
      </a>
      <nav>
        <button class="hamburger" aria-label="Open menu" id="menuBtn">☰</button>
        <ul id="menu">
          <li><a href="#services">Services</a></li>
          <li><a href="#menus">Packages</a></li>
          <li><a href="#gallery">Gallery</a></li>
          <li><a href="#testimonials">Reviews</a></li>
          <li><a href="#booking" class="btn primary" style="padding:.5rem .9rem">Book Now</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <!-- HERO -->
  <main id="top" class="hero">
    <div class="container hero-grid">
      <div>
        <div class="chip">✨ Elevated Mobile Bartending</div>
        <h1 class="title">Craft cocktails, unforgettable service—<br/>we bring the bar to <em>you</em>.</h1>
        <p class="subtitle">From intimate soirées to grand celebrations, Ivy’s Mobile Bar delivers a refined, fully‑insured bar experience with seasonal menus, elegant setups, and certified mixologists.</p>
        <div class="spacer"></div>
        <div class="row">
          <a href="#booking" class="btn primary">Reserve your date →</a>
          <a href="#services" class="btn">Explore services</a>
        </div>
        <div class="spacer"></div>
        <div class="row" aria-label="trust badges">
          <span class="chip">🍸 Tips Certified</span>
          <span class="chip">🧊 Ice & Garnishes</span>
          <span class="chip">🛡️ Fully Insured</span>
        </div>
      </div>
      <div class="hero-card">
        <div class="media">
          <img src="https://images.unsplash.com/photo-1514362545857-3bc16c4c76cc?q=80&w=1600&auto=format&fit=crop" alt="Elegant mobile bar setup with craft cocktails and greenery"/>
          <div class="sparkle" aria-hidden="true"></div>
        </div>
      </div>
    </div>
  </main>

  <!-- SERVICES -->
  <section id="services">
    <div class="container">
      <p class="kicker">Services</p>
      <h2 class="section-title">A polished experience, end to end</h2>
      <div class="grid-3">
        <article class="card fade-in">
          <h3>Full‑Service Bar</h3>
          <p>We handle bar design, setup, breakdown, and staffing with top‑tier equipment and glassware alternatives.</p>
          <div class="row">
            <span class="chip">Mixologists</span>
            <span class="chip">Barback</span>
            <span class="chip">Portable bar</span>
          </div>
        </article>
        <article class="card fade-in">
          <h3>Signature Menus</h3>
          <p>Custom cocktail curation to match your theme—zero‑proof options included. Seasonal syrups and fresh juices.</p>
          <div class="row">
            <span class="chip">Infusions</span>
            <span class="chip">Mocktails</span>
            <span class="chip">Seasonal</span>
          </div>
        </article>
        <article class="card fade-in">
          <h3>Event Add‑Ons</h3>
          <p>Champagne towers, coffee bar, custom napkins, neon signage, garnish displays, and more to elevate your vibe.</p>
          <div class="row">
            <span class="chip">Champagne tower</span>
            <span class="chip">Coffee cart</span>
            <span class="chip">Neon sign</span>
          </div>
        </article>
      </div>
    </div>
  </section>

  <!-- PACKAGES / PRICING -->
  <section id="menus">
    <div class="container">
      <p class="kicker">Packages</p>
      <h2 class="section-title">Simple, transparent options</h2>
      <div class="pricing">
        <div class="card price-card fade-in">
          <span class="badge chip">Best for birthdays</span>
          <h3>Essential</h3>
          <p class="price">$$$</p>
          <ul class="features">
            <li><span class="dot"></span> 1 certified bartender (up to 50 guests)</li>
            <li><span class="dot"></span> Portable bar, tools, ice, mixers & garnishes</li>
            <li><span class="dot"></span> 2 signature cocktails + beer & wine service</li>
          </ul>
          <div class="spacer"></div>
          <a href="#booking" class="btn">Request quote</a>
        </div>
        <div class="card price-card fade-in" style="border-color: rgba(132,214,181,.35); box-shadow: 0 12px 38px rgba(132,214,181,.18), 0 2px 10px rgba(0,0,0,.25);">
          <span class="badge chip" style="background: rgba(132,214,181,.12); color: var(--fg); border-color: rgba(132,214,181,.35)">Most Popular</span>
          <h3>Signature</h3>
          <p class="price">$$$$</p>
          <ul class="features">
            <li><span class="dot"></span> 2 bartenders (up to 120 guests)</li>
            <li><span class="dot"></span> 3 custom cocktails + zero‑proof menu</li>
            <li><span class="dot"></span> Premium mixers, fresh juices & garnishes</li>
          </ul>
          <div class="spacer"></div>
          <a href="#booking" class="btn primary">Book signature</a>
        </div>
        <div class="card price-card fade-in">
          <span class="badge chip">For galas & weddings</span>
          <h3>Luxury</h3>
          <p class="price">Custom</p>
          <ul class="features">
            <li><span class="dot"></span> Bespoke bar build + styled display</li>
            <li><span class="dot"></span> Dedicated lead, barbacks & concierge</li>
            <li><span class="dot"></span> High‑touch menu design + tastings</li>
          </ul>
          <div class="spacer"></div>
          <a href="#booking" class="btn">Plan with Ivy</a>
        </div>
      </div>
    </div>
  </section>

  <!-- GALLERY -->
  <section id="gallery">
    <div class="container">
      <p class="kicker">Gallery</p>
      <h2 class="section-title">A peek at the pour</h2>
      <div class="gallery">
        <div class="g"><img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=1200&auto=format&fit=crop" alt="Bartender stirring a Negroni"/></div>
        <div class="g"><img src="https://images.unsplash.com/photo-1528909514045-2fa4ac7a08ba?q=80&w=1200&auto=format&fit=crop" alt="Champagne tower being poured"/></div>
        <div class="g"><img src="https://images.unsplash.com/photo-1514362545857-3bc16c4c76cc?q=80&w=1200&auto=format&fit=crop" alt="Elegant bar cart with greenery"/></div>
        <div class="g"><img src="https://images.unsplash.com/photo-1514362545857-c0bb2c5d9654?q=80&w=1200&auto=format&fit=crop" alt="Smoked old fashioned presentation"/></div>
        <div class="g"><img src="https://images.unsplash.com/photo-1497534446932-c925b458314e?q=80&w=1200&auto=format&fit=crop" alt="Fresh citrus and garnish display"/></div>
        <div class="g"><img src="https://images.unsplash.com/photo-1504674900247-0877df9cc836?q=80&w=1200&auto=format&fit=crop" alt="Outdoor wedding bar under bistro lights"/></div>
      </div>
    </div>
  </section>

  <!-- TESTIMONIALS -->
  <section id="testimonials">
    <div class="container">
      <p class="kicker">Reviews</p>
      <h2 class="section-title">Guests can’t stop talking about us</h2>
      <div class="quotes">
        <blockquote class="card quote fade-in">
          <p>“The cocktails were stunning and the service was seamless. Our guests were obsessed.”</p>
          <div class="who">— Maya R., Bride</div>
        </blockquote>
        <blockquote class="card quote fade-in">
          <p>“Professional, creative, and so elegant. Ivy turned our backyard into a speakeasy.”</p>
          <div class="who">— Devin S., Private Event</div>
        </blockquote>
        <blockquote class="card quote fade-in">
          <p>“Easy to book, incredible menu, and they handled everything. 10/10 would hire again.”</p>
          <div class="who">— Elise K., Corporate</div>
        </blockquote>
      </div>
    </div>
  </section>

  <!-- BOOKING FORM -->
  <section id="booking">
    <div class="container">
      <p class="kicker">Book</p>
      <h2 class="section-title">Reserve Ivy’s Mobile Bar</h2>
      <p class="subtitle">Tell us about your event and we’ll send a tailored quote within 24 hours.</p>
      <div class="spacer"></div>
      <form id="quoteForm" onsubmit="return handleSubmit(event)">
        <div class="field">
          <label for="name">Full name</label>
          <input id="name" name="name" required placeholder="Your name" />
        </div>
        <div class="field">
          <label for="email">Email</label>
          <input id="email" name="email" type="email" required placeholder="you@example.com" />
        </div>
        <div class="field">
          <label for="phone">Phone</label>
          <input id="phone" name="phone" type="tel" placeholder="(555) 555‑5555" />
        </div>
        <div class="field">
          <label for="date">Event date</label>
          <input id="date" name="date" type="date" required />
        </div>
        <div class="field">
          <label for="guests">Guest count</label>
          <input id="guests" name="guests" type="number" min="1" placeholder="e.g., 80" />
        </div>
        <div class="field">
          <label for="package">Package</label>
          <select id="package" name="package">
            <option>Essential</option>
            <option selected>Signature</option>
            <option>Luxury</option>
          </select>
        </div>
        <div class="field full">
          <label for="details">Event details</label>
          <textarea id="details" name="details" placeholder="Venue address, theme, bar preferences, timing, etc."></textarea>
        </div>
        <div class="field full">
          <button type="submit" class="btn primary">Send request →</button>
        </div>
      </form>
      <p id="formMsg" role="status" aria-live="polite" style="margin-top: .8rem; color: var(--muted)"></p>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="container">
      <div class="row" style="justify-content:space-between; align-items:flex-start">
        <div>
          <div class="brand"><div class="logo" aria-hidden="true"></div><span>Ivy’s Mobile Bar</span></div>
          <div class="spacer"></div>
          <div>Serving weddings, private parties & corporate events.</div>
          <div class="spacer"></div>
          <div class="row"><span class="chip">📍 Your City, ST</span><span class="chip">📧 hello@ivysmobilebar.com</span></div>
        </div>
        <div>
          <div class="row">
            <a href="#services" class="nav-link">Services</a>
            <a href="#menus" class="nav-link">Packages</a>
            <a href="#gallery" class="nav-link">Gallery</a>
            <a href="#booking" class="nav-link">Book</a>
          </div>
          <div class="spacer"></div>
          <small>© <span id="y"></span> Ivy’s Mobile Bar. All rights reserved.</small>
        </div>
      </div>
    </div>
  </footer>

  <!-- SCHEMA -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "FoodEstablishment",
    "name": "Ivy’s Mobile Bar",
    "servesCuisine": "Cocktails, Mocktails, Coffee",
    "areaServed": "Mobile — weddings, private & corporate events",
    "email": "hello@ivysmobilebar.com",
    "url": "https://ivysmobilebar.example",
    "sameAs": [
      "https://instagram.com/ivysmobilebar"
    ]
  }
  </script>

  <!-- JS -->
  <script>
    // Mobile menu toggle
    const menuBtn = document.getElementById('menuBtn');
    const menu = document.getElementById('menu');
    menuBtn?.addEventListener('click', () => menu.classList.toggle('open'));

    // Intersection fade‑ins
    const io = new IntersectionObserver((entries)=>{
      entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('show'); io.unobserve(e.target);} });
    }, { threshold:.15 });
    document.querySelectorAll('.fade-in').forEach(el=>io.observe(el));

    // Footer year
    document.getElementById('y').textContent = new Date().getFullYear();

    // Form handler: create a mailto link with form data
    function handleSubmit(e){
      e.preventDefault();
      const f = e.target;
      const data = new FormData(f);
      const subject = encodeURIComponent(`Booking Request — ${data.get('name')} — ${data.get('date')}`);
      const body = encodeURIComponent([
        `Name: ${data.get('name')}`,
        `Email: ${data.get('email')}`,
        `Phone: ${data.get('phone') || '—'}`,
        `Event Date: ${data.get('date')}`,
        `Guests: ${data.get('guests') || '—'}`,
        `Package: ${data.get('package')}`,
        '',
        'Details:',
        data.get('details') || '—'
      ].join('\n'));
      const mailto = `mailto:hello@ivysmobilebar.com?subject=${subject}&body=${body}`;
      window.location.href = mailto;
      document.getElementById('formMsg').textContent = 'Your email client should open with a pre‑filled request. If not, email us at hello@ivysmobilebar.com.';
      f.reset();
      return false;
    }
  </script>
</body>
</html>

