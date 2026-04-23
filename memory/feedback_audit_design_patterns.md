---
name: Audit Landing Page Design Patterns
description: Design system rules and patterns for all audit product landing pages — layout, colors, components, anti-patterns
type: feedback
---

## Page Structure (top to bottom — this order matters)
1. Urgency bar (sezónna správa, oranžový/tmavý)
2. Sticky nav s CTA linkom na pricing ako posledný item (zvýraznený farbou)
3. Hero — navy bg, cenovka auditu v badge, kľúčové metriky v gride
4. Externý audit obsah — viditeľný, hodnotný, buduje dôveru
5. Blurred/locked sekcie (3x) s "Odomknúť →" CTA → scrolluje na pricing
6. Pricing sekcia — navy bg, wasted spend context box NAD kartami, potom pricing karty
7. Footer s kontaktom

**Why:** Tento flow bol iterovaný na Aquapond audite a funguje ako funnel — hodnota → FOMO → reframe ceny → konverzia.

**How to apply:** Každý nový audit produkt by mal sledovať túto štruktúru. Poradie je kľúčové — wasted spend box MUSÍ byť pred pricing kartami.

## Farebný Systém v Audite
- **Navy (#05024E)** — hero, pricing sekcia, premium feel
- **Blue (#0065F7)** — CTA, featured karta border, interaktívne elementy
- **Oranžová (#ff7f00)** — wasted spend, urgency, alarm metriky
- **Teal (#16AB8B)** — pozitívne metriky (úspora, ROI, návratnosť)
- **Červená** — kritické findings (bar .high)
- **Žltá** — stredné findings (bar .med)
- **Biela s opacity** — sekundárne texty na navy (0.35–0.6)

**Why:** Farby nie sú len dekorácia — oranžová = strata/problém, teal = riešenie/úspora. Klient podvedome číta: problém → riešenie.

## Komponenty ktoré fungujú
- **Metric karty v gride** — čísla v boxoch > čísla v texte
- **Finding bary** s farebným indikátorom (high/med/low) — vizuálna priorita
- **Škrtnuté ceny** — menší font + line-through + opacity pre starú cenu
- **Flip karty na platbu** — CTA otočí kartu na IBAN údaje, lepšie ako modál
- **Blur filter + overlay** na locked sekciách — klient vidí obsah ale nemôže čítať
- **Copy-to-clipboard** na IBAN — malý button "Kop." vedľa čísla
- **Gradient banner** na zlúčené/bonus sekcie — odlíši od hlavného auditu

## Anti-patterns (NEROBIŤ)
- Hover transform na kartách vo flip-card kontexte → rozbíja 3D perspektívu
- Inline height:100% na vnorených elementoch vo flip kartách → spôsobuje overflow
- Modály na platbu → flip karta je lepší UX, klient neodchádza z kontextu
- Príliš veľa nav položiek → zlúčiť pod logické skupiny (max 6-7 nav items)
- position: absolute na obe strany flip karty → front musí byť relative (určuje výšku)
- Prekrývajúce sa CTA tlačidlá → VŽDY overiť screenshotom po implementácii

## Flip Card CSS Pattern (správny)
```css
.flip-front { position: relative; }  /* determines container height */
.flip-back { position: absolute; top:0; left:0; width:100%; height:100%; }
.flip-card .pricing-card:hover { transform: none; }  /* disable hover in flip context */
```

## Konzistentné prvky (VŽDY rovnaké naprieč auditmi)
- **Nav:** sticky, biele pozadie s blur, Dexfinity logo vľavo (vždy rovnaký src), nav linky vpravo
- **Logo URL:** `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Small-Light-Landscape@2x.png`
- **Footer logo:** `https://www.dexfinity.com/wp-content/uploads/2021/03/Logo-Landscape@2x.png`
- **Fonty:** Poppins (body, secondary) + Questrial (headings, primary) — vždy Google Fonts import
- **Kontakt:** hello@dex.sk, +421 918 435 105
- **IBAN:** SK18 0900 0000 0050 5804 0235, Dexfinity s.r.o., Slovenská sporiteľňa
- **Brand colors:** vždy CSS variables (--dex-blue, --dex-navy, --dex-teal, --dex-orange...)
- **Urgency bar:** vždy navrchu, sezónna správa relevantná pre klientov biznis
- **Pricing sekcia:** vždy navy bg, vždy wasted spend box pred kartami
- **Footer:** Dexfinity logo, názov auditu, dátum, disclaimer o zdrojoch dát
- **Analytics footnote:** "*Celkové nastavenie analytiky sa nacení podľa výsledku kontroly auditu."

## Responsive
- 2-column grid na desktop, 1-column na mobile (768px breakpoint)
- **Hamburger menu na mobile** — fullscreen biely overlay, z-index 999, body overflow:hidden keď otvorené
- Hamburger button: 3 span lines, animácia na X pri .active
- Nav links po kliku volajú closeMenu() cez addEventListener (nie inline onclick)
- Urgency bar ostáva viditeľný nad menu (vyšší z-index) — to je OK
- Metric gridy: 4-col → 2-col na mobile
