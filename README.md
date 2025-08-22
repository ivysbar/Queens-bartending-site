# Queens-bartending-site
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Ivy’s Mobile Bar — Elevated Mobile Bartending</title>
  <meta name="description" content="Ivy’s Mobile Bar brings a bespoke craft-cocktail experience to weddings, parties, and corporate events. Urban, bold, and unforgettable mobile bartending." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&family=Staatliches&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #0d0d0f;        /* dark city night */
      --fg: #f5f5f5;        /* clean white */
      --muted:#9a9a9a;      /* muted grey */
      --brand:#ff3c7d;      /* neon pink */
      --brand-2:#00e0ff;    /* neon cyan */
      --accent:#ffe400;     /* electric yellow */
      --stroke: rgba(255,255,255,.08);
      --shadow: 0 12px 30px rgba(0,0,0,.5);
      --radius: 16px;
    }
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body{
      margin:0; color:var(--fg); background:linear-gradient(135deg, #0d0d0f 0%, #1a1a1f 100%);
      font: 16px/1.6 "Montserrat", system-ui, sans-serif;
      overflow-x:hidden;
    }
    h1, h2, h3 { font-family: "Staatliches", Impact, sans-serif; letter-spacing:1px; text-transform:uppercase; }
    .container { width:min(1140px, 92%); margin-inline:auto; }
    a { color:inherit; text-decoration:none; }
    .btn{ display:inline-flex; align-items:center; gap:.6rem; border:2px solid var(--brand); padding:.9rem 1.2rem; border-radius:999px; background: transparent;
          box-shadow: var(--shadow); color:var(--fg); font-weight:600; text-transform:uppercase; transition:.25s ease; }
    .btn:hover{ background:var(--brand); color:#fff; transform:translateY(-2px); }
    .btn.primary{ border-color: var(--brand-2); color:var(--brand-2); }
    .btn.primary:hover{ background: var(--brand-2); color:#000; }
    .chip{ display:inline-flex; align-items:center; gap:.5rem; padding:.4rem .8rem; border-radius:999px; background: rgba(255,255,255,.08); font-size:.8rem; text-transform:uppercase; font-weight:600; letter-spacing:.5px; color:var(--accent) }

    /* NAV */
    header{ position:sticky; top:0; z-index:50; background:#111; border-bottom:2px solid var(--brand); }
    .nav{ display:flex; align-items:center; justify-content:space-between; padding:1rem 0; }
    .brand{ display:flex; align-items:center; gap:.6rem; font-weight:700; letter-spacing:.5px; font-family:"Staatliches"; font-size:1.2rem; }
    .logo{ width:40px; height:40px; border-radius:50%; background: radial-gradient(circle at 30% 30%, var(--brand), var(--brand-2)); box-shadow:0 0 14px var(--brand); }
    nav ul{ display:flex; gap:1.2rem; list-style:none; margin:0; padding:0; }
    .nav a{ color:var(--muted); font-weight:600; text-transform:uppercase; }
    .nav a:hover{ color:var(--brand); }
    .hamburger{ display:none; background:none; border:none; color:var(--fg); font-size:1.6rem; }
    @media (max-width: 880px){
      nav ul{ display:none; position:absolute; left:0; right:0; top:70px; background:#111; border-bottom:2px solid var(--brand);
              padding:1rem; flex-direction:column; gap:1rem; }
      nav ul.open{ display:flex; }
      .hamburger{ display:block; }
    }

    /* HERO */
    .hero{ position:relative; padding:7rem 0 5rem; background: linear-gradient(180deg, rgba(255,60,125,.15), rgba(0,224,255,.15)), url('https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=1800&auto=format&fit=crop') center/cover no-repeat; }
    .hero-grid{ display:grid; grid-template-columns: 1.1fr .9fr; gap:2rem; align-items:center; }
    @media (max-width: 980px){ .hero-grid{ grid-template-columns: 1fr; } }
    .title{ font-size: clamp(2.8rem, 6vw, 4.6rem); margin:0 0 1rem; color:var(--brand); text-shadow: 0 0 12px rgba(255,60,125,.6); }
    .subtitle{ color:var(--fg); font-size:1.1rem; max-width:55ch; }
    .media img{ width:100%; border-radius: var(--radius); box-shadow:0 0 20px rgba(0,224,255,.5); }

    /* SECTIONS */
    section { padding: 5rem 0; }
    .section-title{ font-size: clamp(1.8rem, 3.2vw, 2.6rem); margin:0 0 1rem; color:var(--brand-2); text-shadow:0 0 8px rgba(0,224,255,.6); }
    .kicker{ color:var(--accent); font-weight:700; text-transform:uppercase; letter-spacing:.2em; font-size:.9rem; }

    /* CARDS */
    .card{ border:2px solid var(--brand); background: rgba(255,255,255,.02); padding:1.4rem; border-radius:var(--radius); box-shadow:0 0 18px rgba(255,60,125,.3); transition:.3s ease; }
    .card:hover{ transform:translateY(-6px) scale(1.02); box-shadow:0 0 30px rgba(0,224,255,.4); }
    .card h3{ margin:.2rem 0 .5rem; font-size:1.3rem; color:var(--brand); }
    .card p{ color:var(--muted); margin:0 0 .6rem }

    /* PRICING */
    .price{ font-size:2.2rem; font-weight:700; margin:.6rem 0 1rem; color:var(--accent); text-shadow:0 0 6px rgba(255,228,0,.6); }
    .features li{ display:flex; align-items:flex-start; gap:.6rem; color:var(--fg); }
    .dot{ width:10px; height:10px; border-radius:50%; background:linear-gradient(135deg, var(--brand), var(--brand-2)); margin-top:.5rem; }

    /* GALLERY */
    .gallery{ display:grid; grid-template-columns: repeat(3, 1fr); gap:.8rem }
    .gallery .g{ border-radius:14px; overflow:hidden; border:2px solid var(--brand-2); }
    .gallery img{ width:100%; height:100%; object-fit:cover; display:block; transition:.3s; }
    .gallery img:hover{ transform:scale(1.08); filter:brightness(1.2); }

    /* TESTIMONIALS */
    .quote p{ font-style:italic; color:var(--fg) }
    .quote
