---
name: Audit HTML Design System
description: Complete CSS/HTML component library and section patterns for Dexfinity AI Ads Audit landing pages — the gold standard from Aquapond audit
type: reference
---

# Dexfinity Audit HTML Design System — Gold Standard

Extracted from `aquapond-audit-v2.html`. Every new audit MUST follow this system exactly.

---

## 1. CSS VARIABLES (root)

```css
:root {
  --dex-blue: #0065F7;
  --dex-navy: #05024E;
  --dex-white: #ffffff;
  --dex-light-bg: #F4F6FC;
  --dex-blue-light: #E8F0FE;
  --dex-blue-10: rgba(0, 101, 247, 0.1);
  --dex-blue-20: rgba(0, 101, 247, 0.2);
  --dex-navy-light: #0A0A6E;
  --dex-text: #1A1A2E;
  --dex-muted: #6B7280;
  --dex-border: #E5E7EB;
  --dex-teal: #16AB8B;
  --dex-orange: #ff7f00;
  --font-primary: 'Questrial', Arial, sans-serif;
  --font-secondary: 'Poppins', Arial, sans-serif;
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 20px;
  --shadow: 0 2px 8px rgba(0, 101, 247, 0.08);
}
```

**Color semantics:**
- Navy = premium feel, hero/pricing bg, high severity
- Blue = CTA, interactive, medium severity, featured card border
- Teal = positive badges, CTA boxes, check marks, solutions
- Orange = urgency, wasted spend, bad metrics, "STE TU" marker
- White with opacity = secondary text on dark backgrounds (0.35-0.6)

---

## 2. SECTION ORDER (mandatory, top to bottom)

1. **Urgency bar** `.urgency` — blue bg, seasonal message, 13px font
2. **Nav** `.nav` — sticky, white+blur, Dexfinity logo min 48px, nav links, hamburger on mobile
3. **Hero** `.hero` — navy bg, decorative circles, hero-badge (cenovka "690EUR"), tagline, h1, sub, hero-stats
4. **Seasonality** `.season-section` — chart-wrap (navy bg SVG), season-urgency cards, season-cta (orange gradient)
5. **O klientovi** — metrics-grid (4 cards: obrat, rast, budget, pain)
6. **Meta Ads** `section#meta .alt` — cat-headers, ads-grid, priority-summary, cta-box
7. **Google Ads** `section#google` — audit-table, findings, priority-summary, cta-box
8. **Hlavne zistenia** `section#findings .alt` — findings with severity bars
9. **Celkove hodnotenie** `.summary-box` — navy bg, summary-grid (4 items with X/10 scores)
10. **Odporucania** `section#recs` — rec-timeline (3 steps)
11. **Budget** `section .alt` — audit-table
12. **Gap analyza** `section#product-gap .alt` — methodology box, audit-table with badges, findings
13. **Bonus insights banner** — blue gradient banner with star icon
14. **Heureka / Social proof** `section#heureka` — metrics-grid, review quote cards, findings
15. **PageSpeed** `section#pagespeed` — metric-cards with orange border for bad scores, finding
16. **Google Moja Firma** `section#gmb .alt` — metrics-grid, combined reviews count, findings
17. **Konkurencia** `section#konkurencia` — audit-table, brand keyword finding
18. **Locked sections** `section#internal-preview` — 3x locked-section (ROAS, Budget leaks, Action plan)
19. **Pricing** `.pricing-section` — wasted spend context box, 2 flip-card pricing cards
20. **Footer** `.footer` — navy bg, logo, audit name, date, "Go Beyond"

---

## 3. COMPLETE CSS COMPONENT LIBRARY

### Nav
```css
.nav {
  position: sticky; top: 0; z-index: 100;
  background: rgba(255,255,255,0.96);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--dex-border);
  padding: 10px 0;
}
.nav .container { display: flex; justify-content: space-between; align-items: center; }
.nav-logo { height: 48px; } /* MINIMUM 48px — logo must be readable with "Go Beyond" tagline */
.nav-links { display: flex; gap: 28px; list-style: none; }
.nav-links a {
  color: var(--dex-muted); text-decoration: none; font-size: 13px;
  font-weight: 500; font-family: var(--font-secondary); transition: color 0.2s;
}
.nav-links a:hover { color: var(--dex-blue); }
```
- Logo URL: `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Small-Light-Landscape@2x.png`
- Last nav item (pricing) gets inline style: `color: var(--dex-blue); font-weight: 600;`

### Hamburger (mobile)
```css
.hamburger {
  display: none; background: none; border: none; cursor: pointer;
  padding: 8px; z-index: 1000; position: relative;
}
.hamburger span {
  display: block; width: 22px; height: 2px; background: var(--dex-navy);
  margin: 5px 0; border-radius: 2px; transition: transform 0.3s, opacity 0.3s;
}
.hamburger.active span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.active span:nth-child(2) { opacity: 0; }
.hamburger.active span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }
```

### Urgency Bar
```css
.urgency {
  background: var(--dex-blue); color: var(--dex-white); text-align: center;
  padding: 12px 24px; font-size: 13px; font-weight: 600;
  font-family: var(--font-secondary); letter-spacing: 0.5px;
}
```

### Hero
```css
.hero {
  background: var(--dex-navy); color: var(--dex-white);
  padding: 80px 40px 100px; position: relative; overflow: hidden;
}
.hero-badge {
  display: inline-block; background: var(--dex-blue-20);
  border: 1px solid rgba(0,101,247,0.3); border-radius: 50px;
  padding: 6px 18px; font-size: 12px; font-weight: 500;
  font-family: var(--font-secondary); letter-spacing: 1.5px;
  text-transform: uppercase; margin-bottom: 24px;
}
.hero h1 { font-size: 44px; font-weight: 400; line-height: 1.15; }
.hero h1 span { color: var(--dex-blue); }
.hero .tagline {
  font-family: var(--font-secondary); font-size: 14px; font-weight: 300;
  letter-spacing: 3px; text-transform: uppercase; color: var(--dex-blue);
  margin-bottom: 16px;
}
.hero-stats { display: flex; gap: 48px; flex-wrap: wrap; }
.hero-stat .num { font-size: 36px; font-weight: 700; font-family: var(--font-secondary); }
.hero-stat .label {
  font-size: 11px; font-weight: 500; opacity: 0.6;
  text-transform: uppercase; letter-spacing: 1px;
}
```

### Decorative Circles (hero)
```css
.hero .circle-1 { position: absolute; width: 500px; height: 500px; border: 2px solid var(--dex-blue); border-radius: 50%; opacity: 0.12; top: -200px; right: -100px; }
.hero .circle-2 { position: absolute; width: 300px; height: 300px; border: 2px solid var(--dex-blue); border-radius: 50%; opacity: 0.08; bottom: -100px; left: -80px; }
.hero .circle-3 { position: absolute; width: 180px; height: 180px; background: var(--dex-blue); border-radius: 50%; opacity: 0.06; top: 60px; right: 200px; }
```

### Container & Sections
```css
.container { max-width: 1100px; margin: 0 auto; padding: 0 24px; }
section { padding: 56px 0; }
section.alt { background: var(--dex-light-bg); }
section h2 { font-size: 28px; font-weight: 400; color: var(--dex-navy); margin-bottom: 6px; }
section .section-sub { color: var(--dex-muted); font-size: 14px; font-family: var(--font-secondary); margin-bottom: 32px; }
```

### Metric Cards
```css
.metrics-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px; }
.metric-card {
  background: var(--dex-white); border-radius: var(--radius-md);
  padding: 24px; box-shadow: var(--shadow); border-left: 4px solid var(--dex-blue);
}
.metric-card h3 { font-size: 12px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.5px; color: var(--dex-muted); margin-bottom: 8px; }
.metric-card .value { font-size: 28px; font-weight: 700; color: var(--dex-navy); }
.metric-card .desc { font-size: 13px; color: var(--dex-muted); margin-top: 4px; }
/* Pain variant: */
.metric-card.pain { border-left-color: var(--dex-navy); background: var(--dex-navy); color: var(--dex-white); }
.metric-card.pain .value { font-size: 15px; font-weight: 500; font-style: italic; color: var(--dex-white); }
/* Bad PageSpeed variant: */
/* style="border-left-color: var(--dex-orange);" on metric-card */
```

### Ad Cards
```css
.ads-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 16px; margin-top: 16px; }
.ad-card {
  background: var(--dex-white); border-radius: var(--radius-md); overflow: hidden;
  box-shadow: var(--shadow); border: 1px solid var(--dex-border);
  transition: transform 0.2s, box-shadow 0.2s;
}
.ad-card:hover { transform: translateY(-3px); box-shadow: 0 6px 24px rgba(0,101,247,0.12); }
.ad-card .ad-header {
  padding: 12px 18px; background: var(--dex-navy); color: var(--dex-white);
  display: flex; justify-content: space-between; align-items: center;
}
.ad-card .ad-header .type { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: 1px; opacity: 0.8; }
.ad-card .ad-header .platform { background: var(--dex-blue-20); padding: 3px 10px; border-radius: 20px; font-size: 11px; }
.ad-card .ad-body { padding: 18px; }
.ad-card .ad-body h4 { font-size: 14px; font-weight: 600; color: var(--dex-navy); margin-bottom: 8px; }
.ad-card .ad-body p { font-size: 13px; color: var(--dex-muted); margin-bottom: 12px; }
.ad-card .ad-body .issues { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 14px; }
```

### Category Headers
```css
.cat-header {
  font-size: 13px; font-weight: 600; color: var(--dex-navy);
  text-transform: uppercase; letter-spacing: 1.5px; margin: 36px 0 16px;
  padding-bottom: 8px; border-bottom: 2px solid var(--dex-blue); display: inline-block;
}
```

### Badges
```css
.badge { display: inline-block; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 600; letter-spacing: 0.3px; }
.badge-critical { background: var(--dex-navy); color: var(--dex-white); }
.badge-warning { background: var(--dex-blue-10); color: var(--dex-blue); }
.badge-info { background: var(--dex-blue-light); color: var(--dex-blue); }
.badge-ok { background: var(--dex-light-bg); color: var(--dex-navy); }
.badge-positive { background: var(--dex-teal); color: var(--dex-white); }
```

### Issue Tags
```css
.issue-tag { font-size: 11px; padding: 3px 10px; border-radius: 20px; background: var(--dex-blue-10); color: var(--dex-blue); font-weight: 500; }
.issue-tag.severe { background: var(--dex-navy); color: var(--dex-white); }
```

### Ad Link Button
```css
.ad-link {
  display: inline-flex; align-items: center; gap: 6px;
  color: var(--dex-blue); font-size: 13px; font-weight: 500;
  text-decoration: none; padding: 6px 14px;
  border: 1px solid var(--dex-blue); border-radius: var(--radius-sm);
  transition: all 0.2s;
}
.ad-link:hover { background: var(--dex-blue); color: var(--dex-white); }
.ad-link.sm { font-size: 12px; padding: 4px 10px; }
```

### Findings
```css
.finding {
  display: grid; grid-template-columns: 4px 1fr; margin-bottom: 14px;
  border-radius: var(--radius-md); overflow: hidden;
  background: var(--dex-white); box-shadow: var(--shadow); border: 1px solid var(--dex-border);
}
.finding .bar { min-height: 100%; }
.finding .bar.high { background: var(--dex-navy); }
.finding .bar.med { background: var(--dex-blue); }
.finding .bar.low { background: rgba(0,101,247,0.3); }
.finding .content { padding: 20px 24px; }
.finding .content h4 { font-size: 15px; font-weight: 600; display: flex; align-items: center; gap: 10px; color: var(--dex-navy); }
.finding .content p { font-size: 13px; color: var(--dex-muted); line-height: 1.6; }
.finding .content .rec {
  margin-top: 10px; padding: 10px 14px; background: var(--dex-blue-10);
  border-radius: var(--radius-sm); font-size: 13px; color: var(--dex-navy);
  border-left: 3px solid var(--dex-blue);
}
.finding .content .rec strong { color: var(--dex-blue); }
```

### Summary Box
```css
.summary-box {
  background: var(--dex-navy); color: var(--dex-white);
  border-radius: var(--radius-lg); padding: 48px; margin: 48px 0;
  position: relative; overflow: hidden;
}
.summary-box .circle-dec { position: absolute; border: 2px solid var(--dex-blue); border-radius: 50%; opacity: 0.1; }
.summary-box .circle-dec.c1 { width: 300px; height: 300px; top: -120px; right: -60px; }
.summary-box .circle-dec.c2 { width: 200px; height: 200px; bottom: -80px; left: -40px; }
.summary-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; }
.summary-item {
  text-align: center; padding: 24px 16px;
  background: rgba(255,255,255,0.06); border-radius: var(--radius-md);
  border: 1px solid rgba(255,255,255,0.1);
}
.summary-item .val { font-size: 32px; font-weight: 700; color: var(--dex-blue); }
.summary-item .label-title { font-size: 14px; font-weight: 600; margin-top: 4px; }
.summary-item .desc { font-size: 12px; opacity: 0.6; margin-top: 4px; }
```

### Timeline (Recommendations)
```css
.rec-timeline { position: relative; padding-left: 36px; }
.rec-timeline::before {
  content: ''; position: absolute; left: 12px; top: 0; bottom: 0;
  width: 2px; background: linear-gradient(to bottom, var(--dex-blue), var(--dex-navy));
}
.rec-step { position: relative; margin-bottom: 36px; }
.rec-step::before {
  content: ''; position: absolute; left: -36px; top: 4px;
  width: 24px; height: 24px; border-radius: 50%;
  background: var(--dex-blue); border: 3px solid var(--dex-white);
  box-shadow: 0 0 0 2px var(--dex-blue);
}
.rec-step .step-label { font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 1.5px; color: var(--dex-blue); margin-bottom: 6px; }
.rec-step h3 { font-size: 18px; color: var(--dex-navy); margin-bottom: 8px; }
.rec-step p { font-size: 14px; color: var(--dex-muted); }
.rec-step ul li { font-size: 14px; color: var(--dex-text); margin-bottom: 6px; }
```

### Audit Table
```css
.audit-table {
  width: 100%; border-collapse: separate; border-spacing: 0;
  border-radius: var(--radius-md); overflow: hidden;
  box-shadow: var(--shadow); border: 1px solid var(--dex-border); margin-top: 16px;
}
.audit-table th {
  background: var(--dex-navy); color: var(--dex-white);
  padding: 14px 18px; font-size: 11px; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.5px; text-align: left;
}
.audit-table td { padding: 14px 18px; font-size: 14px; border-bottom: 1px solid var(--dex-border); background: var(--dex-white); }
.audit-table tr:last-child td { border-bottom: none; }
.audit-table tr:hover td { background: var(--dex-light-bg); }
```

### Priority Summary (Impact x Effort Matrix)
```css
.priority-summary {
  margin-top: 36px; padding: 32px; background: var(--dex-white);
  border-radius: var(--radius-lg); box-shadow: var(--shadow); border: 1px solid var(--dex-border);
}
.priority-legend { display: flex; gap: 20px; margin-bottom: 20px; flex-wrap: wrap; }
.leg-dot { width: 14px; height: 14px; border-radius: 50%; }
.leg-dot.p1 { background: var(--dex-navy); }
.leg-dot.p2 { background: var(--dex-blue); }
.leg-dot.p3 { background: var(--dex-blue); opacity: 0.35; }
.priority-row {
  display: grid; grid-template-columns: 14px 1fr auto auto;
  gap: 12px; align-items: center; padding: 12px 0;
  border-bottom: 1px solid var(--dex-border);
}
.priority-row .p-dot { width: 14px; height: 14px; border-radius: 50%; }
.priority-row .p-text { font-size: 14px; color: var(--dex-navy); font-weight: 500; }
.p-impact { background: var(--dex-navy); color: var(--dex-white); font-size: 11px; font-weight: 600; padding: 3px 10px; border-radius: 20px; min-width: 80px; text-align: center; }
.p-impact.med { background: var(--dex-blue); }
.p-impact.low { background: var(--dex-blue-10); color: var(--dex-blue); }
.p-effort { background: var(--dex-light-bg); color: var(--dex-navy); font-size: 11px; font-weight: 600; padding: 3px 10px; border-radius: 20px; min-width: 80px; text-align: center; }
```

### CTA Box
```css
.cta-box {
  margin-top: 24px; padding: 20px; background: var(--dex-teal);
  border-radius: var(--radius-md); text-align: center; transition: background 0.2s;
}
.cta-box:hover { background: #129577; }
.cta-box a { color: var(--dex-white); text-decoration: none; font-weight: 600; font-size: 15px; }
```

### Links Box (additional ad links)
```css
.links-box {
  margin-top: 12px; padding: 14px 18px; background: var(--dex-white);
  border-radius: var(--radius-sm); border: 1px solid var(--dex-border);
}
.links-box .links-wrap { display: flex; flex-wrap: wrap; gap: 8px; }
```

### Season Chart Wrapper
```css
.chart-wrap {
  margin-top: 28px; background: var(--dex-navy); border-radius: var(--radius-lg);
  padding: 36px 28px 28px; position: relative; overflow: hidden;
}
.chart-wrap .cw-circle1 { position: absolute; width: 300px; height: 300px; border: 2px solid var(--dex-blue); border-radius: 50%; opacity: 0.06; top: -120px; right: -60px; }
.chart-wrap .cw-circle2 { position: absolute; width: 180px; height: 180px; border: 2px solid var(--dex-teal); border-radius: 50%; opacity: 0.08; bottom: -70px; left: -40px; }
.chart-title { font-size: 13px; font-weight: 500; color: rgba(255,255,255,0.5); text-transform: uppercase; letter-spacing: 1px; }
.chart-subtitle { font-size: 11px; color: rgba(255,255,255,0.35); margin-bottom: 20px; }
.chart-legend-row { display: flex; gap: 24px; margin-top: 16px; flex-wrap: wrap; }
.cleg { display: flex; align-items: center; gap: 6px; font-size: 12px; color: rgba(255,255,255,0.6); }
.cleg-line { width: 20px; height: 3px; border-radius: 2px; }
.cleg-line.l1 { background: var(--dex-teal); }
.cleg-line.l2 { background: var(--dex-blue); }
.cleg-line.l3 { background: var(--dex-orange); }
```

**SVG chart pattern:** 1000x320 viewBox, grid lines at y=40/100/160/220/280 (rgba white 0.06), Y-axis labels (100/75/50/25/0), PEAK zone rect (teal 0.06), NOW marker rect (orange 0.08), area fill with linearGradient (tealGrad, blueGrad), polyline trend lines (teal=main 3.5px, blue=dashed 2.5px, orange=tertiary 2px), animated "STE TU" dot (pulsing circle with animate elements), X-axis month labels.

### Season Cards
```css
.season-card {
  background: var(--dex-white); border: 1px solid var(--dex-border);
  border-radius: var(--radius-md); padding: 20px; text-align: center;
  box-shadow: var(--shadow); border-left: 4px solid var(--dex-teal);
}
.season-card .sc-val { font-size: 28px; font-weight: 700; color: var(--dex-navy); }
.season-card.urgent { border-left-color: var(--dex-orange); }
.season-card.urgent .sc-val { color: var(--dex-orange); }
.season-cta {
  margin-top: 28px; padding: 20px 28px;
  background: linear-gradient(135deg, var(--dex-orange), #e06600);
  border-radius: var(--radius-md); text-align: center;
  font-size: 16px; font-weight: 600; color: var(--dex-white);
}
```

### Locked / Blurred Sections
```css
.locked-section { position: relative; overflow: hidden; border-radius: var(--radius-lg); margin-bottom: 24px; }
.locked-content {
  filter: blur(6px); -webkit-filter: blur(6px);
  pointer-events: none; user-select: none; opacity: 0.5;
  padding: 32px; background: var(--dex-light-bg);
  border: 1px solid var(--dex-border); border-radius: var(--radius-lg);
}
.locked-overlay {
  position: absolute; inset: 0; display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  background: rgba(244, 246, 252, 0.3); backdrop-filter: blur(2px);
  z-index: 10; border-radius: var(--radius-lg);
}
.locked-icon {
  width: 64px; height: 64px; background: var(--dex-navy); border-radius: 50%;
  display: flex; align-items: center; justify-content: center; margin-bottom: 16px;
  box-shadow: 0 8px 32px rgba(5, 2, 78, 0.2);
}
.locked-icon svg { width: 28px; height: 28px; fill: var(--dex-white); }
.locked-title { font-size: 18px; font-weight: 600; color: var(--dex-navy); margin-bottom: 6px; text-align: center; }
.locked-desc { font-size: 14px; color: var(--dex-muted); text-align: center; max-width: 400px; }
.locked-badge {
  display: inline-block; background: var(--dex-navy); color: var(--dex-white);
  font-size: 11px; font-weight: 600; padding: 4px 14px;
  border-radius: 20px; letter-spacing: 0.5px; margin-top: 12px;
}
```
- Lock icon SVG path: `M18 8h-1V6c0-2.76-2.24-5-5-5S7 3.24 7 6v2H6c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V10c0-1.1-.9-2-2-2zm-6 9c-1.1 0-2-.9-2-2s.9-2 2-2 2 .9 2 2-.9 2-2 2zm3.1-9H8.9V6c0-1.71 1.39-3.1 3.1-3.1 1.71 0 3.1 1.39 3.1 3.1v2z`
- Each locked section has "Odomknut ->" CTA that scrolls to #pricing
- 3 locked sections: (1) Skutocny ROAS, (2) Kde stracate budget, (3) Personalizovany akcny plan

### Pricing Section
```css
.pricing-section {
  background: var(--dex-navy); padding: 80px 0; position: relative; overflow: hidden;
}
.pricing-header { text-align: center; margin-bottom: 48px; }
.pricing-header h2 { color: var(--dex-white) !important; font-size: 32px; }
.pricing-header p { color: rgba(255,255,255,0.6); font-size: 16px; max-width: 600px; margin: 0 auto; }
.pricing-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; max-width: 900px; margin: 0 auto; }
.pricing-card {
  background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);
  border-radius: var(--radius-lg); padding: 40px 32px; position: relative;
  transition: transform 0.3s, box-shadow 0.3s;
}
.pricing-card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(0,101,247,0.15); }
.flip-card .pricing-card:hover { transform: none; } /* CRITICAL: disable hover in flip context */
.pricing-card.featured { background: rgba(0, 101, 247, 0.12); border-color: var(--dex-blue); }
.pricing-card .card-badge {
  position: absolute; top: -12px; left: 50%; transform: translateX(-50%);
  background: var(--dex-blue); color: var(--dex-white); font-size: 11px;
  font-weight: 600; padding: 4px 16px; border-radius: 20px; text-transform: uppercase;
}
.pricing-card .price .old { font-size: 16px; color: rgba(255,255,255,0.35); text-decoration: line-through; margin-right: 8px; }
.pricing-card .price .current { font-size: 36px; font-weight: 700; color: var(--dex-white); }
.pricing-card .price .period { font-size: 14px; color: rgba(255,255,255,0.4); margin-left: 4px; }
.pricing-card .features li { font-size: 14px; color: rgba(255,255,255,0.75); padding: 8px 0; border-bottom: 1px solid rgba(255,255,255,0.06); display: flex; align-items: flex-start; gap: 10px; }
.pricing-card .features .check { color: var(--dex-teal); font-weight: 700; }
.pricing-cta { display: block; text-align: center; padding: 14px 28px; border-radius: var(--radius-sm); font-size: 15px; font-weight: 600; text-decoration: none; cursor: pointer; }
.pricing-cta.primary { background: var(--dex-blue); color: var(--dex-white); }
.pricing-cta.primary:hover { background: #0052cc; }
.pricing-cta.secondary { background: transparent; color: var(--dex-white); border: 1px solid rgba(255,255,255,0.3); }
.pricing-cta.secondary:hover { border-color: var(--dex-white); }
```

### Flip Card
```css
.flip-card { perspective: 1200px; }
.flip-card-inner {
  position: relative; width: 100%;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  transform-style: preserve-3d;
}
.flip-card.flipped .flip-card-inner { transform: rotateY(180deg); }
.flip-front, .flip-back { backface-visibility: hidden; -webkit-backface-visibility: hidden; border-radius: var(--radius-lg); width: 100%; }
.flip-front { position: relative; z-index: 2; } /* DETERMINES container height */
.flip-back {
  position: absolute; top: 0; left: 0; height: 100%;
  transform: rotateY(180deg); z-index: 1;
  background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);
  padding: 32px; display: flex; flex-direction: column; justify-content: center;
}
.flip-card.featured .flip-back { background: rgba(0, 101, 247, 0.12); border-color: var(--dex-blue); }
```

**CRITICAL flip card rules:**
- `.flip-front` = `position: relative` (determines container height)
- `.flip-back` = `position: absolute` (overlays)
- NEVER use `height: 100%` on inner elements of flip cards
- ALWAYS disable hover transform on `.flip-card .pricing-card:hover { transform: none; }`

### Wasted Spend Context Box
Inline styles on a div inside `.pricing-section`, before `.pricing-cards`:
- `max-width: 900px; margin: 0 auto 40px;`
- Navy-transparent bg: `background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);`
- 3-column grid (`.wasted-spend-grid`): ad spend | wasted % | ROI payback
- Colors: spend=white, wasted=orange, payback=teal
- Below grid: comparison text + orange urgency line

### Footer
```css
.footer {
  background: var(--dex-navy); color: var(--dex-white);
  padding: 48px 40px; text-align: center; position: relative; overflow: hidden;
}
.footer .circle-f { position: absolute; border: 1px solid var(--dex-blue); border-radius: 50%; opacity: 0.08; }
.footer-logo { height: 64px; margin-bottom: 20px; } /* MINIMUM 64px — footer logo is brand anchor, must be prominent */
.footer p { opacity: 0.5; font-size: 13px; }
.footer .go-beyond { font-size: 12px; font-weight: 300; letter-spacing: 3px; text-transform: uppercase; color: var(--dex-blue); margin-top: 12px; }
```
- Footer logo URL: `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Small-Dark-Landscape@2x.png`
- Content: logo, audit name + date, data sources disclaimer, "Go Beyond"

---

## 4. MONETIZATION LAYER

### Funnel flow:
1. Free audit content (visible, valuable) builds trust
2. 3 locked/blurred sections create FOMO
3. "Odomknut ->" CTA scrolls to pricing
4. Wasted spend box REFRAMES price as < wasted spend
5. 2 flip cards: CTA flips to IBAN payment details

### Pricing products:
- **Card 1 (secondary):** Full Audit + konzultacia = 1 290EUR (skrtnutych 1 590EUR, jednorazovo)
- **Card 2 (featured, "Odporucame"):** Full Setup + sprava = 1 690EUR setup (skrtnutych 2 090EUR) + od 990EUR/mes

### Flip card back content:
- Product name + price (large)
- IBAN table: `SK18 0900 0000 0050 5804 0235`, Dexfinity s.r.o., VS, amount
- Copy-to-clipboard button on IBAN
- Blue gradient "Po platbe" process box
- Contact: hello@dex.sk, +421 918 435 105
- "Spat na prehlad" button to unflip

### Pricing note:
- `*Celkove nastavenie analytiky sa naceni podla vysledku kontroly auditu.`
- Contact line with email and phone

---

## 5. RESPONSIVE RULES

```css
@media (max-width: 768px) {
  .hamburger { display: block; }
  .nav-links {
    display: none; position: fixed; top: 0; left: 0;
    width: 100%; height: 100vh; height: 100dvh;
    background: var(--dex-white); flex-direction: column;
    align-items: center; justify-content: center;
    gap: 0; z-index: 999; padding: 80px 40px 40px;
  }
  .nav-links.open { display: flex !important; }
  .nav-links li { width: 100%; text-align: center; border-bottom: 1px solid var(--dex-border); }
  .nav-links a { display: block; padding: 16px 0; font-size: 16px; color: var(--dex-navy) !important; }
  .hero h1 { font-size: 30px; }
  .hero { padding: 48px 24px 64px; }
  .hero-stats { gap: 24px; }
  .ads-grid { grid-template-columns: 1fr; }
  .summary-grid { grid-template-columns: 1fr 1fr; }
  .summary-box { padding: 32px 24px; }
  .metrics-grid { grid-template-columns: 1fr 1fr; }
  .pricing-cards { grid-template-columns: 1fr; }
  .wasted-spend-grid { grid-template-columns: 1fr !important; gap: 16px !important; }
}
```

Key breakpoints:
- 768px = single column switch for ads-grid, pricing-cards, wasted-spend-grid
- metrics-grid, summary-grid go to 2-column
- Hamburger becomes visible, nav becomes fullscreen overlay (z-index: 999)
- Body overflow hidden when menu open

---

## 6. JAVASCRIPT PATTERNS

### Mobile menu
```javascript
function toggleMenu() {
  document.getElementById('navLinks').classList.toggle('open');
  document.querySelector('.hamburger').classList.toggle('active');
  document.body.style.overflow = document.getElementById('navLinks').classList.contains('open') ? 'hidden' : '';
}
function closeMenu() {
  document.getElementById('navLinks').classList.remove('open');
  document.querySelector('.hamburger').classList.remove('active');
  document.body.style.overflow = '';
}
document.querySelectorAll('#navLinks a').forEach(function(a) {
  a.addEventListener('click', closeMenu);
});
```

### Flip card
```javascript
function flipCard(id) {
  document.getElementById(id).classList.toggle('flipped');
}
```
- Cards have ids: `flipAudit`, `flipSetup`
- CTA onclick: `flipCard('flipAudit')`

### Copy to clipboard (IBAN)
```javascript
// Inline on button inside flip-back:
onclick="event.stopPropagation();navigator.clipboard.writeText('SK1809000000005058040235');this.textContent='OK!';var b=this;setTimeout(function(){b.textContent='Kop.'},1500)"
```

### Locked section scroll
```javascript
// Inline on "Odomknut" CTA:
onclick="document.getElementById('pricing').scrollIntoView({behavior:'smooth'})"
```

---

## 7. TYPOGRAPHY

- **Headings (h1, h2, h3):** Questrial (--font-primary)
- **Body, UI, badges, labels:** Poppins (--font-secondary)
- **Google Fonts import:** `https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Questrial&display=swap`
- **Body:** font-family: var(--font-secondary); color: var(--dex-text); line-height: 1.6;
- **h1, h2, h3:** font-family: var(--font-primary);

---

## 8. ANTI-PATTERNS (NEVER DO)

1. **Hover transform on flip cards** -- breaks 3D perspective
2. **Inline height:100% on pricing-card inside flip** -- causes overflow collapse
3. **Modals for payment** -- flip cards are better UX (legacy modal code exists but flip is primary)
4. **position: absolute on BOTH flip sides** -- front must be relative (determines height)
5. **Too many nav items** -- max 6-7, merge related sections (e.g. "Bonus insights")
6. **Overlapping touch targets** -- always verify with screenshot
7. **Inline onclick on nav links** -- use addEventListener for closeMenu
8. **Generic/non-Dexfinity styles** -- every output must use this design system

---

## 9. DEPLOYMENT

- **GitHub org:** DXFNT
- **URL format:** `dxfnt.github.io/{client}-ads-audit`
- **Git config:** `user.email="pavol.adamcak@dexfinity.com"`
- **gh CLI path:** `/opt/homebrew/bin/gh`
- **Repo:** always public, GitHub Pages enabled (main branch, root)
- **Single file:** one HTML file with all CSS in `<style>` and JS in `<script>`, no external dependencies except Google Fonts

---

## 10. BONUS INSIGHTS BANNER

For merged/extra sections (Heureka + GMB + PageSpeed), use a gradient banner:
```html
<div style="background: linear-gradient(135deg, var(--dex-blue), #0052cc); border-radius: var(--radius-lg); padding: 32px 36px; display: flex; align-items: center; gap: 20px;">
  <div style="width: 48px; height: 48px; background: rgba(255,255,255,0.15); border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0;">
    <!-- Star SVG icon -->
  </div>
  <div>
    <h2 style="color: #fff !important; font-size: 24px;">Bonus insights</h2>
    <p style="font-size: 14px; color: rgba(255,255,255,0.7);">Description</p>
  </div>
</div>
```

---

## 11. REVIEW QUOTE CARD PATTERN

```html
<div style="background: var(--dex-white); border-radius: var(--radius-md); padding: 24px; box-shadow: var(--shadow); border: 1px solid var(--dex-border); border-left: 4px solid var(--dex-blue); position: relative;">
  <div style="font-size: 36px; color: var(--dex-blue); opacity: 0.15; position: absolute; top: 8px; right: 16px; font-family: Georgia, serif;">&ldquo;</div>
  <p style="font-size: 14px; color: var(--dex-navy); font-style: italic; margin-bottom: 8px;">"Quote text"</p>
  <p style="font-size: 12px; color: var(--dex-muted);">-- Name, overeny zakaznik</p>
  <div style="margin-top: 8px;"><span class="badge badge-info">Tag 1</span> <span class="badge badge-info">Tag 2</span></div>
</div>
```
Grid: `grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 14px;`

---

## 12. METHODOLOGY BOX PATTERN

For gap analysis and sections with caveats:
```html
<div style="background: var(--dex-blue-10); border-radius: var(--radius-md); padding: 16px 20px; margin-bottom: 24px; border-left: 3px solid var(--dex-blue);">
  <p style="font-size: 13px; color: var(--dex-navy);"><strong>Metodologia a obmedzenia:</strong></p>
  <p style="font-size: 12px; color: var(--dex-muted); line-height: 1.7;">Explanation text...</p>
</div>
```

---

## 13. DOUBLE-CHECK RULE (POVINNÉ pre negatívne findings)

Každý finding tvaru "X neexistuje" / "0 Y" / "404" / "Neviditeľný" MUSÍ byť overený **2× nezávisle** pred zaradením do auditu.

**Príklad — čo nerobiť:**
Agent hľadal `obchody.heureka.sk/oxalis-original-sk/` → 404 → napísal finding "Heureka SK neexistuje — kritický gap".
Realita: Profil existuje pod iným názvom (`oxalis-sk`). Klient to okamžite vyvráti, audit stratí kredibilitu.

**Ako overovať:**
1. **Variácie názvov** — skús s/bez pomlčky, s/bez "sk", s/bez domény suffix
2. **Google site: search** — `site:obchody.heureka.sk {brand}` alebo `site:trustpilot.com {brand}`
3. **Cross-reference** — pozri web klienta (footer, contact) či tam sú odkazy/badges na platformu
4. **Ak nejde overiť automaticky (403, block)** — nedeklaruj ako fakt, daj `badge-warning` "Na overenie"

**V audite:**
- Overené 2× → `badge-critical` "Kritické" + konkrétne čísla
- Overené 1× alebo blokované → `badge-warning` "Na overenie" + poznámka metódy
- Neoverené → VÔBEC nedávaj do auditu

---

## 14. CONSTANT VALUES

- **Contact:** hello@dex.sk, +421 918 435 105
- **IBAN:** SK18 0900 0000 0050 5804 0235
- **Recipient:** Dexfinity s.r.o.
- **Bank:** Slovenska sporitelna
- **Nav logo:** `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Small-Light-Landscape@2x.png`
- **Footer logo:** `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Small-Dark-Landscape@2x.png`
- **Analytics footnote:** `*Celkove nastavenie analytiky sa naceni podla vysledku kontroly auditu.`
