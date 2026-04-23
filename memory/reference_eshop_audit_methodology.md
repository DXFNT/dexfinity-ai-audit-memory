---
name: Eshop audit methodology
description: Complete external audit methodology learned from Aquapond + Nebshop audits
type: reference
---

# Dexfinity External Eshop Audit — Metodológia v2

Štandardný postup pre externý audit eshopu bez prístupov. Výstup: branded HTML stránka na DXFNT GitHub Pages. Naučené z auditov Aquapond.sk a Nebshop.cz.

---

## ARCHITEKTÚRA STRÁNKY (poradie sekcií)

1. **Urgency banner** — sezónna urgencia hore
2. **Nav** — Dexfinity logo (42px), anchor linky na sekcie
3. **Hero** — názov klienta, "Analýza reklam", štatistiky s labelmi (analyzed/reviewed/identified) v oranžovej
4. **Hlavný highlight** — "bonbónik" finding hneď pod hero, navy box s teal/orange akcentmi, 3-4 čísla. Toto je háčik pre čítanie — najsilnejší insight z celého auditu (napr. keyword gap, nevyužitý potenciál)
5. **Sezónnosť** — SVG trend chart s overenými Google Trends dátami
6. **O klientovi** — metric karty (obrat, rast, budget, pain)
7. **Meta Ads analýza** + prioritizácia (Impact × Effort)
8. **Google Ads analýza** + prioritizácia
9. **Hlavné zistenia** — findings s color-coded severity
10. **Celkové hodnotenie** — summary box (navy)
11. **Odporúčania** — timeline (3-4 kroky)
12. **Budget** — tabuľka (ak poznáme)
13. **Produkty vs Ads — Gap analýza** — tabuľka + findings
14. **Heureka / Social proof** — metriky + najlepšie citáty + ad copy návrhy
15. **Google Moja Firma / Google Reviews** — combined reviews count + Seller Ratings + Product Ratings odporúčania
16. **PageSpeed** — metriky s orange border pre zlé výsledky
17. **Konkurencia** — tabuľka + brand keyword SERP overenie
18. **Footer** — Dexfinity logo (dark), "Go Beyond", dátum auditu

---

## KROK 0: HIGHLIGHT FINDING (NOVÉ)

Ešte pred detailným auditom hľadať "bonbónik" — jeden silný insight, ktorý zaujme klienta na prvý pohľad:
- Keyword gap: produkt na webe, ale žiadna reklama na generický KW (Nebshop: sportovní podprsenka 4800/mes)
- Sezónna urgencia: peak sa blíži a kampane nie sú optimalizované (Aquapond: apríl-júl)
- Zabudnutá kampaň: niečo beží rok bez zmeny
- Obrovský nevyužitý social proof

**Overenie highlight finding:**
- Overiť že klient produkty skutočne MÁ (navštíviť stránku)
- Overiť SERP — klient sa tam naozaj nezobrazuje? (Ahrefs SERP + reálny Google Search)
- Pomenovať konkrétnych konkurentov na tých pozíciách
- Dať do highlight boxu s číselnými metrikami (4 karty)
- Pod čísla pridať SERP detail: kto tam je a kto nie

---

## KROK 1: RESEARCH (paralelne)

Spustiť paralelne:
- WebFetch / Chrome scrape homepage → produkty, kategórie, menu
- Ahrefs: site-explorer-metrics, organic-keywords (top 20 by traffic), organic-competitors, keywords-explorer-overview pre brand + produktové KW
- Meta Ad Library cez Chrome → screenshot + count
- Google Ads Transparency cez Chrome → screenshot + count + advertiser name
- Heureka profil cez Chrome → rating, reviews, citáty
- Google Maps cez Chrome → GMB profil
- PageSpeed Insights → spustiť test
- Google Search pre brand keyword → screenshot (kto biduje)
- Google Search pre top generické KW → screenshot (SERP overenie)

**JAZYK:** Audit v jazyku krajiny klienta (SK = slovenčina, CZ = čeština)

---

## KROK 2: SEZÓNNOSŤ

- Keywords: odvodiť z homepage produktov (nie vymyslené)
- Pridať aj kľúčové slová z gap analýzy do legendy chartu
- **VŽDY overiť Google Trends vizuálne v Chrome** — nikdy neodhadovať krivku
- SVG trend chart: 3 línie (teal hlavná, blue dashed sekundárna, orange terciárna)
- Area fill pod hlavnou líniou
- "STE TU" pulzujúci bod na aktuálnom mesiaci (oranžový, animovaný)
- PEAK zóna highlight (teal, nízka opacity)
- Pod graf: ďalšie relevantné KW z homepage s objemami
- Zdroj: "Google Search Data and Trends" (NIKDY "Ahrefs")

---

## KROK 3: META ADS

- Otvoriť Ad Library, spočítať aktívne reklamy
- Kategorizovať: product, hiring, retargeting/DPA, carousel, brand
- **Hiring ads → VŽDY navštíviť landing page** — sú pozície stále otvorené?
- **Video/image quality → NEKOMENTOVAŤ z Ad Library** (komprimuje previews)
- Sledovať: opakujúci sa copy, chýbajúce A/B testy, zlé CTA
- Discount-heavy approach flagovať — riziko brand dilúcie
- Pridať priority summary (Impact × Effort matica)
- CTA box (teal) s linkom na Ad Library

---

## KROK 4: GOOGLE ADS

- Google Ads Transparency Center → počet reklám, advertiser name, typy
- **Viac účtov ≠ automaticky problém** — záložný účet je bežná stratégia, overiť s klientom
- **Disclaimer box:** koľko reklám sme skontrolovali, aké sú obmedzenia (Transparency neumožňuje hľadať podľa produktu)
- Paid keywords count z Ahrefs — flagovať ak je nízky
- Pridať priority summary
- CTA box (teal) s linkom na Transparency Center

---

## KROK 5: BRAND KEYWORD

- Ahrefs: volume pre brand KW
- **VŽDY overiť v reálnom Google Search:**
  - Biduje klient na vlastný brand? (ak áno = badge "Overené" teal)
  - Biduje konkurencia na klientov brand?
  - Kto sa zobrazuje v Shopping ads?
- Overiť aj 2-3 top generické KW — kto je v paid? Kto v organic?
- Zaznamenať konkrétne mená konkurentov s pozíciami

---

## KROK 6: GAP ANALÝZA (produkty vs reklamy)

- Scrape homepage cez Chrome JavaScript → prioritné produkty
- Navštíviť produktové stránky a overiť: **má klient skutočne tie produkty?** Koľko? Sú bestsellery?
- Porovnať s Meta Ad Library a Google Transparency
- **Tabuľka:** Produkt | Volume | Stav reklám | Status badge | Príležitosť
- **SERP overenie pre top gap:** kto sa zobrazuje? (konkrétne mená + pozície)
- Badge "Nenájdené" nie "Chýba", severity "Na overenie" nie "Kritické"
- **Metodológia box** na vrchu: koľko reklám sme skontrolovali, obmedzenia

---

## KROK 7: RECENZIE & SOCIAL PROOF

### Heureka:
- obchody.heureka.sk (SK) alebo obchody.heureka.cz (CZ)
- Rating, počet recenzií, % odporúča, priemerné dodanie
- 5-6 najlepších citátov s menami a tagmi (rýchlosť, odbornosť, osobný prístup)
- **NIKDY nekomentovať že ich je málo** — vždy pozitívny tón
- Navrhnúť: ad copy, social proof na web, testimonial kreatívy

### Google Reviews / GMB:
- Rating, počet recenzií, adresa, kategória
- **Spočítať CELKOVÝ počet** (Google + Heureka) — prezentovať ako "silný základ"
- Navrhnúť konkrétne:
  - Google Ads headlines s recenziami
  - Meta Ads hook s ratingom
  - **Seller Ratings** (Search ads) — min 100 Google reviews, Heureka feed cez Merchant Center
  - **Product Ratings** (Shopping ads) — product ratings feed cez Merchant Center
  - Google Reviews widget na web

---

## KROK 8: PAGESPEED

- Spustiť test na pagespeed.web.dev (mobile)
- Extrahovat cez Chrome JavaScript: Performance score, LCP, FCP, TBT, Speed Index
- Metric karty s **orange border** pre zlé výsledky
- Komentovať oproti Google thresholds (LCP < 2.5s, FCP < 1.8s, TBT < 200ms)
- Link na kompletný PageSpeed report

---

## KROK 9: KONKURENCIA

- Ahrefs organic competitors (uvádzať ako "Google Search Data")
- Tabuľka: konkurent, spoločné KW, traffic, share
- SERP overenie pre kľúčové generické keywords — kto biduje, kto je v organic

---

## DIZAJN SYSTÉM

### Farby:
- Navy #05024E — pozadia, headings, severity "high"
- Blue #0065F7 — akcentová, linky, severity "med"
- Teal #16AB8B — CTA tlačidlá, pozitívne badges ("Silný základ", "Pokryté", "Overené")
- Orange #ff7f00 — urgencia, zlé metriky, "analyzed/reviewed" labely v hero
- Biela/čierna — text

### Badge systém:
- `badge-positive` (teal) — pozitívne: Silný základ, Overené, Pokryté
- `badge-warning` (blue) — na overenie: Dôležité, Na overenie, Nenájdené
- `badge-critical` (navy) — vysoká priorita (len ak sme si istí)
- `badge-info` (light blue) — info, možnosť

### Hero štatistiky:
- Veľké číslo + label + **oranžový sublabel** (analyzed/reviewed/identified/estimated)

### Typografia:
- Questrial — headings (h1, h2, h3)
- Poppins — body, UI, badges, labels
- Logo: 42px v nav aj footer, PNG z dexfinity.com

### Grafické elementy:
- Dekoratívne kruhy (circle) s nízkou opacity
- SVG trend chart s area fill a animovaným "STE TU" bodom

---

## PRAVIDLÁ TÓNU & KREDIBILITY

1. **Expert pomenuje, neskáče k záverom** — "Nenájdené" nie "Chýba"
2. **Severity len ak sme istí** — "Na overenie" nie "Kritické" (kde nie sme 100% istí)
3. **Vždy uviesť metodológiu a obmedzenia** — koľko reklám sme prešli, čo nie je viditeľné
4. **Pozitívny tón pri recenziách** — nikdy "málo recenzií", vždy "silný základ, nevyužitý materiál"
5. **Landing pages VŽDY overiť pred tvrdeniami** — hiring ads, produktové gaps
6. **Kvalitu médií nekomentovať z Ad Library** — komprimuje previews
7. **Záložný Google účet ≠ problém** — overiť s klientom
8. **Čísla musia byť overiteľné** — z Ahrefs, Google Trends, PageSpeed, reálny SERP
9. **Zdroje uvádzať ako "Google Search Data and Trends"** — nie Ahrefs (know-how)
10. **Každý finding v gap analýze overiť na webe** — má klient ten produkt? Koľko kusov? Je bestseller?
11. **SERP overenie dvojité** — Ahrefs SERP data + reálny Google Search screenshot

---

## DEPLOYMENT

- GitHub org: **DXFNT**
- URL formát: `dxfnt.github.io/{client}-ads-audit`
- Git config: user.email="pavol.adamcak@dexfinity.com"
- gh CLI: `/opt/homebrew/bin/gh`
- Repo vždy public, GitHub Pages enabled (main branch, root)
