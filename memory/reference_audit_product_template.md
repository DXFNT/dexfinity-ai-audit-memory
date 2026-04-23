---
name: Digital Audit Product Template
description: Complete playbook for turning external audits into sellable digital products — pricing, UX, sales strategy, lessons learned from Aquapond.sk
type: reference
---

## Audit Product Architecture

### Funnel Structure
1. **Free externý audit** s viditeľnou cenovkou (690€) — lead magnet
2. **3 blurred/locked sekcie** na konci auditu — ROAS, Wasted spend, Akčný plán
3. **2 produkty na kúpu** pod locked sekciami
4. **Flip card platba** — CTA otočí kartu a ukáže IBAN údaje

### Pricing Strategy
- **Full Audit + konzultácia**: 1 290€ (škrtnutých 1 590€, jednorazovo)
  - Interný audit všetkých kanálov + 60min konzultácia s PPC a Ecommerce špecialistom
- **Full Setup + správa kampaní**: 1 690€ setup (škrtnutých 2 090€) + od 990€/mes retainer
  - Všetko z auditu + kompletné nastavenie + mesačná správa
- Upsell logic: ak klient kúpi audit (1 290€) a potom chce setup, doplatí len 400€

### Wasted Spend Framing (KĽÚČOVÉ)
- Pricing porovnávať s potenciálnym wasted spend, NIE absolútna cena
- "Potenciálny wasted spend: až 20%" — vždy "až/potenciálny", nie definitívne čísla
- "Setup za 1 690€ = menej ako 10 dní vášho ad spendu"
- "Setup sa vráti za menej ako 2 mesiace len na úspore wasted spendu"

### Najsilnejšie Sales Argumenty (poradie priority)
1. **Sezóna a rýchlosť** — "Každý deň bez optimalizácie v sezóne = stratené objednávky, ktoré už nedobehnete"
2. **Nefunkčná agentúra** — každý deň s ňou = strata väčšia ako wasted spend
3. **Wasted spend úspora** — "Strácate 1 000€ mesačne. Setup sa vráti za 2 mesiace."
4. **Dôkaz kompetencií** — "Ak toto vidíme zvonka bez prístupov, predstavte si čo nájdeme vnútri."
5. **Pain point agentúry** — klient nechce radiť agentúre čo má robiť → my sme proaktívni

### UX/Design Poučenia
- Navigáciu zlúčiť ak je veľa sekcií (napr. Heureka+GMB+PageSpeed → "Bonus insights")
- Flip karty na platbu > modál — klient neodchádza zo stránky
- "Odomknúť →" CTA na locked sekciách scrolluje na pricing
- Urgency bar hore: "Sezóna X = mesiac–mesiac — Každý deň oneskorenia = stratené objednávky"
- Oranžový urgency text pod wasted spend boxom pre sezónny tlak

### Čo NEROBIŤ (poučenia z iterácií)
- "Hodnota reportu 690€" framing → nefunguje, lepšie priama cenovka "External Ads Audit — 690€"
- "Doplatok X€ k externému auditu" pod CTA → zbytočný detail, odstraňovať
- Definitívne čísla wasted spendu ("min. 20%") → vždy "až/potenciálny" = dôveryhodnejšie
- Konverzné cesty v Analytics audite → nerobíme, len "Kontrola nastavenia Google Analytics*"
- Hover transform na flip kartách → breaks 3D context, vypnúť
- Inline height:100% na pricing-card vo flip-card → spôsobuje kolaps

### Technický Stack
- Single-page HTML, no backend
- GitHub Pages deployment (DXFNT org)
- CSS 3D flip cards (perspective, transform-style, backface-visibility)
- CSS blur + overlay pre locked sekcie
- Dexfinity brand: navy #05024E, blue #0065F7, Poppins/Questrial fonts
- IBAN platba s copy-to-clipboard button
- Sales playbook ako separátny dokument pre sales tím

### Šablóna pre nový audit produkt
1. Urobiť externý audit klienta (verejne dostupné dáta)
2. Nastaviť cenovku podľa klientovho ad spendu (690€ je base)
3. Vytvoriť 3 locked sekcie s najlákavejším interným obsahom
4. Nastaviť 2 produkty s cenami relatívnymi k ad spendu klienta
5. Pridať sezónnu urgency relevantnú pre klientov biznis
6. Vytvoriť sales playbook s argumentmi a follow-up emailmi
7. Deploynúť na GitHub Pages pod DXFNT org
