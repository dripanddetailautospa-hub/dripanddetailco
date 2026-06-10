<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#0a0d14">
<meta name="apple-mobile-web-app-capable" content="yes">
<title>Book Now – DRIP & DETAIL AUTO-SPA</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  /* ─── TOKENS ─────────────────────────────────────── */
  :root {
    --bg-deep:    #070a10;
    --bg-mid:     #0d1220;
    --bg-card:    rgba(255,255,255,0.035);
    --gold:       #c9a84c;
    --gold-light: #e8c96e;
    --gold-dim:   rgba(201,168,76,0.18);
    --text-white: #f0ede6;
    --text-muted: rgba(240,237,230,0.5);
    --border:     rgba(201,168,76,0.22);
    --error:      #e05b5b;
    --success:    #4caf82;
    --radius:     14px;
    --font-display: 'Cormorant Garamond', serif;
    --font-body:    'Inter', sans-serif;
  }

  /* ─── RESET ──────────────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; -webkit-tap-highlight-color: transparent; }
  body {
    font-family: var(--font-body);
    background: var(--bg-deep);
    color: var(--text-white);
    min-height: 100vh;
    overflow-x: hidden;
    font-size: 15px;
    line-height: 1.6;
  }

  /* ─── AMBIENT BACKGROUND ─────────────────────────── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background:
      radial-gradient(ellipse 80% 50% at 50% -10%, rgba(201,168,76,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 90% 80%, rgba(13,18,32,0.9) 0%, transparent 70%);
    pointer-events: none; z-index: 0;
  }

  /* ─── LAYOUT ─────────────────────────────────────── */
  .wrapper {
    position: relative; z-index: 1;
    max-width: 520px;
    margin: 0 auto;
    padding: 0 16px 60px;
  }

  /* ─── HEADER ─────────────────────────────────────── */
  .header {
    text-align: center;
    padding: 48px 0 32px;
  }
  .header-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--gold-dim);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 5px 16px;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 20px;
  }
  .header-badge::before { content: '◆'; font-size: 8px; }
  .brand-name {
    font-family: var(--font-display);
    font-size: clamp(28px, 8vw, 38px);
    font-weight: 600;
    letter-spacing: 0.04em;
    line-height: 1.15;
    background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 50%, #a87c2a 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .brand-sub {
    font-size: 11px;
    letter-spacing: 3.5px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-top: 6px;
    font-weight: 400;
  }
  .header-divider {
    display: flex; align-items: center; gap: 12px;
    margin: 24px 0 0;
  }
  .header-divider::before, .header-divider::after {
    content: ''; flex: 1; height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
  }
  .header-divider span { font-size: 9px; letter-spacing: 2px; color: var(--gold); text-transform: uppercase; }

  /* ─── CARD / GLASS ───────────────────────────────── */
  .glass-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    padding: 24px 20px;
    margin-bottom: 16px;
  }
  .section-title {
    font-family: var(--font-display);
    font-size: 18px;
    font-weight: 600;
    color: var(--gold-light);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-title .icon {
    width: 28px; height: 28px;
    background: var(--gold-dim);
    border: 1px solid var(--border);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 13px; flex-shrink: 0;
  }

  /* ─── FORM FIELDS ────────────────────────────────── */
  .field { margin-bottom: 14px; }
  .field label {
    display: block;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 1.2px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 7px;
  }
  .field label .req { color: var(--gold); margin-left: 2px; }
  .field input,
  .field select,
  .field textarea {
    width: 100%;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 10px;
    color: var(--text-white);
    font-family: var(--font-body);
    font-size: 15px;
    padding: 13px 15px;
    outline: none;
    transition: border-color 0.2s, background 0.2s, box-shadow 0.2s;
    -webkit-appearance: none;
    appearance: none;
  }
  .field select {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23c9a84c' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 14px center;
    padding-right: 40px;
    cursor: pointer;
  }
  .field select option { background: #0d1220; color: var(--text-white); }
  .field input:focus,
  .field select:focus,
  .field textarea:focus {
    border-color: var(--gold);
    background: rgba(201,168,76,0.06);
    box-shadow: 0 0 0 3px rgba(201,168,76,0.1);
  }
  .field input::placeholder,
  .field textarea::placeholder { color: rgba(240,237,230,0.25); }
  .field textarea { resize: none; min-height: 80px; line-height: 1.5; }
  .field.has-error input,
  .field.has-error select,
  .field.has-error textarea {
    border-color: var(--error);
    box-shadow: 0 0 0 3px rgba(224,91,91,0.1);
  }
  .field-error {
    font-size: 12px;
    color: var(--error);
    margin-top: 5px;
    display: none;
  }
  .field.has-error .field-error { display: block; }
  .row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }

  /* ─── SERVICE PACKAGES ───────────────────────────── */
  .packages { display: flex; flex-direction: column; gap: 10px; }
  .pkg-card {
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 12px;
    padding: 14px 16px;
    cursor: pointer;
    transition: all 0.2s;
    background: rgba(255,255,255,0.03);
    position: relative;
    overflow: hidden;
  }
  .pkg-card::before {
    content: '';
    position: absolute; left: 0; top: 0; bottom: 0;
    width: 3px;
    background: var(--gold);
    transform: scaleY(0);
    transition: transform 0.2s;
    transform-origin: bottom;
  }
  .pkg-card.selected {
    border-color: var(--gold);
    background: rgba(201,168,76,0.08);
  }
  .pkg-card.selected::before { transform: scaleY(1); }
  .pkg-top {
    display: flex; align-items: center; justify-content: space-between;
    margin-bottom: 2px;
  }
  .pkg-name {
    font-family: var(--font-display);
    font-size: 17px;
    font-weight: 600;
    color: var(--text-white);
  }
  .pkg-price {
    font-size: 16px;
    font-weight: 600;
    color: var(--gold);
  }
  .pkg-desc { font-size: 12px; color: var(--text-muted); line-height: 1.4; }
  .pkg-radio { display: none; }

  /* ─── ADD-ONS ─────────────────────────────────────── */
  .addons { display: flex; flex-direction: column; gap: 8px; margin-top: 12px; }
  .addon-item {
    display: flex; align-items: center;
    background: rgba(255,255,255,0.025);
    border: 1px solid rgba(201,168,76,0.12);
    border-radius: 10px;
    padding: 11px 14px;
    cursor: pointer;
    transition: border-color 0.2s, background 0.2s;
    gap: 12px;
  }
  .addon-item.selected {
    border-color: var(--gold);
    background: rgba(201,168,76,0.07);
  }
  .addon-check {
    width: 18px; height: 18px; flex-shrink: 0;
    border: 1.5px solid rgba(201,168,76,0.35);
    border-radius: 5px;
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s;
  }
  .addon-item.selected .addon-check {
    background: var(--gold);
    border-color: var(--gold);
  }
  .addon-check::after {
    content: '✓';
    font-size: 11px;
    color: #070a10;
    display: none;
    font-weight: 700;
  }
  .addon-item.selected .addon-check::after { display: block; }
  .addon-text { flex: 1; }
  .addon-name { font-size: 13px; font-weight: 500; color: var(--text-white); }
  .addon-price { font-size: 12px; color: var(--gold); margin-top: 1px; }
  .section-error {
    font-size: 12px;
    color: var(--error);
    margin-top: 8px;
    display: none;
  }
  .section-error.visible { display: block; }

  /* ─── PAYMENT ─────────────────────────────────────── */
  .payment-options { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
  .pay-card {
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 12px;
    padding: 14px 8px;
    cursor: pointer;
    text-align: center;
    transition: all 0.2s;
    background: rgba(255,255,255,0.03);
  }
  .pay-card.selected {
    border-color: var(--gold);
    background: rgba(201,168,76,0.08);
  }
  .pay-icon { font-size: 22px; margin-bottom: 5px; }
  .pay-name { font-size: 12px; font-weight: 500; color: var(--text-white); }
  .pay-radio { display: none; }
  .payment-instructions {
    margin-top: 14px;
    background: rgba(201,168,76,0.06);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px;
    display: none;
  }
  .payment-instructions.visible { display: block; }
  .pay-instr-title { font-size: 12px; font-weight: 600; color: var(--gold); margin-bottom: 6px; letter-spacing: 0.5px; }
  .pay-instr-body { font-size: 13px; color: var(--text-muted); line-height: 1.6; }
  .pay-number { font-size: 15px; font-weight: 600; color: var(--text-white); margin: 4px 0; font-variant-numeric: tabular-nums; letter-spacing: 0.5px; }

  /* ─── SUBMIT BUTTON ──────────────────────────────── */
  .btn-submit {
    width: 100%;
    padding: 17px;
    background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 60%, #a87c2a 100%);
    border: none;
    border-radius: var(--radius);
    color: #0a0d14;
    font-family: var(--font-body);
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    cursor: pointer;
    transition: opacity 0.2s, transform 0.15s, box-shadow 0.2s;
    margin-top: 8px;
    box-shadow: 0 4px 24px rgba(201,168,76,0.25);
    position: relative;
    overflow: hidden;
  }
  .btn-submit::after {
    content: '';
    position: absolute; inset: 0;
    background: rgba(255,255,255,0.12);
    opacity: 0;
    transition: opacity 0.2s;
  }
  .btn-submit:hover::after { opacity: 1; }
  .btn-submit:active { transform: scale(0.98); }
  .btn-submit:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    transform: none;
  }
  .btn-submit .spinner {
    display: none;
    width: 18px; height: 18px;
    border: 2px solid rgba(10,13,20,0.3);
    border-top-color: #0a0d14;
    border-radius: 50%;
    animation: spin 0.7s linear infinite;
    margin: 0 auto;
  }
  .btn-submit.loading .spinner { display: block; }
  .btn-submit.loading .btn-text { display: none; }
  @keyframes spin { to { transform: rotate(360deg); } }

  /* ─── SUCCESS SCREEN ─────────────────────────────── */
  #success-screen {
    display: none;
    position: fixed; inset: 0;
    background: var(--bg-deep);
    z-index: 100;
    overflow-y: auto;
    padding: 0 16px 60px;
  }
  #success-screen.visible { display: block; animation: fadeUp 0.5s ease; }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .success-wrapper {
    max-width: 520px;
    margin: 0 auto;
    padding-top: 60px;
    text-align: center;
  }
  .success-icon {
    width: 80px; height: 80px;
    background: linear-gradient(135deg, var(--gold-light), var(--gold));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 36px;
    margin: 0 auto 28px;
    box-shadow: 0 0 40px rgba(201,168,76,0.35);
    animation: pulse 2.5s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 40px rgba(201,168,76,0.35); }
    50% { box-shadow: 0 0 60px rgba(201,168,76,0.55); }
  }
  .success-heading {
    font-family: var(--font-display);
    font-size: 32px;
    font-weight: 700;
    background: linear-gradient(135deg, var(--gold-light), var(--gold));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
  }
  .success-sub {
    font-size: 13px;
    color: var(--text-muted);
    margin-bottom: 28px;
    letter-spacing: 0.3px;
  }
  .booking-id-card {
    background: var(--gold-dim);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 18px;
    margin-bottom: 24px;
  }
  .booking-id-label { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 6px; }
  .booking-id-value {
    font-family: var(--font-display);
    font-size: 28px;
    font-weight: 700;
    color: var(--text-white);
    letter-spacing: 2px;
  }
  .booking-summary {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 24px;
    text-align: left;
  }
  .summary-row {
    display: flex;
    justify-content: space-between;
    padding: 7px 0;
    border-bottom: 1px solid rgba(201,168,76,0.08);
    gap: 12px;
  }
  .summary-row:last-child { border-bottom: none; }
  .summary-key { font-size: 11px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.8px; flex-shrink: 0; }
  .summary-val { font-size: 13px; color: var(--text-white); text-align: right; }
  .success-note {
    font-size: 13px;
    color: var(--text-muted);
    margin-bottom: 24px;
    line-height: 1.7;
    padding: 0 8px;
  }
  .contact-buttons { display: flex; flex-direction: column; gap: 10px; }
  .btn-contact {
    display: flex; align-items: center; justify-content: center;
    gap: 10px;
    padding: 15px;
    border-radius: var(--radius);
    font-family: var(--font-body);
    font-size: 14px;
    font-weight: 600;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.15s;
    border: none; cursor: pointer; width: 100%;
  }
  .btn-contact:active { transform: scale(0.98); }
  .btn-whatsapp { background: #25D366; color: white; }
  .btn-messenger { background: linear-gradient(135deg, #0078FF, #9B59B6); color: white; }
  .btn-call { background: rgba(255,255,255,0.07); color: var(--text-white); border: 1px solid var(--border); }

  /* ─── FOOTER ─────────────────────────────────────── */
  .footer {
    text-align: center;
    padding: 20px 0 0;
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 0.5px;
  }
  .footer a { color: var(--gold); text-decoration: none; }

  /* ─── TOAST ──────────────────────────────────────── */
  .toast {
    position: fixed;
    bottom: 24px; left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: #1e2433;
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 12px 22px;
    font-size: 13px;
    color: var(--text-white);
    white-space: nowrap;
    z-index: 200;
    transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
    box-shadow: 0 8px 32px rgba(0,0,0,0.5);
  }
  .toast.show { transform: translateX(-50%) translateY(0); }

  /* ─── ANIMATIONS ─────────────────────────────────── */
  .glass-card { animation: slideIn 0.4s ease both; }
  .glass-card:nth-child(1) { animation-delay: 0.05s; }
  .glass-card:nth-child(2) { animation-delay: 0.10s; }
  .glass-card:nth-child(3) { animation-delay: 0.15s; }
  .glass-card:nth-child(4) { animation-delay: 0.20s; }
  .glass-card:nth-child(5) { animation-delay: 0.25s; }
  @keyframes slideIn {
    from { opacity: 0; transform: translateY(16px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ─── MISC ───────────────────────────────────────── */
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after { animation: none !important; transition: none !important; }
  }
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg-deep); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 4px; }
  input[type="date"]::-webkit-calendar-picker-indicator {
    filter: invert(0.6) sepia(1) saturate(2) hue-rotate(10deg);
    cursor: pointer;
  }
  input[type="time"]::-webkit-calendar-picker-indicator {
    filter: invert(0.6) sepia(1) saturate(2) hue-rotate(10deg);
    cursor: pointer;
  }
</style>
</head>
<body>

<!-- ░░ BOOKING FORM SCREEN ░░ -->
<div id="booking-screen">
  <div class="wrapper">

    <!-- HEADER -->
    <header class="header">
      <div class="header-badge">Book a Service</div>
      <div class="brand-name">DRIP &amp; DETAIL</div>
      <div class="brand-sub">Auto-Spa · Cavite, Philippines</div>
      <div class="header-divider"><span>Premium Mobile Detailing</span></div>
    </header>

    <!-- SECTION 1: CUSTOMER INFO -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">👤</span> Your Details
      </div>
      <div class="field" id="f-name">
        <label>Full Name <span class="req">*</span></label>
        <input type="text" id="full-name" placeholder="e.g. Juan dela Cruz" autocomplete="name">
        <div class="field-error">Please enter your full name.</div>
      </div>
      <div class="field" id="f-mobile">
        <label>Mobile Number <span class="req">*</span></label>
        <input type="tel" id="mobile" placeholder="09XX XXX XXXX" autocomplete="tel" maxlength="11">
        <div class="field-error">Enter a valid PH mobile number (e.g. 09XXXXXXXXX).</div>
      </div>
      <div class="field" id="f-email">
        <label>Email Address <span style="color:var(--text-muted);font-size:10px;"> — Optional</span></label>
        <input type="email" id="email" placeholder="you@email.com" autocomplete="email">
        <div class="field-error">Enter a valid email address.</div>
      </div>
      <div class="field" id="f-address">
        <label>Complete Service Address <span class="req">*</span></label>
        <textarea id="address" placeholder="House/Unit no., Street, Barangay, Municipality, Cavite" rows="3"></textarea>
        <div class="field-error">Please enter your complete address.</div>
      </div>
    </div>

    <!-- SECTION 2: VEHICLE INFO -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">🚗</span> Vehicle Info
      </div>
      <div class="row">
        <div class="field" id="f-make">
          <label>Make <span class="req">*</span></label>
          <input type="text" id="make" placeholder="e.g. Toyota">
          <div class="field-error">Required.</div>
        </div>
        <div class="field" id="f-model">
          <label>Model <span class="req">*</span></label>
          <input type="text" id="model" placeholder="e.g. Vios">
          <div class="field-error">Required.</div>
        </div>
      </div>
    </div>

    <!-- SECTION 3: SERVICE PACKAGE -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">✨</span> Choose Your Package
      </div>
      <div class="packages" id="packages">
        <label class="pkg-card" data-value="Express Wash – ₱499">
          <input type="radio" name="package" value="Express Wash" class="pkg-radio">
          <div class="pkg-top">
            <span class="pkg-name">Express Wash</span>
            <span class="pkg-price">₱499</span>
          </div>
          <div class="pkg-desc">Quick exterior rinse, foam wash, and dry — back on the road fast.</div>
        </label>
        <label class="pkg-card" data-value="Basic Detail Wash – ₱1,499">
          <input type="radio" name="package" value="Basic Detail Wash" class="pkg-radio">
          <div class="pkg-top">
            <span class="pkg-name">Basic Detail Wash</span>
            <span class="pkg-price">₱1,499</span>
          </div>
          <div class="pkg-desc">Full exterior wash + basic interior vacuum, wipe-down, and window clean.</div>
        </label>
        <label class="pkg-card" data-value="Full Detail Spa – ₱3,999">
          <input type="radio" name="package" value="Full Detail Spa" class="pkg-radio">
          <div class="pkg-top">
            <span class="pkg-name">Full Detail Spa</span>
            <span class="pkg-price">₱3,999</span>
          </div>
          <div class="pkg-desc">Complete exterior + deep interior detailing, clay bar, wax, and odor treatment.</div>
        </label>
      </div>
      <div class="section-error" id="pkg-error">Please select a service package.</div>

      <!-- ADD-ONS -->
      <div style="margin-top:20px;">
        <div style="font-size:11px;letter-spacing:1.2px;text-transform:uppercase;color:var(--text-muted);margin-bottom:10px;font-weight:500;">Add-On Services</div>
        <div class="addons" id="addons">
          <div class="addon-item" data-value="Engine Bay Cleaning – ₱299">
            <div class="addon-check"></div>
            <div class="addon-text">
              <div class="addon-name">Engine Bay Cleaning</div>
              <div class="addon-price">+₱299</div>
            </div>
          </div>
          <div class="addon-item" data-value="Interior Sanitization – ₱199">
            <div class="addon-check"></div>
            <div class="addon-text">
              <div class="addon-name">Interior Sanitization</div>
              <div class="addon-price">+₱199</div>
            </div>
          </div>
          <div class="addon-item" data-value="Headlight Restoration – ₱399">
            <div class="addon-check"></div>
            <div class="addon-text">
              <div class="addon-name">Headlight Restoration</div>
              <div class="addon-price">+₱399</div>
            </div>
          </div>
          <div class="addon-item" data-value="Tire Dressing &amp; Shine – ₱149">
            <div class="addon-check"></div>
            <div class="addon-text">
              <div class="addon-name">Tire Dressing &amp; Shine</div>
              <div class="addon-price">+₱149</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- SECTION 4: SCHEDULE -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">📅</span> Your Schedule
      </div>
      <div class="row">
        <div class="field" id="f-date">
          <label>Preferred Date <span class="req">*</span></label>
          <input type="date" id="pref-date">
          <div class="field-error">Pick a future date.</div>
        </div>
        <div class="field" id="f-time">
          <label>Preferred Time <span class="req">*</span></label>
          <input type="time" id="pref-time" min="07:00" max="18:00">
          <div class="field-error">Select a time.</div>
        </div>
      </div>
    </div>

    <!-- SECTION 5: PAYMENT -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">💳</span> Payment Method
      </div>
      <div class="payment-options" id="payment-options">
        <label class="pay-card" data-value="Cash on Service">
          <input type="radio" name="payment" value="Cash on Service" class="pay-radio">
          <div class="pay-icon">💵</div>
          <div class="pay-name">Cash</div>
        </label>
        <label class="pay-card" data-value="GCash">
          <input type="radio" name="payment" value="GCash" class="pay-radio">
          <div class="pay-icon">🔵</div>
          <div class="pay-name">GCash</div>
        </label>
        <label class="pay-card" data-value="Maya">
          <input type="radio" name="payment" value="Maya" class="pay-radio">
          <div class="pay-icon">🟢</div>
          <div class="pay-name">Maya</div>
        </label>
      </div>
      <div class="section-error" id="pay-error">Please select a payment method.</div>

      <!-- GCash Instructions -->
      <div class="payment-instructions" id="gcash-instructions">
        <div class="pay-instr-title">GCash Payment Instructions</div>
        <div class="pay-instr-body">
          Send payment to:<br>
          <div class="pay-number">0952 472 6921</div>
          Account Name: <strong>Drip &amp; Detail Auto-Spa</strong><br><br>
          Screenshot your GCash receipt and send it to us via WhatsApp after booking.
        </div>
      </div>

      <!-- Maya Instructions -->
      <div class="payment-instructions" id="maya-instructions">
        <div class="pay-instr-title">Maya Payment Instructions</div>
        <div class="pay-instr-body">
          Send payment to:<br>
          <div class="pay-number">0966 257 2400</div>
          Account Name: <strong>Drip &amp; Detail Auto-Spa</strong><br><br>
          Screenshot your Maya receipt and send it to us via WhatsApp after booking.
        </div>
      </div>
    </div>

    <!-- SECTION 6: NOTES -->
    <div class="glass-card">
      <div class="section-title">
        <span class="icon">📝</span> Additional Notes
      </div>
      <div class="field">
        <label>Any special instructions? <span style="color:var(--text-muted);font-size:10px;"> — Optional</span></label>
        <textarea id="notes" placeholder="e.g. Gate code, parking info, specific areas of concern…"></textarea>
      </div>
    </div>

    <!-- SUBMIT -->
    <button class="btn-submit" id="submit-btn" onclick="submitBooking()">
      <div class="btn-text">Confirm Booking</div>
      <div class="spinner"></div>
    </button>

    <!-- FOOTER -->
    <div class="footer">
      <p>📍 Serving all areas within Cavite, Philippines</p>
      <p style="margin-top:6px;">Questions? Call <a href="tel:09662572400">0966 257 2400</a></p>
    </div>

  </div><!-- /wrapper -->
</div><!-- /booking-screen -->


<!-- ░░ SUCCESS SCREEN ░░ -->
<div id="success-screen">
  <div class="success-wrapper">
    <div class="success-icon">✓</div>
    <div class="success-heading">Booking Received</div>
    <div class="success-sub">Thank you for choosing DRIP &amp; DETAIL AUTO-SPA</div>

    <div class="booking-id-card">
      <div class="booking-id-label">Your Booking ID</div>
      <div class="booking-id-value" id="display-booking-id">—</div>
    </div>

    <div class="booking-summary" id="booking-summary"></div>

    <p class="success-note">
      We will contact you shortly to confirm your schedule.<br>
      Our team serves all areas within Cavite, Philippines.
    </p>

    <div class="contact-buttons">
      <a id="wa-link" href="#" class="btn-contact btn-whatsapp" target="_blank" rel="noopener">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        Message on WhatsApp
      </a>
      <a href="https://www.facebook.com/share/1BPDRkFaLB/?mibextid=wwXIfr" class="btn-contact btn-messenger" target="_blank" rel="noopener">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="white"><path d="M12 0C5.373 0 0 4.974 0 11.111c0 3.498 1.744 6.614 4.469 8.652V24l4.088-2.242c1.092.3 2.246.464 3.443.464 6.627 0 12-4.975 12-11.111C24 4.974 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8l3.131 3.259L19.752 8l-6.561 6.963z"/></svg>
        Facebook Messenger
      </a>
      <a href="tel:09662572400" class="btn-contact btn-call">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>
        Call Now · 0966 257 2400
      </a>
    </div>

    <div class="footer" style="margin-top:32px;">
      <a href="#" onclick="resetForm(); return false;">← Book Another Service</a>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>


<script>
/* ─── STATE ─────────────────────────────── */
const ENDPOINT = 'https://script.google.com/macros/s/AKfycbzHkho1igFDWT0_Bj1i2fjRL6RvYFGrcVgyyAe_GdLc7nseuq96V2jqq3aQHqFRCrEg/exec';

/* ─── DATE MIN ───────────────────────────── */
(function () {
  const d = new Date();
  d.setDate(d.getDate() + 1);
  const iso = d.toISOString().split('T')[0];
  document.getElementById('pref-date').setAttribute('min', iso);
})();

/* ─── PACKAGE SELECTION ─────────────────── */
document.querySelectorAll('.pkg-card').forEach(card => {
  card.addEventListener('click', () => {
    document.querySelectorAll('.pkg-card').forEach(c => c.classList.remove('selected'));
    card.classList.add('selected');
    card.querySelector('input').checked = true;
    document.getElementById('pkg-error').classList.remove('visible');
  });
});

/* ─── ADD-ON TOGGLES ────────────────────── */
document.querySelectorAll('.addon-item').forEach(item => {
  item.addEventListener('click', () => item.classList.toggle('selected'));
});

/* ─── PAYMENT SELECTION ─────────────────── */
document.querySelectorAll('.pay-card').forEach(card => {
  card.addEventListener('click', () => {
    document.querySelectorAll('.pay-card').forEach(c => c.classList.remove('selected'));
    card.classList.add('selected');
    card.querySelector('input').checked = true;
    document.getElementById('pay-error').classList.remove('visible');
    const val = card.dataset.value;
    document.getElementById('gcash-instructions').classList.toggle('visible', val === 'GCash');
    document.getElementById('maya-instructions').classList.toggle('visible', val === 'Maya');
  });
});

/* ─── VALIDATION ────────────────────────── */
function validate() {
  let ok = true;
  const fields = [
    { id: 'full-name', fid: 'f-name', check: v => v.trim().length >= 2 },
    { id: 'mobile',    fid: 'f-mobile', check: v => /^09\d{9}$/.test(v.replace(/\s/g,'')) },
    { id: 'email',     fid: 'f-email',  check: v => !v || /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v), optional: true },
    { id: 'address',   fid: 'f-address', check: v => v.trim().length >= 10 },
    { id: 'make',      fid: 'f-make',   check: v => v.trim().length >= 1 },
    { id: 'model',     fid: 'f-model',  check: v => v.trim().length >= 1 },
    { id: 'pref-date', fid: 'f-date',   check: v => { if(!v) return false; return new Date(v) >= new Date(new Date().toDateString()); } },
    { id: 'pref-time', fid: 'f-time',   check: v => !!v },
  ];
  fields.forEach(f => {
    if (f.optional && !document.getElementById(f.id).value) return;
    const val = document.getElementById(f.id).value;
    const valid = f.check(val);
    document.getElementById(f.fid).classList.toggle('has-error', !valid);
    if (!valid) ok = false;
  });
  const pkg = document.querySelector('.pkg-card.selected');
  if (!pkg) { document.getElementById('pkg-error').classList.add('visible'); ok = false; }
  const pay = document.querySelector('.pay-card.selected');
  if (!pay) { document.getElementById('pay-error').classList.add('visible'); ok = false; }
  return ok;
}

/* ─── BOOKING ID ────────────────────────── */
function genBookingId() {
  const now = Date.now();
  const alpha = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
  let rnd = '';
  for (let i = 0; i < 7; i++) rnd += alpha[Math.floor(Math.random() * alpha.length)];
  return 'DD-' + rnd;
}

/* ─── FORMAT DATE/TIME ──────────────────── */
function formatDate(d) {
  if (!d) return '—';
  const dt = new Date(d + 'T00:00:00');
  return dt.toLocaleDateString('en-PH', { weekday: 'short', year: 'numeric', month: 'long', day: 'numeric' });
}
function formatTime(t) {
  if (!t) return '—';
  const [h, m] = t.split(':');
  const d = new Date(); d.setHours(+h, +m);
  return d.toLocaleTimeString('en-PH', { hour: 'numeric', minute: '2-digit', hour12: true });
}

/* ─── SUBMIT ────────────────────────────── */
async function submitBooking() {
  if (!validate()) {
    showToast('⚠️ Please complete all required fields.');
    document.querySelector('.has-error, .section-error.visible')?.scrollIntoView({ behavior: 'smooth', block: 'center' });
    return;
  }

  const btn = document.getElementById('submit-btn');
  btn.classList.add('loading');
  btn.disabled = true;

  const bookingId = genBookingId();
  const timestamp = new Date().toLocaleString('en-PH', { timeZone: 'Asia/Manila' });
  const pkg = document.querySelector('.pkg-card.selected')?.dataset.value || '';
  const addons = [...document.querySelectorAll('.addon-item.selected')].map(a => a.dataset.value).join(', ') || 'None';
  const payment = document.querySelector('.pay-card.selected')?.dataset.value || '';

  const data = {
    bookingId,
    timestamp,
    fullName:  document.getElementById('full-name').value.trim(),
    mobile:    document.getElementById('mobile').value.trim(),
    email:     document.getElementById('email').value.trim(),
    address:   document.getElementById('address').value.trim(),
    vehicleMake:  document.getElementById('make').value.trim(),
    vehicleModel: document.getElementById('model').value.trim(),
    servicePackage: pkg,
    addOns:    addons,
    prefDate:  formatDate(document.getElementById('pref-date').value),
    prefTime:  formatTime(document.getElementById('pref-time').value),
    payment,
    notes:     document.getElementById('notes').value.trim(),
    status:    'Pending Confirmation',
    area:      'Cavite, Philippines',
  };

  try {
    await fetch(ENDPOINT, {
      method: 'POST',
      mode: 'no-cors',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data),
    });
  } catch (e) {
    // no-cors — treat as success; GAS will still receive
  }

  btn.classList.remove('loading');
  btn.disabled = false;
  showSuccess(data, bookingId);
}

/* ─── SHOW SUCCESS ──────────────────────── */
function showSuccess(data, bookingId) {
  document.getElementById('display-booking-id').textContent = bookingId;

  const rows = [
    ['Name',    data.fullName],
    ['Mobile',  data.mobile],
    ['Vehicle', `${data.vehicleMake} ${data.vehicleModel}`],
    ['Service', data.servicePackage],
    ['Add-Ons', data.addOns],
    ['Date',    data.prefDate],
    ['Time',    data.prefTime],
    ['Payment', data.payment],
  ];
  const s = document.getElementById('booking-summary');
  s.innerHTML = rows.map(([k,v]) => `<div class="summary-row"><span class="summary-key">${k}</span><span class="summary-val">${v || '—'}</span></div>`).join('');

  // Build WhatsApp message
  const msg = encodeURIComponent(
    `Hello DRIP & DETAIL AUTO-SPA! 🚗✨\n\n` +
    `Booking ID: ${bookingId}\n` +
    `Name: ${data.fullName}\n` +
    `Phone: ${data.mobile}\n` +
    `Address: ${data.address}\n` +
    `Vehicle: ${data.vehicleMake} ${data.vehicleModel}\n` +
    `Service: ${data.servicePackage}\n` +
    `Add-Ons: ${data.addOns}\n` +
    `Date: ${data.prefDate}\n` +
    `Time: ${data.prefTime}\n` +
    `Payment: ${data.payment}\n\n` +
    `Please confirm my booking. Thank you!`
  );
  document.getElementById('wa-link').href = `https://wa.me/639662572400?text=${msg}`;

  document.getElementById('booking-screen').style.display = 'none';
  const ss = document.getElementById('success-screen');
  ss.classList.add('visible');
  window.scrollTo(0, 0);
}

/* ─── RESET ─────────────────────────────── */
function resetForm() {
  document.getElementById('success-screen').classList.remove('visible');
  document.getElementById('booking-screen').style.display = '';
  document.querySelectorAll('.pkg-card').forEach(c => c.classList.remove('selected'));
  document.querySelectorAll('.addon-item').forEach(c => c.classList.remove('selected'));
  document.querySelectorAll('.pay-card').forEach(c => c.classList.remove('selected'));
  document.querySelectorAll('.field.has-error').forEach(f => f.classList.remove('has-error'));
  document.querySelectorAll('.section-error.visible').forEach(e => e.classList.remove('visible'));
  document.querySelectorAll('.payment-instructions.visible').forEach(e => e.classList.remove('visible'));
  document.getElementById('booking-screen').querySelectorAll('input, textarea').forEach(el => el.value = '');
  window.scrollTo(0, 0);
}

/* ─── TOAST ─────────────────────────────── */
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3000);
}

/* ─── CLEAR ERROR ON INPUT ──────────────── */
document.querySelectorAll('input, textarea, select').forEach(el => {
  el.addEventListener('input', () => {
    el.closest('.field')?.classList.remove('has-error');
  });
});
</script>
</body>
</html>

