---
name: AI Audit verzie (audit vs audit deep)
description: Dva typy AI Ads Auditov — "ai audit" (štandardný, 1 trh) a "ai audit deep" (multi-trh, quick wins, exec summary, bar charty). Trigger words a rozdiely.
type: reference
---

# Dexfinity AI Ads Audit — 2 verzie

## AI Audit (default)
**Trigger:** "ai audit [url]", "urob audit pre [eshop]", "audit [firma]"
**Vzor:** Aquapond, Kleinsport
**Kedy:** Štandardný SK/CZ eshop, 1 trh, 1 jazyk

**Čo obsahuje:**
- Urgency bar, Nav, Hero so stats
- Highlight finding (bonbónik)
- Sezónnosť (navy SVG chart)
- O klientovi (metric cards)
- Meta Ads analýza + priority summary
- Google Ads analýza + priority summary
- Gap analýza (produkty vs reklamy)
- Hlavné zistenia (findings s severity)
- Heureka + Google Reviews / Social proof
- PageSpeed metriky
- Konkurencia (tabuľka)
- Summary box
- Odporúčania (rec-timeline)
- 3 Locked sekcie + Pricing (flip cards, IBAN)
- Footer

**Rozsah:** ~2600 riadkov, 1 trh

---

## AI Audit Deep
**Trigger:** "ai audit deep [url]", "deep audit", "multi-trh audit", "audit ako lamely3d"
**Vzor:** Lamely3D
**Kedy:** Multi-trh klient, zahraničná expanzia, viac domén, komplexnejší prípad

**Čo obsahuje navyše oproti AI Audit:**
- **Executive summary floating box** — biely card s blue border, numbered quick wins, colored icons (danger/warning/info). Priamo pod hero, overlapping.
- **Quick wins framing** — "produkt × dopyt × bez kampane = príležitosť" namiesto kritiky. Konzultačný tón.
- **Multi-trh dashboard** — tabuľka SK/CZ/DE/AT s porovnaním: search volume, org KW, paid KW, traffic, DR, status badge
- **Horizontálne bar charty** — vizuálne porovnanie organic traffic konkurentov
- **Color-coded highlight boxes** — `.highlight-positive` (green), `.highlight-warning` (orange), `.highlight-negative` (red), `.highlight-neutral` (blue)
- **Ad creative showcase** — reálne ukážky reklám s copy preview, dátumom, Library ID
- **Dual PageSpeed** — porovnanie viacerých domén vedľa seba
- **Brand protection finding** — ak existuje konkurenčná/kanibalizačná doména
- **Print styles** — `@media print` pre PDF export
- **Tabular-nums** — zarovnané čísla v tabuľkách

**Rozsah:** ~2900+ riadkov, multi-trh, multi-jazyk

---

## Kľúčové rozdiely v tóne

| | AI Audit | AI Audit Deep |
|---|---|---|
| **Tón** | Expert analýza | Konzultačný, quick wins |
| **Urgency bar** | Sezónna urgencia | Príležitostný framing |
| **Highlight** | Najsilnejší finding | Produkt × dopyt × kampaň prienik |
| **Exec summary** | Nie | Áno — floating box s numbered findings |
| **Konkurencia** | Tabuľka | Tabuľka + bar charty |
| **Findings** | Color-coded severity | + highlight boxes (positive/warning/negative) |

## Deployment
- Oba typy: GitHub Pages pod DXFNT org
- URL: `dxfnt.github.io/{client}-ads-audit`
- Pricing rovnaký: 690€ / 1 290€ / 1 690€+990€/mes
