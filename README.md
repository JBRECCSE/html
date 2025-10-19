<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Starter Website — Responsive Single File</title>
  <meta name="description" content="A clean, responsive single-file website starter with accessible markup, responsive layout, and small JS interactivity." />

  <style>
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#94a3b8; --accent:#06b6d4; --glass: rgba(255,255,255,0.03);
      --max:1100px; --radius:12px; --gap:1.25rem;
      color-scheme: dark;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      background:linear-gradient(180deg,#071021 0%, #071528 60%); color:#e6eef6; -webkit-font-smoothing:antialiased; padding:2rem;
      display:flex; align-items:center; justify-content:center;
    }
    .wrap{width:100%;max-width:var(--max)}

    header{display:flex;align-items:center;justify-content:space-between;gap:1rem;margin-bottom:1.5rem}
    .brand{display:flex;align-items:center;gap:.75rem}
    .logo{width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#7c3aed);display:flex;align-items:center;justify-content:center;font-weight:700}
    nav{display:flex;gap:1rem}
    nav a{color:var(--muted);text-decoration:none;padding:.5rem .65rem;border-radius:8px}
    nav a:hover{color:#fff;background:var(--glass)}

    .hero{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent); padding:2rem;border-radius:var(--radius);display:grid;grid-template-columns:1fr 360px;gap:1.25rem;align-items:center}
    @media (max-width:880px){ .hero{grid-template-columns:1fr; padding:1rem} nav{display:none} }

    .h-title{font-size:clamp(1.5rem,3vw,2.25rem);line-height:1.02;margin:0}
    .h-lead{color:var(--muted);margin-top:.5rem}

    .card{background:linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));padding:1rem;border-radius:10px;border:1px solid rgba(255,255,255,0.03)}

    .features{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-top:1rem}
    @media (max-width:880px){ .features{grid-template-columns:repeat(1,1fr)} }
    .feature{padding:1rem;border-radius:10px;background:var(--card);}
    .f-title{font-weight:600}
    .muted{color:var(--muted);font-size:.95rem}

    .cta{display:flex;gap:.75rem;margin-top:1rem}
    .btn{display:inline-block;padding:.6rem 1rem;border-radius:10px;text-decoration:none;font-weight:600}
    .btn-primary{background:var(--accent);color:#012;}
    .btn-ghost{border:1px solid rgba(255,255,255,0.04);color:var(--muted);background:transparent}

    form{display:flex;flex-direction:column;gap:.5rem}
    input,textarea{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:.6rem;border-radius:8px;color:inherit}
    textarea{min-height:90px}
    .small{font-size:.85rem;color:var(--muted)}

    footer{margin-top:1.25rem;color:var(--muted);text-align:center}

    /* subtle animated underline */
    .link-underline{position:relative}
    .link-underline::after{content:"";position:absolute;height:2px;left:0;right:100%;bottom:-3px;background:linear-gradient(90deg,var(--accent),#7c3aed);transition:right .25s ease}
    .link-underline:hover::after{right:0}

    /* tiny utilities */
    .grid-2{display:grid;grid-template-columns:1fr 1fr;gap:.75rem}
    @media (max-width:600px){ .grid-2{grid-template-columns:1fr} }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo">S</div>
        <div>
          <div style="font-weight:700">StarterSite</div>
          <div style="font-size:.8rem;color:var(--muted)">Simple responsive single-file starter</div>
        </div>
      </div>
      <nav aria-label="Main navigation">
        <a href="#features">Features</a>
        <a href="#pricing">Pricing</a>
        <a href="#contact" class="link-underline">Contact</a>
      </nav>
    </header>

    <main>
      <section class="hero" aria-labelledby="hero-heading">
        <div>
          <h1 id="hero-heading" class="h-title">A clean, responsive website — one file.</h1>
          <p class="h-lead">Ship a professional landing page or prototype quickly. Accessible semantics, responsive layout and tiny JavaScript for interactivity.</p>

          <div class="features" id="features">
            <article class="feature card">
              <div class="f-title">Fast to launch</div>
              <p class="muted">Single file — open in a browser or drop into any web server.</p>
            </article>

            <article class="feature card">
              <div class="f-title">Responsive</div>
              <p class="muted">Mobile-first layout, works on phones, tablets and desktops.</p>
            </article>

            <article class="feature card">
              <div class="f-title">Accessible</div>
              <p class="muted">Semantic HTML and clear focus states for keyboard users.</p>
            </article>

          </div>

          <div class="cta">
            <a class="btn btn-primary" href="#contact">Get in touch</a>
            <a class="btn btn-ghost" href="#pricing">See pricing</a>
          </div>

          <section id="pricing" style="margin-top:1rem">
            <h3 style="margin:0 0 .5rem 0">Pricing</h3>
            <div class="grid-2">
              <div class="card">
                <strong>Free</strong>
                <div class="small muted">Basic prototype for personal projects</div>
              </div>
              <div class="card">
                <strong>Pro — $9 / month</strong>
                <div class="small muted">Custom domain, email form handling, priority support</div>
              </div>
            </div>
          </section>
        </div>

        <aside class="card" aria-label="Contact form">
          <h4 style="margin-top:0">Contact</h4>
          <p class="small muted">Send a quick message — this is a front-end demo so messages don't go anywhere.</p>
          <form id="contactForm" onsubmit="return handleSubmit(event)">
            <input id="name" placeholder="Your name" required />
            <input id="email" type="email" placeholder="Email" required />
            <textarea id="message" placeholder="Message"></textarea>
            <button class="btn btn-primary" type="submit">Send message</button>
            <div id="formResult" class="small muted" aria-live="polite" style="margin-top:.5rem"></div>
          </form>
        </aside>
      </section>

      <section style="margin-top:1rem">
        <h3 style="margin:0 0 .5rem 0">More features</h3>
        <div class="card">
          <ul>
            <li>SEO-friendly meta tags and semantic structure</li>
            <li>Keyboard accessible controls</li>
            <li>Easy to extend with any CSS framework or build tool</li>
          </ul>
        </div>
      </section>

    </main>

    <footer>
      <div class="small muted">Made with ♥ — modify it, reuse it, and ship it. © StarterSite</div>
    </footer>

  </div>

  <script>
    // Minimal form handling — demonstrates progressive enhancement (no network required).
    function handleSubmit(e){
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const message = document.getElementById('message').value.trim();
      const out = document.getElementById('formResult');
      if(!name || !email){ out.textContent = 'Please enter name and a valid email.'; return false; }
      out.textContent = `Thanks, ${name}! Message received (demo).`;
      // In a real site, send via fetch to an API endpoint here.
      return false;
    }

    // Small accessibility helper: focus the contact name if URL has #contact
    if(location.hash === '#contact'){
      const nm = document.getElementById('name'); if(nm) nm.focus();
    }
  </script>
</body>
</html>
